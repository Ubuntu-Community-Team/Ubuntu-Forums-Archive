---
title: "pySerial help?"
date: 2011-01-13
forum: General Help
---

### Post by damic1 on 2011-01-13
Hello!

I am trying to communicate to a Sanyo projector using  pySerial and am having issues. I did some google searching and tried the  newline that seemed to help another forum poster, but this has not  solved my problem. I have verified that my baudrate and parity are all  set correctly. Here is my code (using COM13):

import serial
ser = serial.Serial(12)
ser.baudrate = 19200

print ser
print ser.write("CR0\n")
ser.close()


I  have also tried variations using "CR0\r", "CR0\r\n", "CR0\x0D" and  nothing seems to change it. I'm using another application to ensure that  I can speak to the Sanyo projector, and I get a correct response.

CR0 is a status read of the hardware that should return something like "80" which would mean "STANDBY"

However,  the responses that I keep getting are things like 3,4, or 5 which seem  to be errors, given that they are returned apparently based solely on  the length of the String I send, not based on the actual command.

Any ideas?

Thanks so much in advance!

-Damic

---

### Post by damic1 on 2011-01-13
Alright, I got some help, so I'll post it here.

I was simply missing a read() afterward.

Once the line: ser.read() was included after the write, everything works fine and dandy.

---

