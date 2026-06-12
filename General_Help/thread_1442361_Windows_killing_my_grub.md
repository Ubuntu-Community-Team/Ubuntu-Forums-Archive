---
title: "Windows killing my grub?"
date: 2010-03-29
forum: General Help
---

### Post by trailhead on 2010-03-29
First post here, new to Linux and not a geek so please be gentle ;)...
 
I'm trying Ubuntu 9.10 on an older Toshiba laptop and I quite like it. Unfortunately a couple aps I need in the workshop require windows so I've also installed XP Pro. Almost every time I use windows there's a problem on the next reboot. Tries to load GRUB, which apparently isn't there any more and goes into a grub loading-reboot loop.
 
Thanks to a couple posts here I've gotten adept at re-installing grub from the live CD.
 
I've read here where something sees grub in the MBR, thinks it's bad and removes/disables it but haven't seen what looks like the answer to my problem. I don't have any antivirus running with windows, just the basic install and two third-party programs.
 
I don't seem to have any trouble as long as I don't boot to windows so I assume it's something windows is doing?
 
Any ideas?
 
Thanks
Duane

---

### Post by oldfred on 2010-03-30
I have been  collecting these issues. The first link is where meierfra posted most of the issues.

And welcome to the forums. 

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
HP ProtectTools, Dell Recovery, and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct issues with MBR
[http://ubuntuforums.org/showthread.php?t=923576](http://ubuntuforums.org/showthread.php?t=923576)
[http://ubuntuforums.org/showthread.php?t=1344828](http://ubuntuforums.org/showthread.php?t=1344828)
[http://ubuntuforums.org/showthread.php?p=8433673](http://ubuntuforums.org/showthread.php?p=8433673)
Found out today after numerous searches the issue. I found the answer here -- I had heard dynamic disk partioning may be the cause (which I don't have) or virus software (which I removed). I have a Compaq netbook -- HP product. Turns out they have HP Recovery tools that will overwrite parts of the MBR. The thing is, I uninstalled every single piece of their recovery software, sync software, etc, cuz I didn't want any of that crap. I went into services, and lo-and -behold -- there was the hpqwmiex service running. So I disabled it, did the update-grub thing again, logged into Windows then back into Ubuntu, and all is well!
Another windows issue that caused grub2 issues.
Looks like I found the culprit. It was Norton Ghost running in the background, that I had just recently installed. I disabled it during startup through msconfig and no more trouble. 
Thus it seems the my antivirus scans the master boot record and as it finds something strange (Grub), it kind of deletes it and make my Boot bugged.
I un-installed norton and a gateway recovery management application and that seems to have fixed it.

---

### Post by trailhead on 2010-03-31
Thanks Oldfred, that sure gives me info to start with.

---

### Post by trailhead on 2010-05-03
Well, I haven't made any progress on this issue. From reading the referenced links most people seem to find the problem caused by other than Windows (antivirus or proprietary process from Dell etc). I don't think I have any of that, just windows. The only thing I could think to try was disabling windows firewall, which didn't help.
 
If I posted a list of processes running in windows would wiser heads be able to spot a likely culprit?
 
I just want this to work, is degrading to Grub Legacy my best shot?
 
Thanks

---

### Post by john newbuntu on 2010-05-03
There's gotta be something in windows messing the MBR.  If you are curious, you could make a copy of a good MBR and compare it with a copy of one after you log off of windows to confirm MBR change.
```
dd if=/dev/sda of=grub.mbr bs=512 count=1
```One possible solution for you would be to install Grub2 into another partition, say your root partition (/).  You could then use windows XP bootloader to dual boot by following the instructions in:
[http://bkpavan.wordpress.com/2008/04/02/how-to-boot-linux-using-windows-bootloader-xp/](http://bkpavan.wordpress.com/2008/04/02/how-to-boot-linux-using-windows-bootloader-xp/)

---

### Post by trailhead on 2010-05-31
> **john newbuntu said:**
> There's gotta be something in windows messing the MBR. If you are curious, you could make a copy of a good MBR and compare it with a copy of one after you log off of windows to confirm MBR change.

 
Thanks. Next stupid question: I've done hexdumps of the good and bad MBR, now do I go through character-by-character looking for differences? What do I do when I find them?:confused:
 
Cheers

---

### Post by wilee-nilee on 2010-05-31
> **trailhead said:**
> Thanks. Next stupid question: I've done hexdumps of the good and bad MBR, now do I go through character-by-character looking for differences? What do I do when I find them?:confused:
 
Cheers

You would probably be best to start a new thread and post the bootscript in code tags.[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end. Or just highlight the text and hit the # in the reply panel. It has been 4 weeks since your last post and I doubt if anybody keeps a auto-email notification for that long.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Mark this thread as solved and post the script in a new thread and give a description of what actually boots.

Actually most problems are with people installing grub into a partition, especially a NTFS partition.

---

