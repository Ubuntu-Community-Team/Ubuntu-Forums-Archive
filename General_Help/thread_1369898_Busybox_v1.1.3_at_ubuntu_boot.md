---
title: "Busybox v1.1.3 at ubuntu boot"
date: 2010-01-01
forum: General Help
---

### Post by gotanothergrot on 2010-01-01
I thought I'd start a new thread on this as the following thread was getting a little long winded.

[http://ubuntuforums.org/showthread.php?t=1367464](http://ubuntuforums.org/showthread.php?t=1367464)

Testing today, thank to the help from Leppie I can boot the Open-SUSE operating system OK.

Window's and Ubuntu are there In the Windows 2 grub menu list.

Windows boots OK. But I can't boot Ubuntu, I get busybox V1.1.3 (initramfs). 

I think Ideally I would rather have windows and Ubuntu on my system and use the live cd for open-suse and get to know it that way. but for now i just need to get Ubuntu up and running.

---

### Post by northrup on 2010-01-01
This happened to me if Windows wasn't shut down correctly; if an NTFS filesystem is marked as "in use", Ubuntu won't be able to read it at boot until Windows changes it during its own shutdown procedure.  Try booting into Windows again, then performing a clean shutdown.

Is this a regular Ubuntu install, or was it done using Wubi?

---

### Post by gotanothergrot on 2010-01-01
I installed ubuntu via windows.

A clean shutdown of windows has not helped

---

### Post by jmszr on 2010-01-01
gotanothergrot,

Perhaps this will be of help:

Wubi installs Ubuntu into a windows folder - usually a NTFS type of file system, this file system has a known reaction of being unstable in other operating systems like Ubuntu when a hard shutdown happens.

Just boot into windows, then shutdown correctly and then try to boot into ubuntu as normal, everything should work. (From LowSky)

If it doesn't:
                    Boot into Windows, Goto "My Computer", Right click the drive that you have installed Ubuntu in. Click Properties. Select the "Tools" tab and click "check now" under error checking (with Vista you might be asked for administrative rights). Make Sure "Automatically fix file system errors" is checked and click Start. After the checking is done, shut down  by using the start menu (Do Not hard reboot) and  try using Ubuntu now. ( From Ago)
                  
You can also accomplish the immediate previous tip by running chkdsk/f  in Windows and then shutting down properly.

---

### Post by gotanothergrot on 2010-01-02
No, it has not worked in fact I have tried half a dozen times.

I don't get the Ubuntu 9.10 start-up (splash screen) screen but I get an earlier version very bloated scrolling bar ect before Busybox

---

