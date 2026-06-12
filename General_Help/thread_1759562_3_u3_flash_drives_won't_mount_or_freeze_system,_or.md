---
title: "3 u3 flash drives won't mount or freeze system, or won't unmount"
date: 2011-05-15
forum: General Help
---

### Post by ubume2 on 2011-05-15
I have 3 u3 type flash drives, 1 Memorex and 2 Sandisk Cruzers, and one non-U3 (JDSecure). The purpose is file storage.

All four work perfectly on Ubuntu 10.04 and XP.

I have continual problems with the U3 devices on 11.04. Problems vary from not being able to open the flash drives causing screen to freeze until I remove the device from the hub, or I am unable to unmount the device causing the desktop to freeze until devices are removed. Sometimes I am able to access files in the flash, before the freeze.

The non-U3 device works perfectly on  11.04, 10.04, and XP.

Sounds like a system problem to me.  I have google searched this to death, but can't find a solution.

Help would be appreciated.

---

### Post by mörgæs on 2011-05-15
This is a known problem. The application **u3-tool** from the repository deletes the U3 application (identifying itself as a CD drive) from the USB stick.

---

### Post by ubume2 on 2011-05-16
> **mörgæs said:**
> This is a known problem. The application **u3-tool** from the repository deletes the U3 application (identifying itself as a CD drive) from the USB stick.

I tried that application and got nowhere.
 
```
desktop@1004:~$ sudo u3-tool -p /dev/sdb1
```
Not enough arguments
u3-tool 0.3 - U3 USB stick manager

Usage: u3-tool [options] <device name>

Options:
	-c                Change password
	-d                Disable device security
	-D                Dump all raw info(for debug)
	-e                Enable device security
	-h                Print this help message
	-i                Display device info
	-l <cd image>     Load CD image into device
	-p <cd size>      Repartition device
	-R                Reset device security, destroying private data
	-u                Unlock device
	-v                Use verbose output
	-V                Print version information

For the device name use:
  '/dev/sda0', '/dev/sg3'

When I use /dev/sda0 and /dev/sg3 all I get is this again

For the device name use:
  '/dev/sda0', '/dev/sg3'


I also have a laptop with 11.04 installed and the flash drives are mounted, read, written to, and unmounted flawlessly.

---

### Post by ubume2 on 2011-05-16
> **mörgæs said:**
> This is a known problem. The application **u3-tool** from the repository deletes the U3 application (identifying itself as a CD drive) from the USB stick.

> **ubume2 said:**
> I tried that application and got nowhere.
 
```
desktop@1004:~$ sudo u3-tool -p /dev/sdb1
```
Not enough arguments
u3-tool 0.3 - U3 USB stick manager

New: 
I found this u3-tool code and used it. Read comments below. Proceed with caution.  It worked for me.
```
sudo u3-tool -p 0 /dev/sdb
```

Before I dared try that command I copied the contents of the flash drive to a folder on my Desktop, and then proceeded.  I ran the code above. It gives you a stern warning that it will remove EVERYTHING from the flash drive.  I proceeded with using u3-tool. I rebooted.  The flash mounted and unmounted properly. I could read from and write to it. My files were still there. 

But problem solved. Now I can use Natty Narwahl and my flash drives without Natty acting up.

Edit: I found these links regarding u3-tool which might be helpful:

[http://u3-tool.sourceforge.net/](http://u3-tool.sourceforge.net/)

[http://ubuntuforums.org/showthread.php?t=803809&page=2](http://ubuntuforums.org/showthread.php?t=803809&page=2)

---

### Post by mörgæs on 2011-05-17
Good, please mark the thread 'solved'.

---

