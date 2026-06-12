---
title: "Ubuntu 11.04 Crashes Input/output error"
date: 2011-05-13
forum: General Help
---

### Post by tonyuprm on 2011-05-13
Hi all,

I have a Lenovo Thinkpad W510 with Ubuntu 11.04 and separate ext4 partitions for / /opt and /home. I have been having a lot of crashes with 10.04 and decided to try 11.04. Unfortunately the computer still crashes. I've been through the forums and some people seem to have similar problems but still no solution. 

The crash I've seen lately has to do with input/output errors. I can navigate the computer but Iam unable to open applications. I get a message saying Failed to execute child process "name-of-process" (Input/output error).  I cant open some of the folders in my home directory and the icon in nautilus changes from a folder to a blank file. 

If I do a ssh from another computer I get "sh: /usr/bin/xauth: Input/output error" when logged in. I cant do anything with the computer and it wont even take shutdown command. 

The only option is to force shutdown because it wont take any command or buttons.

Any help would be much appreciated.

Thanks!

Tony

---

### Post by 3rdalbum on 2011-05-13
Input/Output Error is one of the more serious error messages you'll see. Basically, the data on your hard disk is damaged. If you open Disk Utility and check your disk, you'll probably find that you have more bad sectors than you have spare sectors.

First thing you should do is back up ALL your data. Do this from a live CD. If Disk Utility shows that your disk is failing with too many bad sectors, then put your disk in the bin and buy a new hard disk. If there's few or no bad sectors, then it's just filesystem damage, and you can reformat the hard disk, reinstall Ubuntu onto it, and then put all the files back.

---

### Post by tonyuprm on 2011-05-13
Thanks for your reply. My disk utility does warns me about bad sectors. 

SMART Status: Disk has a few bad sectors

And when I run a self test I get:

Overall Assessment: Disk has a few bad sectors.

ID    Attribute                                                                                   Assessment           Value

Reallocated Sector Count:                                                                              Count of remapped sectors. When the hard drive                                         finds a read/write/verification error, it marks the                                            sector as "reallocated" and transfers data to a special           reserved area (spare area)

Assessment: Warning         

Value:
Normalized:   97
Worst:           97
Threshold:     36
Value:            68 sectors

Everything else seems ok.

I've installed/uninstalled Ubuntu several times now. And this is not the first time I see this crash, Ive never checked this utility though. I have no idea what is the order of magnitude of this problem by reading this output. Is there a way to make sure my problem is the hard drive, because if it is the computer is still under warranty. Can this have something to do with my disk partitioning?


Thanks,

Tony

---

### Post by subvertbeats on 2011-09-01
Interesting Tony.

Same issue here, W510 also.

My main HD is an SSD.

Sometimes the system can be stable for hours, other times only minutes.

Windows disappear, and get the same error as you when trying to run apps, including things like the shutdown dialog

Did you ever get to the bottom of this?

Im not convinced its a bad sector thing because I've tried secure erasing my SSD and shouldnt be any bad blocks

---

### Post by tonyuprm on 2011-09-01
Hi,

Yes. It was the hard drive. I called and got a new hard drive. I've been running Natty perfectly fine for a couple of months now. I did install Windows and ran one of the utilities for checking the hard drive (dont remember which one but its on their support website) and it said it was messed up. It was still under warranty.

gl,

Tony

---

