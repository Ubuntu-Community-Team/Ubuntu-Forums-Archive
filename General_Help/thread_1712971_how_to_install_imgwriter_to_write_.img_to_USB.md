---
title: "how to install imgwriter to write *.img to USB?"
date: 2011-03-23
forum: General Help
---

### Post by dragonfly41 on 2011-03-23
I'm trying to write an *.img file to a USB flash drive.

I've downloaded FreeDos-1.0-USB-Boot.img from here ..

[http://derek.chezmarcotte.ca/?p=188](http://derek.chezmarcotte.ca/?p=188)

I've also read this ..

[https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

Here is a log of my efforts so far ..

```

[COLOR=Blue]ubuntu@ubuntu:~$ sudo imagewriter
sudo: imagewriter: command not found

ubuntu@ubuntu:~$ sudo add-apt-repository ppa:ogra/ppa
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 2F5E654186577485B7B4440290345E8D2FEF0CE2
gpg: requesting key 2FEF0CE2 from hkp server keyserver.ubuntu.com
gpg: key 2FEF0CE2: public key "Launchpad PPA for Oliver Grawert" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)

ubuntu@ubuntu:~$ sudo imagewriter
sudo: imagewriter: command not found

ubuntu@ubuntu:~$ sudo apt-get install python-glade2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-glade2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

ubuntu@ubuntu:~$ sudo apt-get install usb-imagewriter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package usb-imagewriter
ubuntu@ubuntu:~$[/COLOR]


```So ..

How do I copy FreeDOS-1.0-USB-Boot.img to a USB?

How do I get imgwriter working?

---

### Post by _0R10N on 2011-03-23
[LEFT]Did you tried what is suggested here? [http://ubuntuforums.org/showthread.php?t=260752](http://ubuntuforums.org/showthread.php?t=260752)[/LEFT]

---

### Post by dragonfly41 on 2011-03-23
Thanks for the pointer .. I'm quite new to ubuntu (ex Vista crash) and still not familiar with commands

seems that dd might to the trick but reading this ..

[COLOR=Red]Caution is advised, using this command with the wrong operators can cause serious data loss. [/COLOR]

[https://help.ubuntu.com/community/DriveImaging](https://help.ubuntu.com/community/DriveImaging)

Here is the command which I guess I need .. to copy from Desktop *.img to USB in /dev/sdb1

```

$ sudo dd if=~/Desktop/FreeDOS-1.0-USB-Boot.img  of=/dev/sdb1

```Does that look safe?    Just one letter wrong in above command (e.g. /dev/sda1 and not /dev/sdb1) will wipe my primary disk in error.

Any arguments to add?

And I would still like to know where the imgwriter GUI is.

Thanks.

---

### Post by dragonfly41 on 2011-03-23
o.k. I gave the command a try (crossing fingers) and this is what I get ..

```

[COLOR=Blue]ubuntu@ubuntu:~$ dd if=~/Desktop/FreeDOS-1.0-USB-Boot.img of=/dev/sdb1
dd: opening `/dev/sdb1': Permission denied
ubuntu@ubuntu:~$[/COLOR] 

```

There are no applications accessing the USB.   Why is permission denied?

---

### Post by dragonfly41 on 2011-03-23
After clearing out the USB, dumping rubbish bin, unmounting and remounting USB I was able to get the command to run ..

```

[COLOR=Blue]ubuntu@ubuntu:~$ sudo dd if=~/Desktop/FreeDOS-1.0-USB-Boot.img of=/dev/sdb1
[/COLOR][COLOR=Blue]63488+0 records in
63488+0 records out
32505856 bytes (33 MB) copied, 0.264685 s, 123 MB/s
ubuntu@ubuntu:~$ [/COLOR]

```but .. GPartEd will not now run and the USB icon on desktop reads"4.0 GB Unrecognised"

There are no files copied into the USB.

Getting worried now that something has gone wrong.  

dd is a dangerous command in newbie hands..

....

Adding to the post

Removed my USB and GPartEd was able to launch.
Reinserted USB but it is no longer seen in Computers .. seems to be completely dead (a brand new 4GB USB).

How do I get it recognised to be re-formatted?   It shouldn't be this difficult!

....

Adding to this micro blog ..

o.k. I've managed to get back to a formatted USB using System > Administration > Disk Utility

So exactly where did I go wrong in writing an *.img to USB?

---

### Post by dragonfly41 on 2011-03-23
I searched for imagewriter in Ubuntu Software Centre

and the result - 
[COLOR=DarkRed]
Sorry, 'usb-imagewriter' is not available for this type of computer (i386)[/COLOR]

---

### Post by tredegar on 2011-03-23
> ubuntu@ubuntu:~$ sudo dd if=~/Desktop/FreeDOS-1.0-USB-Boot.img of=/dev/sdb1

Your command looks fine, and you normally have to be root to do this, or you will get "Permission denied".

ISOs generally (but not always) refer to the whole device, so you might try```
sudo dd if=~/Desktop/FreeDOS-1.0-USB-Boot.img of=/dev/[COLOR="Red"]sdb[/COLOR]
```
Then try booting from it.

If you gave us a link to where you are downloading this ISO from, we might be able to help you understand the associated instructions better. Meanwhile we are "in the dark".

---

### Post by dragonfly41 on 2011-03-23
Thanks for the confirmation ..

> [COLOR=Blue]ISOs generally (but not always) refer to the whole device, [/COLOR]

but note that this is an *.img file not *.iso.
I found the same advice here ..

[https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)
[COLOR=black]
[/COLOR]> [COLOR=black][COLOR=Blue]Command Line Interface
(ignore the device number; e.g. /dev/sdc, not sdc1)[/COLOR][/COLOR]Here is a list of devices (two USB sticks)

```

[COLOR=Blue]sudo blkid
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: LABEL="Ubuntu 10.10 i386" TYPE="iso9660" 
/dev/loop1: TYPE="squashfs" 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D8-0508" TYPE="vfat" 
/dev/sda2: LABEL="RECOVERY" UUID="5204ADEB04ADD271" TYPE="ntfs" 
/dev/sda3: LABEL="OS" UUID="C8A6B0E3A6B0D364" TYPE="ntfs" 
/dev/sda5: LABEL="MEDIADIRECT" UUID="72B4-788D" TYPE="vfat" 
/dev/sdb1: LABEL="FreeDOS" UUID="6CA6-F2BE" TYPE="vfat" 
/dev/sdc1: LABEL="Vista" UUID="5A0D18B62CA3DE07" TYPE="ntfs" 
/dev/sdc2: LABEL="Other" UUID="018A-2665" TYPE="vfat" 
ubuntu@ubuntu:~$[/COLOR]

```So the target device is /dev/sdb   (not /dev/sdb1 partition as I tried earlier)

The tutorial I have been following is here ..

[http://derek.chezmarcotte.ca/?p=188](http://derek.chezmarcotte.ca/?p=188)    (link was posted earlier in this thread)

and the *.img link to FreeDOS-1.0-USB-Boot.img.bz2

is here ..

[http://derek.chezmarcotte.ca/wp-content/uploads/2009/08/FreeDOS-1.0-USB-Boot.img.bz2](http://derek.chezmarcotte.ca/wp-content/uploads/2009/08/FreeDOS-1.0-USB-Boot.img.bz2)

I've now tried this command (targetting the device and not the partition)

```

[COLOR=Blue]ubuntu@ubuntu:~$ sudo dd if=~/Desktop/FreeDOS-1.0-USB-Boot.img of=/dev/sdb
63488+0 records in
63488+0 records out
32505856 bytes (33 MB) copied, 6.93894 s, 4.7 MB/s
ubuntu@ubuntu:~$ [/COLOR]

```Looking at /dev/sdb in GPartEd there is 30.98 MiB in FAT 16, with boot flag set.

I'm shutting down for the night (U.K. time) and I'll let you know if it boots into FreeDOS.

Thanks.

---

### Post by dragonfly41 on 2011-03-25
Just to wind up this thread .. FreeDOS did bootup o.k. in the USB.

Thanks.

---

