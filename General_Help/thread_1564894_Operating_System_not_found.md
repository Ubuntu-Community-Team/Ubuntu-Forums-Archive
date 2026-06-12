---
title: "Operating System not found"
date: 2010-08-31
forum: General Help
---

### Post by JBudOne on 2010-08-31
Hey guys, first off I'm sorry if I'm posting under the wrong thread here.. Feel free to move it if need be. 

I have a Dell Studio laptop, and see Dell came with something called "Dell DataSafe" installed on it. I didn't care much about it, and just left it alone, until today when it said the package was expiring tomorrow. I thought that since I never use it, I may as well delete it...it was taking up over 40gb of space anyways. So since Dell didn't have any uninstall file for the DataSafe program, I just restarted into safe mode, and used CCleaner to uninstall both the DataSafe files. Everything was working just fine, and they uninstalled just fine too.

After restarting the computer again, Grub loaded up (I have Grub installed w/ Linux and Windows Vista dual booted on it), and listed this:


GRUB loading.
the symbol '&#9658;' not found
Aborted. Press any key to exit.
Copyright (C) 2000-2008 Broadcom Corporation
Copyright (C) 1997-2008 Intel Corporation
All rights reserved.
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting Broadcom PXE ROM.
Operating System not found



I checked the BIOS and it is booting from the hard drive, not the network. I've tried calling Dell Support, but the lady didn't really know, and she said I'm going to have to send it off to the professionals to retrieve my data.. I spent the past few hours over google, and found that  Dell Data Safe   actually writes to the MBR. I've loaded up my   Ultimate Boot CD   and tried a few things out on there, but all the options I tried show that it can't find my operating system. I also tried loading up the Vista installation cd, booting from that and checking to repair the system. The weird thing is that it searches for   the operating system, and it IS able to find it!!  But then when I try some of the options (recovering my files, repairing the startup, system restore), it shows that it cannot find the operating system / cannot repair the startup / does not see any system restore points listed. 

I'm totally lost and completely stressing out over here =[   What can I do ??  I  can reinstall Vista if need be, but what about all my files ??  Is there any way I can get them back ?  I have a lot of work files on here that took hours of work to accomplish. The Dell support lady said that I need to send it off to the professionals to restore my files; but what would they do anyways? I'll try anything, I just really don't want to lose these files! I know I have my work files on here, but I'm trying not to think about what else I will be losing, I can't bare the thought of having to start from scratch!

*sigh*   If anybody is reading this and has any idea, a clue, a suggestion, a previous experience ??  Please list it, anything, I'll take anything at this point to try and retrieve those files and then reinstall Vista (if needed). Any help is very much so appreciated..Thank you.

---

### Post by lmarmisa on 2010-08-31
I think you have to reinstall the GRUB loader.

I recommend you to follow the procedure of this thread (entry #3 of psycho5):

[http://ubuntuforums.org/showthread.php?t=1550148](http://ubuntuforums.org/showthread.php?t=1550148)

You will need an Ubuntu Live CD of the same version you want to fix.

Best regards,

Luis

---

### Post by JBudOne on 2010-08-31
Thanks for the quick reply Imarmisa!

I should have mentioned that my important files are actually located on the Vista HD.. the last time I even logged onto my Ubunutu partition (other than accidently selecting Ubuntu rather than Vista in GRUB), was nearly last year.

I tried this solution, but I'm guessing its for Linux only? Since I get to


sudo mount /dev/sda4 /mnt


and hit a "mount: You must specify the filesystem type". Also tried   /mnt/win   and    /mnt/ntfs     .. No luck. 

Interesting point, however, is that it DOES see my partition, along with  *gasp*   "Dell Utility" system.

my   sudo fdisk -l    lists:


```

Device Boot    Start    End      Blocks    Id     System
/dev/sda1         1       19     152586    de     Dell Utility
/dev/sda2        20     1978   15728640     7     HPFS/NTFS
/dev/sda3 *    1978    22184  162310078     7     HPFS/NTFS
/dev/sda4     22185    38913  134375693+    f     W95 Ext'd (LBA)
/dev/sda5     30118    38913   70653838+    7     HPFS/NTFS
/dev/sda6     22185    29788   61079067    83     Linux
/dev/sda7     29789    30117    2642661    82     Linux swap/Solaris  

```


I'm pretty sure /dev/sda4  would be the partition I'm looking for (since its the biggest, and I recognize the W95). Although I could be wrong

---

### Post by xircon on 2010-08-31
Also every time you boot Windows it will destroy grub unless you remove Dell DataSafe.  I believe the problem is being addressed:


[http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/2010/08/28](http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/2010/08/28)

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)

I would love to help, but I uninstalled DataSafe :)

---

### Post by lmarmisa on 2010-08-31
Linux is located in the partition /dev/sda6. Follow the intructions of the thread but change /dev/sda1 with /dev/sda6. If you are able to repair GRUB, both Vista and Ubuntu systems will start normally.

---

### Post by JBudOne on 2010-08-31
OMG!!   I stumbled upon this by COMPLETE accident.. I guess it wasn't that hard to find, but, under    Places, it lists,

Computer
OS
JDrive
63 GB Filesystem


All of which seem to contain my important files!!  (namely   OS & JDrive)..  THANK YOU Imarmisa!  I wouldn't have even thrown in my LiveCD and looked around if it wasn't for that. I checked now and was able to find (at least some of, so far) my work files in here. Its 4 am now, so I think its finally time for bed for me =]

Tomorrow I begin a full day of restoring these files and reinstalling Vista, along with my other programs again. I have a feeling there may be issues with reinstalling Vista (although that could just be the anxiety speaking). But in any case, I'd like to leave this thread up in case of any other noobs like me running into this similar problem.

I don't understand how Ubuntu can see these files though? When Ultimate Boot CD and Vista Installation cd can't?   Oh well, Ubuntu = magic in my eyes as of now  =P   Thank you again!

---

### Post by lmarmisa on 2010-08-31
I believe that you do not need to reinstall Vista at all. Simply you have to repair the GRUB loader program. That is all.

---

### Post by JBudOne on 2010-08-31
Imarmisa, you were 100% right!

This worked, COMPLETELY fixed up the issue with Grub. Thanks so much for this, since now I don't have to go through and reinstall everything :P   

I also called up Dell and showed this thread to them; they said that they will be using this for any future calls relating to this problem   =]


You really helped me (and potentially a lot of other Dell/Grub users) today. Thanks!

---

### Post by pricetech on 2010-08-31
It's sad that Dell support was clueless, but hopefully they actually will use this thread and maybe they'll even learn something.

---

### Post by daveurjit on 2011-03-19
Hey guys I need some help with my laptop. Its an acer aspire laptop and my friend put it on hibernate. When i turned it on it went to a black screen and this message appeared: "pxe-e61 media test failure, pxe-m0f: exiting PXE ROM" and then "operating system not found". Does anyone know how to fix this?? I need some serious help

---

### Post by NadiyaTT on 2011-10-31
I installed ubuntu9.1 two years ago, with a parallel windows vista(first  installed vista). Now a days before loading getting a message like  "Operating system not found" ; if i restart the grub may automatically  get loaded.... i want an immediate solution to these....

---

