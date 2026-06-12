---
title: "problem with grub menu"
date: 2012-05-08
forum: General Help
---

### Post by knarfman on 2012-05-08
[SIZE=3]I'm hoping someone can help ASAP for a solution to my problem.

I just installed (upgraded to) Ubuntu 12.04 and all worked fine until I went into Grub Customiser. I unticked what I didn't need (as I have done in previous versions) but when I went to reboot, all I get is the normal black screen but showing ONLY memtest -- instead of giving me the option of choosing between Ubuntu 12.04, Memtest AND Windows 7.

I must have unticked something I should not have. 

So basically, the only option I have after turning on my laptop now is to boot into Memtest. I cannot access Ubuntu or Windows 7. 

Can someone please tell me how to solve this problem? Your help will be MUCH appreciated. Everything is on there and I need access to it. There is nobody where I am right now who can help :cry:.
[/SIZE]

---

### Post by wojox on 2012-05-08
Reinstall Grub2 from a [Live-CD]("https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files") ;)

---

### Post by wilee-nilee on 2012-05-08
> **wojox said:**
> Reinstall Grub2 from a [Live-CD]("https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files") ;)

+1
Look for the instructions on purging the grub, then reinstall, in a chroot of the OS "if needed". A reload of the mbr may get you in, but I helped another with the same problem a couple of days ago on the IRC and they had to do a purge. 

Here is a link for that specifically, read carefully.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by knarfman on 2012-05-08
[SIZE=3]thanks for the replies. I don't have a live CD and the instructions look over-the-top for _my_ experience level as I have no clue what is installed where on the partitions, i.e. what they are named etc. in order to fix this.

I will try the purge thing first and pray that works.---EDITED TO SAY, DIDN'T SEE I NEED LIVE CD FOR THIS... :((

If anyone else knows some other (non complicated) way......

 [/SIZE]

---

### Post by wilee-nilee on 2012-05-08
To be honest if you don't have a live cd or loaded usb you are missing about the most important tool you can have.

This will allow you to fix your OS and get into windows to recover if it goes south on you.

You could try the supergrub disc, but there really is not any easier way. Supergrub may get you into the OS to fix from there. Otherwise there is not any easier way really.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

There is also a bootrepair tool as well, but to be honest the more you peck at it rather than doing a straight fix your risking a bricked OS to some extent if you're not experienced.

[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

---

### Post by knarfman on 2012-05-08
wilee-nilee, thanks again. am currently downloading the 12.04 iso on another computer and will burn it to a disk. i could not find my previous disk anywhere -- anyway, that one would have the previous version of the OS anyway.

once i have the live CD, which method do you suggest is the LEAST complicated way of restoring things without losing my operating systems/files? sorry to ask but i am not experienced with doing this and don't want to mess up things more than they already are. 

thanks in advance for any help you can give me.

---

### Post by wilee-nilee on 2012-05-08
I think it is a good start to try the link wojox gave you. Read carefully and copy and paste the commands, and note where the command has just a sdX that is the mbr like sda no numbers for partitions. Copy and paste the commands and put in the mbr letter and partition number in by hand.

[https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files](https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files)

Be sure to run. 

```
sudo fdisk -l
```To confirm the Ubuntu partition and how the HD is showing.When the command say's sdXX the second X is the Ubuntu partition, a number. **Also do not put grub in any windows partition.**

If you get into the Ubuntu install, **not from the live cd** be sure to run

```
sudo update grub
```Then fix the boot customization tool, you can run a purge and reinstall from the Ubuntu cd or the install if needed. The live cd purge would be using a chroot which is a little farther down the page, same section of the grub wiki link.

I will be on all day and others that are even better at this than myself will be as well so ask questions first, as you have been doing.

Good luck. :)

---

