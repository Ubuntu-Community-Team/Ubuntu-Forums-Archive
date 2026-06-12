---
title: "Don't know if this is a Windows and Ubuntu issue"
date: 2009-12-09
forum: General Help
---

### Post by Justinfinity on 2009-12-09
...or maybe even a hardware issue.

Background leading to the issue:

A few days ago Windows 7 completely crashed randomly. On reboot, it notified me that the boot files were corrupted (I haven't had a crash literally in years, so what caused this problem is beyond me). Luckily, I had Ubuntu on a separate partition, and I was able to boot into and access and back up my files from Windows 7.

I need Windows as much as I like Ubuntu. So I decided to delete the partitions and reformat my HDD to install Windows 7.

The issue:

I don't know what went wrong, but my Windows 7 disc kept freezing during installation. It's a perfectly fine disc. Though, just in case it was the disc, I tried a Windows XP disc I had. This goes to a BSOD on installation. I then tried a Windows 2000 disc, this too would freeze during installation. I then tried different Windows XP disc, this too goes to BSOD. Then I tried a different Windows 7 disc, and after the windows files load, it freezes, not even allowing me to begin to install it. I tried the original Windows 7 disc again, and it now does the same thing. I've tried several times on 5 different discs wishing for a bit of luck... it never happened.

In all honesty, I don't know what the hell is going on. A friend let me borrow her computer so I was able to download Ubuntu, and after a couple tries without freezing during the installation process, Ubuntu finally installed fine on this computer (though, now either my keyboard or mouse randomly stops working. It happened while writing this message, which I then had to reboot and retype). I know there's no problem with the discs as they work fine on her computer (she asked me to install a fresh copy of XP and it works fine).

I don't know if its a problem relating somehow to Ubuntu/Grub when Windows first crashed, or if it could be a hardware problem.

If anyone can provide any insight to my problem, and help me get Windows 7 back on this computer, it'll be greatly appreciated. I've been going at this for 2 days, and frankly, its stressing me out lol. I don't know how many times I've deleted partitions and reformatted my HDD.

---

### Post by audiomick on 2009-12-09
My first suspicion would be that the drive that windows was on is failing. That would account for the crash, and that the windows installers were having trouble.

Don't forget that re-installing windows will overwrite your Grub, which you will have to re-install.

---

### Post by ElevenWarrior on 2009-12-09
*agrees with audiomick*

---

### Post by Justinfinity on 2009-12-09
> **audiomick said:**
> My first suspicion would be that the drive that windows was on is failing. That would account for the crash, and that the windows installers were having trouble.

Don't forget that re-installing windows will overwrite your Grub, which you will have to re-install.

I was hoping it was a Grub problem, that's why I decided to delete all partitions and reformat to the whole drive to NTFS to install Windows. But none of the installations installed completely.

I was thinking it is a HDD issue. I was going to buy a new one, because I thought that this one finally gave out on me, but its working fine as I'm using Ubuntu on it now. I'm thinking of buying a new HDD anyway and try to install Windows on it if I can't figure out what exactly is wrong.

---

### Post by hobit on 2009-12-09
I had some issues installing Ubuntu recently and what it boiled down to was a bad DDR2 module.  You might also consider a bad CD-ROM cable or for that matter a bad CD drive.  Hope this helps.

---

### Post by Justinfinity on 2009-12-09
> **hobit said:**
> I had some issues installing Ubuntu recently and what it boiled down to was a bad DDR2 module.  You might also consider a bad CD-ROM cable or for that matter a bad CD drive.  Hope this helps.

Yeah, I was afraid of that. I'm guessing it could be a number of hardware problems. Perhaps I should just invest in a new computer. lol.

Thanks for the reply, though.

---

### Post by Groundswell on 2009-12-09
before you go spending money, do the simple things like memtest, make a memtest boot cd if you have to, also use a distribution's live cd and run the live desktop. that should confidently give you an idea weather the cd drive/cable is bad.

if both those things pass, then you can be pretty sure it's the hard-drive.
have any old hd's laying around? do a test install?

and last, any new hardware? even usb? i have windows 7 and to just install it without the installation freezing i had to disable my usb controller, take out my second graphics card/tv card, and 2nd harddrive. took 5 hours of playing with it. win7 has been a complete piece of crap to me [-( go figure. Then while trying to diagnose a BSOD issue, i reinstalled windows, just to find this time around i didn't need to disable anything.

just keep in mind win7 installation can be fickle.

edit: wanted to add, this isn't just me, lots of posts on the web about it, specific to the usb controller.

---

### Post by gradinaruvasile on 2009-12-09
> **Justinfinity said:**
> ...or maybe even a hardware issue.

Background leading to the issue:

A few days ago Windows 7 completely crashed randomly. On reboot, it notified me that the boot files were corrupted (I haven't had a crash literally in years, so what caused this problem is beyond me). Luckily, I had Ubuntu on a separate partition, and I was able to boot into and access and back up my files from Windows 7.

I need Windows as much as I like Ubuntu. So I decided to delete the partitions and reformat my HDD to install Windows 7.

The issue:

I don't know what went wrong, but my Windows 7 disc kept freezing during installation. It's a perfectly fine disc. Though, just in case it was the disc, I tried a Windows XP disc I had. This goes to a BSOD on installation. I then tried a Windows 2000 disc, this too would freeze during installation. I then tried different Windows XP disc, this too goes to BSOD. Then I tried a different Windows 7 disc, and after the windows files load, it freezes, not even allowing me to begin to install it. I tried the original Windows 7 disc again, and it now does the same thing. I've tried several times on 5 different discs wishing for a bit of luck... it never happened.

In all honesty, I don't know what the hell is going on. A friend let me borrow her computer so I was able to download Ubuntu, and after a couple tries without freezing during the installation process, Ubuntu finally installed fine on this computer (though, now either my keyboard or mouse randomly stops working. It happened while writing this message, which I then had to reboot and retype). I know there's no problem with the discs as they work fine on her computer (she asked me to install a fresh copy of XP and it works fine).

I don't know if its a problem relating somehow to Ubuntu/Grub when Windows first crashed, or if it could be a hardware problem.

If anyone can provide any insight to my problem, and help me get Windows 7 back on this computer, it'll be greatly appreciated. I've been going at this for 2 days, and frankly, its stressing me out lol. I don't know how many times I've deleted partitions and reformatted my HDD.

Most likely a memory issue as it was suggested before.
How to test:

Boot from the Ubuntu cd, and in the first menu select memory test. 
Let it do a full pass. You will see if there are problems with the RAM - the errors are reported in red.

PS It seems that Windows 7 is as picky with RAM as Linux. I have seen XP installs running fine and Linux crashing on bad RAM, but Windows 7 crashes just as Linux.

---

