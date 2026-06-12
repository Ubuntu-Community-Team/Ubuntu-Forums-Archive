---
title: "Endgame"
date: 2010-03-18
forum: General Help
---

### Post by Fitch on 2010-03-18
Is there anything in Karmic that would get something to run at shutdown?

I have a US Robotics 56K message modem ( USR5668 ) which receives faxes during the day, and has to switch to answer machine / fax at night.  It has a memory when the computer is switched off - which is handy, and all the phones switch over to the message modem extension automatically.

All I want is to do is send the command AT+MCA=1 to the serial port ttyS0 at shutdown.

Any sportster owners might say that this goes to answer machine only, so if they want to tell me the correct string for answer/fax please feel free...

I do have vm installed (or whatever vgetty calls it), so maybe it can be done there as well, again, anyone, please feel free to elucidate.

---

### Post by mastermindg on 2010-03-18
The simplest way to do this would be to create a shell script, drop it under /etc/init.d. Then create a symbolic link under /etc/rc6.d. That way it will be run at shutdown.

---

### Post by Fitch on 2010-03-18
Thanks for the reply,

Sorry to be picky, but what commands would I actually put in the shell script?

---

### Post by soltanis on 2010-03-18
It's been a while since I messed with modems but I think there's a serial port communications program called "kermit" that will let you send commands to your modem via a shell script. Look it up?

---

### Post by Fitch on 2010-03-18
I had a look at Kermit, then crawled into a hole and cried a little.

I thought of doing "echo AT+MCA=1 > /dev/ttyS0" , not for long though since it doesn't work.

The other thing is that I have to quit efax-gtk - or at least put it on standby, before I can send any commands, so that would have to go into the script as well.

---

