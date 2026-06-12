---
title: "Unsupported Hard Drive? Ubuntu 10.10 won't play nice with it."
date: 2010-11-11
forum: General Help
---

### Post by Slinkee2k on 2010-11-11
Hey, all! WOW, there's a lot of info to sift thru here. Okay, here's my quick problem/question:

I burned a copy of Ubuntu 10.10 [COLOR=Red](EDIT: Not the 10.10 Beta)[/COLOR] and installed flawlessly to my HP tx2500z laptop. However, on another computer, at the very end of the installation, the same Ubuntu live disc fails to install the boot loader. I built the other computer with an older Asus (Intel, DDR-era) mobo, and the installer could not install the boot loader. I moved the 80GB SATA HDD to my nicer, newer desktop (an Asus AM2 board, M2N32-SLI). I installed Ubuntu there, and I get the exact same error. Does it not like the HDD?

Anyway, using the Ubuntu live disc, from the console, I managed to manually install "grub" (legacy v0.97) to the drive by mounting the Ubuntu partition to /mnt, and using "grub-install". Now, the HDD will FINALLY actually boot, but despite the presence of /boot/grub/grub.cfg, boot just dumps me to the grub console.

Please, ask me questions, and give me answers/suggestions. I gave it my best! (hours and hours, that is). Thanks!
-Slink (Slinkee2k)

---

### Post by dcstar on 2010-11-12
> **Slinkee2k said:**
> Hey, all! WOW, there's a lot of info to sift thru here. Okay, here's my quick problem/question:

I burned a copy of Ubuntu 10.10 beta, and installed flawlessly to my HP tx2500z laptop. However, on another computer, at the very end of the installation, the same Ubuntu live disc fails to install the boot loader. I built the other computer with an older Asus (Intel, DDR-era) mobo, and the installer could not install the boot loader. I moved the 80GB SATA HDD to my nicer, newer desktop (an Asus AM2 board, M2N32-SLI). I installed Ubuntu there, and I get the exact same error. Does it not like the HDD?
.........

If the obviously very old HD has bad blocks where the boot loader is written, then things like this can occur.

There is no need to use a 10.10 beta ISO when updated images are currently available.

---

### Post by Slinkee2k on 2010-11-13
Thank you. I was considering that, but it wasn't obvious to me.

Please be patient with me! :) I guess I will try to write the OS to a different physical section of the disk. I have had to do this with W$ in the past.

I'm still a Linux newb. Is there a utility on the live disk where I can test every sector of the hard disk? I figure there's an option in the disk checker.

Thanks much!

---

### Post by Slinkee2k on 2010-11-14
Okay, I figured out that I can do a thorough disk check for bad sectors using "badblocks". I formatted the entire disk blank (which was unnecessary) and I'm doing a fully "destructive" read/write check on this disk. I was metaphorically "banging my head against a wall" for about 15 minutes trying to figure out why the -X switch wouldn't work (-X ignores the "disk in use by OS") until I realized it was a capital X. -_- ugh. ](*,)Anyway, badblocks is 50% done now. I'll report the bad sectors at the end of this post, in an edit.

Note: I see that the "SMART data" from the HDD reported "a few bad sectors". Yeah. I bet there are.

Note: Any Linux newbs reading this, please note that using badsectors can/will destroy your data if you tell it to! It can also be used without disrupting data, but won't do as thorough a check.

In closing, I'm SO happy to be learning this stuff! Such power and versatility... I have always appreciated the stability and reliability of Linux, but that was from the other side of the window pane. I'm sorry, perhaps that is spelled "Windows Pain"? IDK. I'm getting comfier with Ubuntu. :)

[COLOR="Red"]EDIT:[/COLOR] WONDERFUL. :mad: I let it scan for hours, but didn't set an output file. Somehow, the console window closed. Looks like my cat was on the keyboard. Unplugged the controls this time, and set an output file to the desktop of the live OS.

---

### Post by Slinkee2k on 2010-11-14
Okay, scan finished. Said there were no bad sectors found!! :( Did I do something wrong?

Here is the output:
```
ubuntu@ubuntu:~/Desktop$ sudo badblocks -wvsX /dev/sda -o results.txt
Checking for bad blocks in read-write mode
From block 0 to 78150743
Testing with pattern 0xaa: done                                
Reading and comparing: done                                
Testing with pattern 0x55: done                                
Reading and comparing: done                                
Testing with pattern 0xff: done                                
Reading and comparing: done                                
Testing with pattern 0x00: done                                
Reading and comparing: done                                
Pass completed, 0 bad blocks found.
ubuntu@ubuntu:~/Desktop$ 

```What gives?? Why would Ubuntu fail to install to this drive, with two different motherboards? The Ubuntu 10.10 install disc verified itself was correct. What do I do now?
Thanks.

Hmm, this thread is getting no attention. I guess I will post a new thread.

Posted new thread here: [http://ubuntuforums.org/showthread.php?p=10123763](http://ubuntuforums.org/showthread.php?p=10123763)

---

