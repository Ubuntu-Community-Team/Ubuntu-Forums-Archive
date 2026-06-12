---
title: "How do I triple boot Windows 7, Ubuntu and Moblin?"
date: 2010-01-05
forum: General Help
---

### Post by Vignesh S on 2010-01-05
Right, I have an ambitious plan. I want to triple boot Windows 7, Ubuntu and Moblin/whatever other fast booting OS I come across. At the moment, I've got Windows 7 and Ubuntu there. I can make free space for Moblin, but how would I configure GRUB 2 so it reads it too?

Moblin does have a GRUB, but I'm presuming that its the legacy version, not GRUB 2. How would I get the Ubuntu GRUB back as the main bootloader if that were the case? 

This is just planning, there will probably be more question springing to mind later on.

---

### Post by synapsys on 2010-01-05
If grub legacy can boot moblin, then I'm sure grub 2 can boot moblin. If grub doesn't pick it up automatically, you can always write a custom entry for it. 

If anything overwrites your MBR with something other than grub, you can boot to a live cd and reinstall grub from there. 

more here:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Vignesh S on 2010-01-05
errr.... what's an MBR?

I'm testing dual-booting Ubuntu and Moblin and seeing how that goes...

---

### Post by wilee-nilee on 2010-01-05
It doesn't hurt to know more,
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

### Post by Vignesh S on 2010-01-05
lol, Wikipedia, the solution to everything :-P

Thanks for that, though yes, Moblin didn't work on my test machine because its too old :?. So there is no way to test it unless I put it on a "functional" computer, and that is VERY risky. The last thing I need is not being able to access Ubuntu, though yes, it is easily solveable. Well, here goes nothing, I'm putting it on my Desktop, seeing that I can use my laptop if anything stuffs up. Besides, I can always put Ubuntu on there again in case anything goes wrong and sort things out from there.

---

### Post by cenzorrll on 2010-01-05
hmm, i like ambitious plans.  i would suggest redoing your partition layout.  it'll make it easier for your ambitious self, especially since of done this many times (went as far as a quad boot, then realized i never used more than three at a time)

i had (250gb hard drive):

partition 1 primary: 512mb /boot 
(i only mounted this in the ubuntu setup, all other /boot was in the root for each OS)

partition 2 primary: 100Gb windows

partition 3 primary: 10gb ubuntu /
(i didn't put this in the extended so i wouldn't confuse it with the other OS's)

then in an extended partition:
10gb each for each linux os
at the end a 3.5 gb swap (used for all my OS's, i rarely hibernate)
and the rest was /home for my ubuntu partition

this let me play around with the other OS's without having to worry about ubuntu or windows (probably overkill, but i've screwed up A LOT when messing with linuxes, i like everything to be separate)

edit: if your computer is beastly enough i would also suggest using virtualbox, that way you can at least see what it's like if there's no livecd before installing

---

### Post by Vignesh S on 2010-01-05
Well, seeing that my mind won't rest until this is done, I'm designating the whole of tomorrow as a "computer day", in which I go ahead without worrying about my holiday homework.

As a last minute solution, I decided to dual-boot Ubuntu and Moblin in the same VM, and thank god I did, because it didn't even come up with GRUB! :? Now that is a serious problem, and there is no way I'm going to take that crap. I'm going to reinstall Ubuntu in it and I'll see if it registers Moblin or not. If it doesn't, then this doesn't look good

Yeah, I think it would be lot easier to reformat the whole computer from scratch, especially since Moblin stuffed up some of the partitions on the computer to begin with, though it still works. Its going to be a long day, but I think I'm up for the challenge.

---

### Post by Vignesh S on 2010-01-05
Right, I've got some good news and bad news.

Good news is that GRUB 2 in Ubuntu actually registers Moblin. Bad news is that it comes up with the error outlined in the screenshot. Now, that could easily be a virtualisation error, seeing that I used a virtually dynamic image which expands/contracts depending on how much storage space is in there at that time. But if that happens for real, then that's a real worry :?. Well, at least Ubuntu registers Moblin's existence :-P. 

Oh and I've just realised: I can't even use ethernet on my laptop because the kernel version in Moblin doesn't have the required ethernet driver! That sucks :-(. 

I'm beginning to wander if installing an Ubuntu base and installing the moblin clutter interface (seeing that its in the repositories) would be a safer bet until the next version of Moblin comes around... and there's the fact that Ubuntu is aiming at a 10 second boot time for Lucid (nowhere near the 5 seconds Moblin can go at, still, that's well within my range of a fast booting OS)...

EDIT: found out that I'm not the only one with the below problems [http://ubuntuforums.org/showthread.php?p=7563297](http://ubuntuforums.org/showthread.php?p=7563297) but that's for GRUB, not GRUB2. That's the problem with sticking with the latest and the greatest: stuff sometimes doesn't always work

---

### Post by Vignesh S on 2010-01-05
Right, I've decided that I want Moblin, and I'd like to know how to recover the GRUB2 in Ubuntu 9.10 after I've installed Moblin. I know I'll be able to access Windows, but how do I get the Ubuntu GRUB2 back?

---

### Post by Leppie on 2010-01-05
to reinstall grub2 with the karmic livecd:
```
$sudo mount /dev/sdXY /mnt
$sudo mount /dev/sdXZ /mnt/boot  ##only if you have a seperate /boot partition which could of course be on another drive as well
$sudo grub-install --recheck --root-directory=/mnt /dev/sda
```

---

### Post by Vignesh S on 2010-01-05
Thanks for that, Leppie. Now all I need to do is recover any important files in Windows, and I'll be on my way :-D

---

### Post by Vignesh S on 2010-01-05
Well, partitioning didn't work. The Moblin installer crashed, though I could still access my GRUB2. So next step, going to install it on SD card. Bad move. Ubuntu isn't detected, and Moblin decided to kernel-panic on me and I'm going in Ubuntu 9.10 LiveUSB so I can recover the GRUB2. Well, I think it kernel-panicked because I didn't allocate any swap space for it, but I'm going to give it another crack..

EDIT: YAY, that GRUB2 recovery works like magic! Now I can try reinstalling Moblin now that I know how to fix it up

EDIT (again): Unfortunately, allocating swap space crashed the installer (again). I don't think this is quite going to work.

---

### Post by Vignesh S on 2010-01-06
YESS! I got Moblin onto my HDD. But I have no idea how to configure GRUB2 so that it shows up on the boot list at start up.

---

### Post by Leppie on 2010-01-06
doesn't moblin use grub2 as well?

---

### Post by Vignesh S on 2010-01-06
Alright, I got the screenshot of /boot/grub on the Moblin partition, and it looks like GRUB legacy to me.

After doing a sudo update-grub, Moblin came onto the GRUB 2 menu list at boot up, but it wouldn't load. It came up with the same error that befell Moblin in my virtual machine earlier on. How on Earth do I change the settings so that it boots up Moblin? I think it has something to do with configuring the /boot/intrid and the kernel of Moblin at boot up, but I'm not sure, seeing that this isn't my area of expertise :-)

If that's not possible, then my only chance is to reinstall Moblin (not a problem) and configure its GRUB so that it reads Ubuntu and Windows 7 as well as the recovery partition for Windows.

EDIT: Yes, confirmed, Moblin uses legacy GRUB. I saw GRUB 0.97 on the top of the GRUB menu

---

