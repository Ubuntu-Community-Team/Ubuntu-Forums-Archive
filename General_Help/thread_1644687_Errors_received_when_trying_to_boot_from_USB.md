---
title: "Errors received when trying to boot from USB"
date: 2010-12-13
forum: General Help
---

### Post by steveb52 on 2010-12-13
Hi,

I have a relatively new computer that won't boot Win 7.  After going through a lot of tries, I got a suggestion that I try to boot using Ubuntu from a USB flash drive ( since I can't burn a CD).  I followed the procedure to put the necessary files (Version 10.04 64 bit if I recall correctly) on the drive and tried to boot using it.  I got this message:

SYSLINUX 4.02 2010=07-21 EDD Copyright (C) 1884-2919 H. Peter Anvin et al
ERROR: No configuration file found
No DEFAULT or UI configuration directive found!
boot:

When I tried to boot again (from the above) I just got the second message (No DEFAULT etc.)

How can I fix this?

Thanks,
Steve

---

### Post by Rubi1200 on 2010-12-13
Hi and welcome to the forums :)

Sounds like a corrupted image or a bad install.

How did you put it on the USB?

Have you tried UNetbootin?

---

### Post by steveb52 on 2010-12-13
> **Rubi1200 said:**
> Hi and welcome to the forums :)

Sounds like a corrupted image or a bad install.

How did you put it on the USB?

Have you tried UNetbootin?

Hi!  And thanks for the help.  I put it on the flash drive using another older computer running Win XP, using the instructions given and the Universal USB Installer.  It said that the install was completed successfully.

I don't know what UNetbootin is, but if it can help me boot this computer, I'm definitely interested!

Steve

---

### Post by C.S.Cameron on 2010-12-14
First check the iso's MD5SUM.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If it is ok try UNetbootin:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by steveb52 on 2010-12-17
OK, I tried several other ways I found to boot off a USB drive (like WintoFlash or something like that), but none of them worked including UNetbootin.  It always seems to be missing one file or another.  The BIOS includes 3 different ways to boot off USB, but none works.  Could the USB drive be too old or the wrong type or something?

I'm also trying the Command Prompt, even though I haven't used the commands for a LONG time (but I can get them off another computer's web connection).  Would I use an exterior drive to connect and then copy my files that way?  Also, I don't see the files on the computer.  I can find Windows files and under Users, some other directories, but I can't seem to find the files I want to copy.  Where would my data files be located?  I know this can be a hassle, so if I could be directed to some instructions, I'd really appreciate it.

Thanks again,
Steve

---

