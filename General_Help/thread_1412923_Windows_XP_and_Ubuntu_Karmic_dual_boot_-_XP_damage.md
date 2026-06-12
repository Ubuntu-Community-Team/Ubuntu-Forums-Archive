---
title: "Windows XP and Ubuntu Karmic dual boot - XP damaged"
date: 2010-02-21
forum: General Help
---

### Post by Capt. Trouserblast on 2010-02-21
Hi I wonder if anybody could help me with this...

I have Windows XP and Ubuntu Karmic installed as a dual boot (XP was installed first) and everything has worked wonderfully until now.

Something...I am not sure what it was...has damaged the XP install so that now, when I select XP in GRUB, XP does boot, loads for for maybe a few seconds and then (still in the middle of the XP slpash screen and the scrolling bar) I get a quick blue-screen and the system restarts. Ubuntu, as ever, is working perfectly.

I can mount and access the XP partition in Ubuntu and as far as I can see from a superficial level everything is still present and correct. 

I have attempted to recover XP using my XP disc...but when I select to install Windows XP (bypassing the recovery console option) and then want to select my partition for repair...XP installation can't recognize its own partition...*everything* reads as unknown even when I select the partition that I know to be XP. There is no option to 'repair' on any of the partitions visible.

I imagine that the fault lies somewhere within the XP system files and re-writing them will sort it out...but is it possible to recover XP in this state?

I'd be very grateful for any help that anybody could offer on this one...I imagine it's quite simple but has me stumped!

Thankyou!

---

### Post by byStanderone on 2010-02-21
...is it by any chance that you have your xp partition in ntfs format?
you'd have to install ntfsprog in karmic for proper access of ntfs.

---

### Post by mr clark25 on 2010-02-21
if you think you need to re-install XP, you can use ubuntu to back up all of your data, re-install XP, recover grub, and put all of your backed up files back.

---

### Post by Capt. Trouserblast on 2010-02-21
Thankyou for your replies but not quite what I need I think...I can access the (ntfs) XP partition without any problems from within Ubuntu as I have already set that up. My problem is getting XP to load after booting. I really would rather not re-install everything from scratch as I'm sure there must be a better fix than that!

Any other ideas anybody?

---

### Post by davey98 on 2010-02-21
Press and hold down F8 at startup to get the advanced menu, select
"disable automatic restart on system failure" then you will be able to read the info.

---

### Post by Capt. Trouserblast on 2010-02-22
@ davey98 Thankyou...unfortunately that didn't help but I didn't know how to get to the advanced mode during boot by pressing F8 so you have taught me something new there! :D

I'm marking this as solved because...I have solved it myself!

In case (although unlikely) anybody else has this problem...in this case the bootloader (GRUB) was set up just fine, all values and everything perfect.

The issue was with the XP boot process *after* it had been initiated by GRUB because GRUB knew where XP was and loaded the first few files. When I ran it from the Windows install disc, the XP install couldn't recognize its own system files on the partition to repair...therefore the problem must be a corruption within XP system files, not GRUB.

I dug out my XP disk (reluctantly) loaded recovery console and executed chkdsk...which checked the Windows file system for errors...found some and repaired them. Rebooted the system and XP loaded fine. XP install now recognizes XP Home Edition on the disk as well.

Thankyou to everybody who tried to help! All is well now until I next break it! :D

---

