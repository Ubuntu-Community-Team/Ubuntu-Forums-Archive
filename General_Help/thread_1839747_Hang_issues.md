---
title: "Hang issues"
date: 2011-09-06
forum: General Help
---

### Post by tecs on 2011-09-06
Hello, Ubuntu community.

I am running Ubuntu 11.04 installed on a 16GB USB Key. Recently my system hangs after about 1 day of uptime. Unity side panel turns gray with no icons and Ubuntu top-left icon (for triggering Unity panel) disappears, Chromium exits, Skype logs out saying another instance may exist. No icons are left remaining and keyboard shortcuts do not work. I can only switch workspaces, cannot login to other ttys and sometimes even X server is terminated. Only hard restart fixes the issue. Some google search had led me to think the problem lies in auto remounting of the / device.

uname -a
```
Linux tecs-laptop 2.6.38-11-generic #49-Ubuntu SMP Mon Aug 29 20:47:58 UTC 2011 i686 i686 i386 GNU/Linux
```

syslog (before crash)```
Sep  6 02:20:49 tecs-laptop kernel: [37545.854268] show_signal_msg: 12 callbacks suppressed
Sep  6 02:20:49 tecs-laptop kernel: [37545.854275] chromium-browse[32078]: segfault at 0 ip   (null) sp bfd87bdc error 4 in libpangocairo-1.0.so.0.2800.4[110000+a000]
Sep  6 02:39:01 tecs-laptop CRON[10872]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Sep  6 03:09:01 tecs-laptop CRON[12750]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
Sep  6 03:17:01 tecs-laptop CRON[13245]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep  6 03:39:01 tecs-laptop CRON[14596]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
```

screen capture (after crash and X server quit)
 [[IMG]http://img822.imageshack.us/img822/5959/20110906001.jpg[/IMG]](http://imageshack.us/photo/my-images/822/20110906001.jpg/)

and a "Error: unable to enumerate USB device on port..." came after that.

Trying to log to another tty gives "EXT4-fs error (device sda1): ext4_find_entry: inode..." and some kind of an I/O error after that...

I guess all this happens because USB key is being "removed" on a software level while the system is running and this messes up everything.

Thanks in advance for any help, as it will be greatly appreciated!

---

### Post by 2F4U on 2011-09-06
If your usb key is not corrupt itself, maybe the usb port on your computer goes into power save mode?

---

### Post by tecs on 2011-09-06
> **2F4U said:**
> If your usb key is not corrupt itself, maybe the usb port on your computer goes into power save mode?

Is there any way I can check both? I did a fsck from another PC and USB key shows no errors. Also the crash has happened several times while I was using my laptop. IIRC issue appeared after some updates and I am pretty sure there was also a kernel update there.

System worked flawlessly for at least 2 months before the recent hangups. I am pretty sure I can rule out power saving on the USB port, which means there are only three possible reasons for failure - kernel, USB key and the port itself. How can I test under which one my case falls in?

---

### Post by 2F4U on 2011-09-06
The kernel would probably the easiest to rule out if you are willing to go back to the kernel that seemed to work.

---

### Post by tecs on 2011-09-07
Well the kernel is ruled out now... I set my kernel to a few months older one in grub, verified with `uname -a` it loaded the correct one and the system hung after around a day.

Some screen shots (these aren't in the log because of the drive 'unmounting'):

code here
[[IMG]http://img163.imageshack.us/img163/5798/20110907002.jpg[/IMG]](http://imageshack.us/photo/my-images/163/20110907002.jpg/)

and trying to log to tty1:
[[IMG]http://img841.imageshack.us/img841/4035/20110907004.jpg[/IMG]](http://imageshack.us/photo/my-images/841/20110907004.jpg/)


---

Trying on another USB port now, but I am afraid the system will die again, so... any way to check the flash stick? It is a Kingston DataTraveler 100 G2 16GB, came with a 5 year warranty and a guarantee of well over 100k writes per block - and I think I am well under those for 2-3 months of usage and the extensive use of ramdisks to ease the load of the flash stick.

EDIT: Just experienced another hang - USB port is also ruled out.

---

### Post by tecs on 2011-09-08
bump

---

### Post by sandyd on 2011-09-08
> **tecs said:**
> bump

Look on the second line of your last pic.
I/O Errors mean either corrupt filesystem, or damaged USB key. USB keys use the same technology as flash cards, and after a number of read/writes, they start failing.

---

### Post by tecs on 2011-09-09
> **sandyd said:**
> Look on the second line of your last pic.
I/O Errors mean either corrupt filesystem, or damaged USB key. USB keys use the same technology as flash cards, and after a number of read/writes, they start failing.

Yes, I came to the same conclusions, but how do I find out is it the filesystem or the device itself corrupt. Is there any reliable way to find out which one is the problem. I don't have any problem reformatting or buying a new USB key anyway - I just want to solve this issue, but don't want to take the easy way out.

---

