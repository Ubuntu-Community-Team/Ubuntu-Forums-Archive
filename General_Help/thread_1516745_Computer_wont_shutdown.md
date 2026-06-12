---
title: "Computer wont shutdown"
date: 2010-06-24
forum: General Help
---

### Post by ubunov on 2010-06-24
my ubuntu 9.10 (fresh) installation has shutdown problem. It is sporadic.. 90% of the times it does not shutdown. I have tried to shutdown from the command line as well but with no improvement. 
After logging out of the session when i use the shutdown button the screen goes black but the monitor and the cpu fan keeps running. I have to manually shutdown using the power button. 
Can anybody help me in this problem?

---

### Post by jesuisbenjamin on 2010-06-24
Hi there,

plenty of threads on that one:
[http://ubuntuforums.org/showthread.php?t=1469501&highlight=computer+shutdown](http://ubuntuforums.org/showthread.php?t=1469501&highlight=computer+shutdown)
[http://ubuntuforums.org/showthread.php?t=1516299&highlight=computer+shutdown](http://ubuntuforums.org/showthread.php?t=1516299&highlight=computer+shutdown)
[http://ubuntuforums.org/showthread.php?t=1514190&highlight=computer+shutdown](http://ubuntuforums.org/showthread.php?t=1514190&highlight=computer+shutdown)

Hope this helps :)

---

### Post by DominicF on 2010-07-02
I've been having the same problem for ages, I was thinking to replace my motherboard.  Any how, I think I solved my problem today.

I'm been running Mythbuntu and the issue I was seeing was that every second shutdown was hanging with the CPU fan still spinning e.g. 
1) I've started the machine and logon, I then shutdown from the menu or from xterm command, the machine will shutdown successfully.  
2)I then restart the machine, logon again and then do a shutdown and this time it will hang, I would need to hold the power button for 10 secs to totally powerdown or hit the reset to reboot.
3) My next attempt of logging on and shutting down will be successful again.

I came across this link:
[https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI)

I had to change my acpi setting in grub.cnf. And tried the number of different settings and experimented as above.

For me, booting with "nolapic" which disables the local APIC - I'm not really sure what this means but worked for me.  I must have done at least 10 successfull shutdowns.

Here are the steps:

open a terminal and type
"sudo gedit /etc/default/grub"

Look for the line:-
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 

Add to it the "nolapic" I had also removed splash command:
GRUB_CMDLINE_LINUX_DEFAULT="quiet nolapic" 

Update GRUB:
"sudo update-grub"

Shutdown your machine:
"sudo poweroff"

On your next startup and shutdown you should hopefully be seeing a successful shutdown (everything powered down).

I hope this helps.

---

### Post by stumped on 2010-07-07
I have the same problem. The above "fix" does not work for me.
You would think that since there are plenty of threads on this, that someone, somewhere, would have a true fix.

The shutdown and restart do the exact same thing...they both restart.

---

