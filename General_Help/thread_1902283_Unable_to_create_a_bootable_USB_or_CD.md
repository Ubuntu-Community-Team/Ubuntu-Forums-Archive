---
title: "Unable to create a bootable USB or CD"
date: 2011-12-30
forum: General Help
---

### Post by ursus262 on 2011-12-30
Hi everyone.  I wonder if anyone could help as I am tearing my hair out trying to create a bootable USB or CD of 11.10.

I bricked my Netbook and need to re-install the operating system whcih previously had 10.04 installed.  I've tried everything, and even attempted to boot on my other laptop (the one I'm using now!) with no success.

Has anyone else had this problem?  Any ideas or suggestions or advice would be gratefully received.

Many thanks

---

### Post by BC59 on 2011-12-30
Which system you are using and you like to create the CD-USB?
For both Windows-Linux Netbootin is better to create bootable USBs. For a CD in Linux use the Brasero. In Windows 7 use the system CD creator, but don't forget that you have to specify you are burning an image.

---

### Post by ursus262 on 2011-12-30
Hi
Thanks for that, however I've followed all that and am still not getting anywhere.  I've done this successfully before, but it would appear that it's impossible to create bootable usbs or cds now.  Has it become a closed environment?

---

### Post by BC59 on 2011-12-30
This is no happening, because the images posted on Ubuntu.com are the same 2 months now. During those 2 months, millions of people burned CDs. The problem is somewhere else.
Did you try to download another .iso file? Sometimes fails the download.

---

### Post by gsgleason on 2011-12-30
verify the md5sum of the iso against the published version.

make sure you're burning the CD as an image rather than just writing the iso file to a disc.

---

### Post by ursus262 on 2011-12-31
Thanks for your help guys.  I got round the problem by having the USB stick created on a windows machine!  There appears to be a problem with the software in 10.04, which is a complete mystery to me.  Has anyone else had these difficulties?

---

### Post by gsgleason on 2012-01-03
Yes, actually.  I've had issues when the USB stick has a GUID partition table.

My solution was to zero out the first few MB and then create a new bootable partition with fdisk then create a vfat partition.

---

