---
title: "Wakes up right away after suspend"
date: 2006-02-04
forum: General Help
---

### Post by anandrd on 2006-02-04
I just installed Ubuntu 5.10 Breezy on dell inspiron 6000 and it works great. The suspend feature almost works. Sometimes it wakes up immidiately (after a second or two) after going into suspend mode. It happens regardless of whether I go in suspend mode by closing the lid or by choosing suspend from the log out menu. Also, whenever it comes back from suspend, it makes an annoying loud beep.

Can someone help me get a stable suspend and turn off that beep?

---

### Post by Ocxic on 2006-02-04
check your bios to make sure you don't have any "wake from lan" type options enabled.

---

### Post by anandrd on 2006-02-04
No. Suspend used to run without problems in Windows and I haven't changed BIOS settings. Still, I checked again and couldn't find any 'wakeup on lan' type options enabled.

---

### Post by anandrd on 2006-02-05
Does anyone know how to fix it?

---

### Post by anandrd on 2006-02-05
So, I don't think it actually goes into the suspend mode. That is, the power light doesn't dim (which happens in suspend mode). So it tries to go into suspend mode but cannot.
Does anyone have any idea/solution?

---

### Post by anandrd on 2006-02-07
I ran sleep.sh from the command-line and I am giving the parts of the output that I think are not good -

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

xscreensaver-command: can't open display :0
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

xscreensaver-command: can't open display :0
Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
xset:  unable to open display ":0"
There is already a pid file /var/run/dhclient.eth0.pid with pid 6751
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Does this help?

---

### Post by anandrd on 2006-02-07
More info-
Suspend used to work flawlessly earlier (I don't remember what made it act weirdly as it does now). The beep and this "waking up immediately" started at the same time. Hope that helps.

---

### Post by anandrd on 2006-02-08
I think I have made some progress on this issue. I read /var/log/kern.log (especially the activity between my running sleep.sh and the computer's resuming back to life automatically after 5 seconds.) 

What is happening is it cannot stop all the tasks. There is one task that refuses to stop and then it restarts all the tasks and I think that is why the system resumes. To be explicit, this is the relevent part from /var/log/kern.log

Feb  8 00:21:09 localhost kernel: [4297107.388000] Stopping tasks: ===========================================================================================
Feb  8 00:21:09 localhost kernel: [4297114.222000]  stopping tasks failed (1 tasks remaining)
Feb  8 00:21:09 localhost kernel: [4297114.232000] Restarting tasks...<6> Strange, hald-addon-stor not stopped
Feb  8 00:21:09 localhost kernel: [4297114.245000]  done

Now, PLEASE SOMEBODY HELP ME...... don't make me go back to Win XP....

---

### Post by nanotube on 2006-02-08
well... the obvious thing to try is to kill the hald-addon-storage process, before you go to sleep, and see if that helps :) try it.

---

### Post by anandrd on 2006-02-08
I did "ps aux", found out its PID and tried to kill it but it doesn't die .... :( 
In the system monitor, it shows up as "Uninterruptible"

---

### Post by jazzgossen on 2006-02-08
FWIW, I had similar problems with my stationary computer (power off worked from Windows, but when shutting down or hibernating from Ubuntu, the computer instantly powered on again).

I solved it by disabling the "wake on any key" setting in the BIOS.

---

### Post by anandrd on 2006-02-11
Now I just stop or kill the process hald-addon-storage while it's still sleeping and things work well. Not an ideal solution I guess, but it works.

---

