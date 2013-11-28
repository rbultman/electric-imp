### Hello World

This hello world application illustrates communicating with a host device via 
a UART, communication between the device and cloud agent, and communication
between a web client and the cloud agent.  It also shows how a Squirrel table
can be used to route URL's to handlers.

The device code does the following things:
- It prints a few bits of interesting information at power up.
- It periodically prints "Hello World" to uart1289 (pins 8 and 9 on the imp-001 card).
- It saves the last character received on the UART.
- It sends the last character received to the cloud agent when the character is received.
- It sends the last character received to the cloud agent when request.

The agent code does the following things:
- It stores the last character send from the device.
- It handles a URI request to / which returns the last character received.
- It handles a URI reuqest to /dynamic.  This will cause a round-trip read to the 
device to return the last character received as stored on the device.

The dynamic reading, or read-thru, of the last character received illustrates
how the agent can expose resources on the device without having to store data in
the cloud.

### To Use
The imp-001 and April development board were used in these examples.  You will also
need an USB-to-UART cable so you can communicate with the Imp from a terminal program
like kermit or PuTTY.  Note that the Imp is 3.3V, so make sure that your cable is 3.3V
and not 5V.  I used the ttl-232r-3v3 availale from FTDI, although other cables are
available from vendors such as SparkFun and Adafruit.  You will need to use the 
Imp app to commission your Imp to your router, which also requires that you create an
Electric Imp account.  You will need to use one USB cable to power the Imp via the 
USB connector on the April or the 3.3V power from the USB-to-UART cable if it is
available on your cable.

Once you have the device in your account, create a new project (model?) in the Imp
development on-line IDE.  Paste the device and agent code into the appropriate panel
in the IDE and click the 'Build and Run' button.
