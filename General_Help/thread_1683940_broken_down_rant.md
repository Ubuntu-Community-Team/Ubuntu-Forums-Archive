---
title: "broken down rant"
date: 2011-02-08
forum: General Help
---

### Post by cannuck1964 on 2011-02-08
This is the third time now I have had to reload this system.  I have had one headache after another, first the updates break the bootstrap loader, this is a known issue yet they still continue to release grub updates that effect this and break the boot sequence.  I am very surprised that this is done.

so onto the next issue, they say use a CD to boot from and move the files for grub2 over, well that has been a nightmare taking two days to only find it deleted my initial Linux install, so wasted days, no real back up for the entire system and lost emails etc.

The CDs lock up on boot, they do not load from the CDs and the instructions for fix grub are very lacking.

I would have thought a windoz based solution would have been offered so that this was more easy to do.  This boot from a Live CD does not work and the CD downloads are not working either (using them to load via windoz again, but have lost months of work AGAIN).

If an update is known to break the bootstrap loader, why on earth would you release updates that continuously break it??  

Just ranting as support seems lacking....seems like you are on track to performing like windoz well...

Peter M

I am not impressed in the least given I work in the Open Source Community and havve done so for years..

---

### Post by garyjmellor on 2011-02-08
Hello, what specifically are you having a problem with on the Live CD? I don't quite understand your problem but would like to try and help you if I can.
 
What version of Ubuntu are you trying to install - are you talking about an installation or something else? You mention updates, are these just system updates via Update Manager? Has your system worked and then subsequently got 'broken'. Can you provide more details on the issues you are experiencing?
 
Generally, Community members on the forums are very helpful and I've resolved a lot of issues here.

---

### Post by cannuck1964 on 2011-02-08
I have downloaded the Live Cd from the downloads page, both the 64 and 32 bit systems, the 64, has an error on the load with busybox, and goes not further, the 32 bit system just sits on the ubuntu page and does not load (sits for over 1/2 hr ).

Onwards, I tried to load again via CD, from an older version, great, loaded up (and this deleted my initial install), so all emails, ftp info etc all gone...

I am pretty frustrated as I am new at this, but I would have thought a known issue would have stopped being updated and released in the system until it was fixed.

I have last a lot of work (thank goodness I keep clients files in other places).  This is just poor management in my opinion on this issue (I am not alone in the grub issue, as it is well known).

thanks

---

### Post by garyjmellor on 2011-02-08
[1] OK, so, are you now trying to install a nice, new working system? If so, if I can clarify, [2] you're saying that the downloads page on the Ubuntu site is taking a long time to do the download? Would both of these statements be correct?
 
I totally understand your frustrations as I am a relative newcomer as well but will try to assist you if I can.
 
I think I misunderstood you - you're saying that the load on BusyBox is taking a long time on 32-bit and on 64-bit doesn't work at all - correct?

---

### Post by sydbat on 2011-02-08
Making sweeping, nonsensical statements only prevents us from assisting you.

Knowing what your hardware is, what version of Ubuntu you are trying to install, what other Operating Systems you may have on your computer, etc, etc, etc will help us help you.

So - what kind of computer do you have? HP? Dell? Other?

If you know, what is your CPU, RAM, Graphics card?

Do you have Windows? Which version?

When you installed Ubuntu the first time, how did you do it? Wubi? In it's own partition (dual boot)?

---

### Post by cannuck1964 on 2011-02-08
> [1] OK, so, are you now trying to install a nice, new working system? If  so, if I can clarify, [2] you're saying that the downloads page on the  Ubuntu site is taking a long time to do the download? Would both of  these statements be correct?

I totally understand your frustrations as I am a relative newcomer as well but will try to assist you if I can.
  
 I think I misunderstood you - you're saying that the load on BusyBox is  taking a long time on 32-bit and on 64-bit doesn't work at all -  correct?

I have downloaded both the 32 and 64 bit systems from the downloads page.

the 32 bit system boots onto the ubuntu page and sits there for over 1/2 hrs does nothing.

the 64 bit system, boots and errors out (ie breaks down ) on loading busybox, no idea what that issue is.

 
> Making sweeping, nonsensical statements only prevents us from assisting you.Not really sweeping, Update Manager updates grub2, breaks the dual boot system and is a known issue for montyhs and yet is still released untested and breaking people bootstraps.



> Knowing what your hardware is, what version of Ubuntu you are trying to  install, what other Operating Systems you may have on your computer,  etc, etc, etc will help us help you.

Well I have re-installed the OS already, it deleted my original Linux install, which is why the rant, the Live CD offered solution does not work well and deleted the initial install...




> So - what kind of computer do you have? HP? Dell? Other?Acer 

> If you know, what is your CPU, RAM, Graphics card?Quad Duo processor, 6 Gig Ram, the video card supports generic VGA


> Do you have Windows? Which version?Vista, dual boot system, grub2 broke on an update manager install (even after I redid this a different way to avoid this exact issue over a month ago).

> When you installed Ubuntu the first time, how did you do it? Wubi? In it's own partition (dual boot)?First time yes in its own partition, used the update manager to update from 10.4 to 10.10 broke grub, lost everything, re-installed using wubi and set up a different login method, now another update is released and again grub2 is broken and this time tried the Live CD metyhod and well it just over wrote my install and lost everything again.

Might be that they should not include the grub2 update if it is known to cause issues??

I have since read I can remove it from the updates and lock it in, this in my next step...

---

### Post by Rubi1200 on 2011-02-08
If you are having issues with a Wubi install, please refer to the Wubi Megathread for solutions:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by garyjmellor on 2011-02-08
I've dual booted XP and Ubuntu and had no issues but I have no experience of BusyBox at all.

I always install off the Live CD but not letting it boot to the Live CD desktop - I press escape while it's loading and then select to install Ubuntu. The install then starts and the partition manager lets you install alongside any other detected OS's - in your case, Vista.

I can't say whether BusyBox is your problem as I don't use it. I've had no issues with the bootstrapper becoming broke following an update either. Unfortunately I have also never installed via Wubi.

I don't understand why your installs are freezing or breaking as I've installed 32-bit and 64-bit Ubuntu (Maverick) today into my test environment using the .iso files for the desktop flavour from the Ubuntu homepage. I can only suggest that something in your hardware config is causing the issues or maybe even BusyBox itself(?) - perhaps someone with more experience can help you out in this regard? I'm sorry I've not been of much help so far.

If you can, I would try and download the architecture you need again from the Ubuntu homepage (i.e. grab the correct .iso file again). I would also strongly suggest that after you've downloaded it, you check the MD5Sum for it ([https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)) to ensure nothing went awry during the download.

Next, burn the .iso to disk (CD not DVD) and burn it at the lowest possible speed to minimise burn errors. Set your machine's boot order to boot from the ODD first before the HDD or any other source and then install as I suggested earlier. What you should see when the CD loads during boot time is a darkish screen with two icons at the bottom of it. At this point hit ESC, and select the language of your choice. After selecting your language I'd also do a memory check just to rule out anything screwy here (I might be grasping at straws here but do try it). The memory test can be accessed from the menu you should be looking at after selecting your language. I think, from memory, there are 11 tests it runs through and it just keeps looping through them until you intervene. After memtest has run all the checks and hopefully turned up nothing, exit from it (I can't remember the way to do this but it tells you on screen).

I would now run a check on the CD to check it for defects (as a final catch all - this might all sound like overkill but I've burnt a lot of .iso files and this can be a time saver in the long run). If this comes back all clear, you're good to go. I would then proceed to install Ubuntu - I think it's the second option in the menu. Proceed through the installer to get Ubuntu alongside your Vista install - the partition manager will help you with this.

Follow the rest of the installation instructions and then sit back and wait for it to finish. When you eventually reboot (when it tells you to) grub/grub2 (not sure of the difference... I think it's all grub2 in Ubuntu) should ask you which OS you want to boot into.

If this isn't the solution you're looking for, then I perhaps don't understand the usage of BusyBox and apologise for perhaps wasting your time.

Post back with how you get on if you follow this.

One other word of sage advice: backup, backup and test your backup - this might save you losing work in future. I know it's a bit like shutting the stable door after the horse as bolted but it really is worth doing. I run my system so light that it doesn't warrant a backup - I can live with the loss of everything on it and rebuild it in under an hour from scratch, but not everybody has this luxury. GOOD LUCK.

---

### Post by djeikyb on 2011-02-08
If you boot the livecd, and select install, then yes, of course, it will install and overwrite what you tell it to overwrite. This is why the recommended partition layout has /home, /usr/local, and /var on their own partitions. All your personal files are in /home, all custom installed programs (ie not through apt) go in /usr/local, and logs and web sites are in /var. Incidentally, these are the partitions I back up. I don't have space for or care about bare metal recovery on my system, but I do backup my important files.

During the livecd install, there was a partition layout screen. If you already have a home partition, this is where you let Ubuntu know. Same goes for any other partitions Ubuntu ought to know about. It should only overwrite files on the root partition.

And yes, grub is a pos that barely gets the job done. It's extraordinarily obtuse and difficult to configure, especially on Ubuntu. Grub2 is even worse, from what I hear. Fwiw now, since it seems you've got things borked even more, but what you should have done was use the livecd to boot into your existing system and fixed grub (possibly by downgrading from grub2). I don't believe a reinstall was necessary.

At the end here, my questions are:
(1) Do/did you have /home on a separate partition? 
(2) Can you mount that partition, and verify data loss?
(3) Did you tell the installer to use a partition that was not /home?

If the answer to all three of these questions is yes, we probably have a reportable bug.

---

