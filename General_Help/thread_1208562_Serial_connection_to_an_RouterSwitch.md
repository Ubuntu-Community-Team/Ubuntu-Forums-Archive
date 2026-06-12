---
title: "Serial connection to an Router/Switch"
date: 2009-07-09
forum: General Help
---

### Post by Nimanic on 2009-07-09
Hi all,
 
i am searching now for two days and have no idea where to start.
 
I have an embedet Hardware (ix86) with an Voyage (Debian) Linux running.
 
I want to connect this PC to and DSL Modem/router to configure this Modem/Router. The connection the the PC is done by SSH.
 
i already try to use Putty with X11 forwarding, didnt work.
I already try it with minicom and also this is nor working.
 
I know that my serial port is /dev/ttyS0 and i was also able to connect to this embedet PC through the serial port from an other PC (Nullmodem).
 
I already deactivat getty in inittab to prevent that a serial port is used twice.
 
 
If anybody can send me an how to or give some hints to to go an i would be very happy.
 
I am new to Linux so i am not used to lots of expression, so if possible make it foolproof. :-D
 
 
Thanks for your help
 
 
Maybe also important, i need the output of the serial port input in text file and on my ssh session

---

### Post by t4thfavor on 2009-07-10
I believe there is a language barrier keeping anyone from asnwering this. 

I will give it a try:

You should be able to use Minicom to connect the serial port on your PC to the serial port on the embedded PC provided that the kernel on the embedded PC has been told to use the serial console.

If its for embedded devices it should be setup that way. You will have to find out what speed the port is set at, and make sure your PC is the same.

About logging:

I think Minicom can be setup to record a log of all text input/output. I know that Putty under Windows can do serial now, and I know it logs its output if told to do so.

Hope I could help.

---

### Post by Nimanic on 2009-07-10
Hi t4thfavor,
 
thanks for your answear.
 
but thats not realy what i want to do. Maybe its easier to think that the embedet PC is a normal PC i am sitting at and now i want to open a serial terminal to an router to configure this.
 
Like i would do it in Windows with Hyperterminal or Terraterm.
 
 
Thanks for your help.

---

### Post by niteshifter on 2009-07-10
> **Nimanic said:**
> 
 
Like i would do it in Windows with Hyperterminal or Terraterm.
 


Hyperterminal == terminal emulator. Talk / listen via serial port.
minicom == terminal emulator. Talk / listen via serial port.

minicom package description:
> Minicom is a clone of the MS-DOS "Telix" communication program. It emulates
ANSI and VT102 terminals, has a dialing directory and auto zmodem download.

---

### Post by Peter09 on 2009-07-10
Just to check -
most routers have a web interface for setup / configuration. When you say serial interface do you mean serial or ethernet (Wired). I know this is basic but sometimes confusion can arise.

---

### Post by Nimanic on 2009-07-10
Hi all,
 
thanks for your replays.
 
I already solved my problem :-( it was the serial port of my router, i had to restart it, because it had a problem with the initialisation.
 
For your information: i realy used RS232 connection because, the router i am using is sending out much more debug information over serial than vie telnet or SSH.
 
 
Thanks a lot for your help.

---

### Post by t4thfavor on 2009-07-10
Sounds like he's using a "real" router a opposed to a SOHO linksys or D-Link. Most "routers" have a serial interface so that you can get into them if you hose up the networking capabilities therefore limiting your usage of things like SSH, or the web interface.

The Linksys WRT54G has a serial terminal as well, it's just not soldered to the board, and the line levels are at 3v instead of 12v so a level shifter is required to interface with it from a standard PC.

I just thought that would be a relevant peice of information to add to a thread about serial terminal access to a router.

The serial terminal spits out more debug, because the Kernel is probably set to print debug to ttyS0, which is nice if your trying to fix an OS issue, or a real sticky network issue.

---

