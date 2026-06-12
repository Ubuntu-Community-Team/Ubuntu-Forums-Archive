---
title: "problem with minicom settings?"
date: 2011-07-30
forum: General Help
---

### Post by just_abhi22 on 2011-07-30
i am unable to communicate between two instances of minicom, connected  to 2 different ports (COM6 & COM7), connected together.why this is happening? 
my  settings for serial communication is 9600 8-N-1,flow control-hardware.  
[B]is anything else required??

please give an insight to this small problem.
[/B]

---

### Post by relay_man on 2011-07-30
These are two physical ports on your machine?

If you are connecting these ports with a serial cable, it is very likely that both ports are either DCE or DTE.  For them to communicate, you must connect them using a null modem cable. (transmit on port 6 connected to receive on port 7 etc.)

I would also recommend setting the flow control to "none" to get started.

Look here for help with serial cables and info about serial connections: [http://www.arcelect.com/rs232.htm](http://www.arcelect.com/rs232.htm)

---

### Post by just_abhi22 on 2011-08-04
i am using free software for virtual serial port that provides bridged virtual serial ports. so have two ports, COM6 with 1 instance of minicom(/dev/ttyS0) and COM7 with other instance of minicom (/dev/ttyS1). i cannot receive any message what i type.
same thing works well with two instances of hyperterminal (can see text on both terminals). i suppose there is some problem with minicom setting as it cannot recievce but can send (see my other thread on serial communication for more detail) but i could not figure it out.
please help me out

---

