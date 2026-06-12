---
title: "Killed Ubuntu 11.10 - how to recover?"
date: 2012-01-04
forum: General Help
---

### Post by JimLS on 2012-01-04
I have been working on a system for Mythtv.  Installed myth with apt-get.  Added root password.  Got most of MythTV working.  Installed lirc with apt-get.  Now system won't boot.  Can't get to text screen.  When I try to ssh I get the prompt for user and password but no response after I enter password.  A couple things I may have done to kill it...

When I installed LIRC a script asked for remote type, transmitter type, and serial port.  Serial ports were 1 or 2 - none was not an option although that's what I wanted.  Since I only have one serial port and wanted to use it for other things (I have MCEUSB device for LIRC) I selected serial port 2 which does not exist (afaik).  I also added a line to 
/etc/rc.local so only LIRC responded to IR events (at least that was the purpose):
echo lirc > /sys/class/rc/rc0/protocols

lirc complained that it was not able to load kernel modules during the install.  When I rebooted it wouldn't start.  Looks like I need to boot from a live CD to fix this (the rescue mode worked but I ended up in a read only file system).  Also, I am not sure what I need to look at or fix.  I can reverse the change to /etc/rc.local and can change LOAD_MODULES to false in the lirc config but those are only guesses...

---

### Post by JimLS on 2012-01-04
Did some more checking.  Most of the log files show a date that matches last attempted boot but are zero length - boot, udev, dmesg.  kern.log contains a last entry of yesterday - the last good operation.  I could post the end of it - a couple of "NX (Execute Disable)..." What else should I be checking?

---

### Post by JimLS on 2012-02-12
I hooked up a serial cable to a windows box to log kernel messages and when the grub menu came up I removed "quiet" and "splash" and added console for serial port (and tty0).  LIRC complained the serial port wasn't available but the system started ok.  Apparently the use of the serial console changed how things booted.  I shut down and booted without grub changes (don't think I even saw the menu on boot) and it booted ok.  Shut down, disconnected cable, system would not boot.  Reconnected cable, took "quiet" and "splash" from grub but DIDNT add serial console.  System booted ok.  

Operation does not seem to be consistent, at least from what I can tell.  I am a bit lost in all of this.  Any suggestions?

---

