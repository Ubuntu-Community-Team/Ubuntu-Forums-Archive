---
title: "Using Ubuntu to Backup Windows"
date: 2009-07-24
forum: General Help
---

### Post by indianballer24 on 2009-07-24
I plan on transferring all my data to another computer. I am currently using a macbook pro with osx and windows installed on it. I have purchased another identical macbook pro and wish to transfer my windows OS onto it exactly like it is on my first macbook pro. I have formatted the second macbookpro exacly like the first one and have installed osx on the first partition. Can I simply boot from to a linux live cd and copy the files from the windows partition on my old macbook and paste those files on the partition of my new macbook and preserve the exact same copy of windows with all settings and files?

---

### Post by LowSky on 2009-07-24
um sure using a usb drive to temporary store the files between machine.. its very easy

---

### Post by indianballer24 on 2009-07-27
So simply copying the files in the windows drive to a usb external hardrive and then copying the files to the new computer will transfer the OS and everything else exactly how it is? Are there any additional steps I need to take?

---

### Post by coffeecat on 2009-07-27
I do not believe that will work at all. If you try to clone a Windows installation with a simple file copy, the clone will not boot up. You'll need to do a block copy with the dd command, but I can't give you the details with confidence because this is one thing I've not tried.

What I can suggest is to point you to some proprietary but free (as in beer) software that will do the job for you. It's at...

[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

The main Macrium app runs in your Windows C: drive and makes an image of the whole C: drive to an external drive. You also prepare a bootable rescue CD with it. The rescue CD is based on Linux, so you can console yourself with the thought that you're using Linux (even if not Ubuntu) to clone your Windows install. :wink: When you're ready to clone the image to your new Macbook, you boot up with the rescue CD and use that to restore the backup image to the hard drive. At least in theory you do. It works on a standard PC, but I really don't know whether it works with a Bootcamped Mac.

However, and this is a BIG however. By cloning to different hardware (even if legally) you may run foul of Microsoft's inbuilt anti-piracy measures. Windows makes some sort of inventory of hardware with a scoring system and if it detects too many changes in too short a period, it requires revalidation. The trouble is that the MAC address on the network interface card has a particularly high score, so even though you are cloning between identical hardware, the different MAC code may cause you problems here.

---

### Post by indianballer24 on 2009-07-30
Anyone have a second opinion?

---

### Post by mcpancakes on 2009-07-30
This wiki page mentions various methods of backing up:

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by indianballer24 on 2009-07-31
But will the method of simply using an external harddrive to temporarily carry the files work?

---

### Post by indianballer24 on 2009-08-02
> **indianballer24 said:**
> But will the method of simply using an external harddrive to temporarily carry the files work?

Or possibly could I copy just the partition using a backup program?

---

