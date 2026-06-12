---
title: "GRUB loads only after ~3min of flashing white cursor"
date: 2009-08-09
forum: General Help
---

### Post by adempewolff on 2009-08-09
I'm having an issue where on boot, I get a flashing white cursor for about 3 minutes before the GRUB bootloader finally shows up  (at first I thought it was just gone until I went across the room to write this and heard Ubuntu boot after 3 minutes!).  Here is possibly relevant information:

I just recently got a new hard drive and installed Windows XP, Vista 64, and Ubuntu 9.04 amd64.  Ubuntu is my main OS so after installing XP and Vista I installed Ubuntu and have been using it except maybe booting into Vista once.  Last night I booted into XP for the first time to run chkdsk on an NTFS partition.  To boot into XP I first need to choose the Vista bootloader from the GRUB menu and then I choose "previous version of windows" (if anyone knew how to safely have grub point directly to each OS that would be groovy).  So after running chkdsk in XP I restarted into Ubuntu and then suspended it (to RAM) overnight.

In the morning I woke it from suspend only to find a flashing white cursor, not surprised by the occasional bug from a resume I pressed ctrl-alt-F1 and was able to login.  I then went to start gnome which it said started but it must have been a different session or something so I then tried restarting gnome which worked and I was able to log in to the GUI.

I then restarted after a little while with the intent of migrating back over to XP for another chkdsk.  Upon restart I got the flashing white cursor and GRUB did not show up.  I tried ctrl-alt-F1 (for the heck of it, I ws pretty certain linux hadn't booted) to no avail then manualled powered the computer down and restarted.  This time the BIOS did an extended bootup (probably because I forced the power off) and then I got the same white cursor.  However when I left it to write this post I heard Ubuntu prompt for a login some time later.  I went back over and logged in then restarted to another white cursor (BIOS loaded fast this time) and left it for approximately 2-3min before the GRUB bootloader finally showed up.

I don't know if booting into XP actually had anything to do with this but it seems awfully suspicious as it only happened after I first booted into it after installing ubuntu.

Another possible culprit is that in my partition tables the Vista partition has a "boot" flag.  I didn't want to remove it because GRUB seemed to be working fine from the MBR with it and I didn't know if removing it would mess up Vista or it's bootloader.


Any suggestions on what to do?  I think I'd like to just do a fresh install of GRUB but I don't really know enough about how it deals with Windows OS's to feel safe doing it manually.

Any advice is always appreciated!

---

### Post by Barafu Albino Cheetah on 2009-08-09
I had the same thing, but it waited for 20seconds only. It disappeared when I installed kubuntu skin for Grub. You should try it.

---

### Post by Post Monkeh on 2009-08-09
do you have a cd in your drive?


either way, first thing i'd try is checking your boot device settings in your bios, and make sure your ubuntu disk is first on the list.

if it is, it's possible the delay is your pc scanning your partitions to see which is the most suitable to boot from.

---

### Post by adempewolff on 2009-08-09
> **Post Monkeh said:**
> do you have a cd in your drive?


either way, first thing i'd try is checking your boot device settings in your bios, and make sure your ubuntu disk is first on the list.

if it is, it's possible the delay is your pc scanning your partitions to see which is the most suitable to boot from.

no cd in the drive (and I know for a fact the internal hdd is above the cd drive in my bios).  although the two most recent times I restarted the first time I waited at least 5 minutes for nothing. so I put a livecd in the cd-drive resigned to have to reinstall GRUB and restarted but for some reason I let it boot from the hdd one more time and grub popped right up.

I don't really want to restart again yet because I have work to do and can't afford to wait 5 minutes every time I want to restart my computer or switch OSes.  I wonder if there is a way to make GRUB dump log files...

I thought the same thing about it scanning the partitions, but it does finally boot to GRUB so it must be loading from the MBR.  I think I'm going to have to reinstall GRUB, I just need to do some reading on how Windows OSes boot so I don't mess them up.  Right now it looks like Vista put a bootloader in the XP partition (sda2, or hd0,1) so GRUB points to that to load either Windows OS.  So I need to figure out how to delete that and make sure both Vista and XP are both bootable from their own partitions then make GRUB chainload to them.  If anyone has any advice on this it would be much appreciated.  Right now I think the MS-DOS "fixboot" command from a windows recovery console is my best bet but I'm not entirely sure how it works... Google here I come!

---

### Post by Post Monkeh on 2009-08-09
i would try reinstalling grub. it shouldn't affect your windows setup at all, in fact it shouldn't even need to be set up 
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

that's a good guide.

providing grub was originally pointing tovista properly, you won't need to edit any settings, just follow the guide to reinstall grub.

the reason i asked about the cd was that when i have a cd (unbootable) in my drive, if i'm set to boot from cd first, then the pc will scan the cd, taking up a few seconds, before deciding it needs to go to my hard disk.

it sounds like in your case, the pc was scanning all your partitions to find which one to boot from.  i may be wrong on that though.

it certainly won't do any harm to reinstall grub.

i wouldn't bother with fixboot. it will remove grub altogether, meaning you'll HAVE to reinstall it.

the problem is with grub, or your general boot setup - if it was with the windows booting system, then grub would still load and your problems would only occur when booting into windows.

---

