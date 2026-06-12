---
title: "XSane as normal user"
date: 2005-02-10
forum: General Help
---

### Post by Syzygy on 2005-02-10
Hi!. I am new to Linux and I've been trying Ubuntu since last week. Most things are working fine, but I can't get Xsane to detect my scanner (Agfa snapscan 1212u, USB) as a normal user and I always have to start it with sudo in order to get it working. I have searched through forums and Google a lot before asking, but the solutions and answers I've found don't fix the problem (i.e.: adding myself to the scanner group, etc) or simply are too cryptic for a Linux novice...does anybody know how could I solve this?. The only thing that works is unplugging and re-plugging the scanner again, then Xsane detects it OK, but when I close the application I get an error message ("You don't have permission to create a file") and I'd like to use my scanner without needing to hotplug every time I need it...

Thanks in advance!.

---

### Post by m4ng0 on 2005-02-10
If you don't want to unplug/replug your scanner, you have to edit file permissions in
/proc/bus/usb. Type:
ls -l /proc/bus/usb/*/*
and find the file which represents your scanner.
Example:
search in /proc/bus/usb/devices for your scanner. If "T:" line says "Port=01 and Dev#= 2",
you have to type:
sudo chgrp scanner /proc/bus/usb/001/002
sudo chmod g+w /proc/bus/usb/001/002 

Then you can launch xsane as a normal user...

I think it's easier to unplug/replug  :-)

---

### Post by Syzygy on 2005-02-11
Thanks!. Do you know if these changes are permanent or if I'll have to re-enter this every time I reboot?. I have found out that my scanner is in /proc/bus/usb/001/003, and in the another subforum they've told me to do sudo chmod 660 /proc/..etc, and it works fine, but all changes are reverted when I close the session. I have even tried to make the scanner appear as mine with sudo chown etc, but, again, that setting is reset at shutdown...I'm gonna try your solution and hope it remains after rebooting! :-D

---

### Post by m4ng0 on 2005-02-11
No, it won't remain after a reboot, because usbfs is created every time you start the system. 
You may look this [thread](http://http://ubuntuforums.org/showthread.php?t=6963) to learn how to insert in a boot script the commands you have to type, so that they get executed every time you boot the system.

---

### Post by Syzygy on 2005-02-12
Thanks!. I've added "chgrp scanner /proc/bus/usb/001/003" and " chmod g+w /proc/bus/usb/001/003" to the end of /etc/init.d/bootmisc.sh and now it works fine!. I still get an error message ("could not create archive: permission denied") when I close Xsane but it's not very important since it allows you to scan and save images in folders where you have writing permissions. I write it here so that somebody else with the same problem can find the solution just by searching in the forum.

Now that the scanner issue is solved, I'll start with bluetooth!!!

---

### Post by alikilaij on 2007-01-18
> **Syzygy said:**
> Thanks!. I've added "chgrp scanner /proc/bus/usb/001/003" and " chmod g+w /proc/bus/usb/001/003" to the end of /etc/init.d/bootmisc.sh and now it works fine!. I still get an error message ("could not create archive: permission denied") when I close Xsane but it's not very important since it allows you to scan and save images in folders where you have writing permissions. I write it here so that somebody else with the same problem can find the solution just by searching in the forum.

Now that the scanner issue is solved, I'll start with bluetooth!!!

The fix for the could not create archive: permission denied, is to change the permissions in /home/youruserfolder/.sane/xsane.

 I am submitting this because I was up until 2 AM this morning trying to get SANE in a state where it was Wife friendly and this issue took me an extra 1/2 hour to resolve. 

 I hope someone can use this

---

