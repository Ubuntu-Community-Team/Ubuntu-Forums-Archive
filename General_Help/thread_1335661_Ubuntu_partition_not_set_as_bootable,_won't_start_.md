---
title: "Ubuntu partition not set as bootable, won't start GRUB"
date: 2009-11-23
forum: General Help
---

### Post by racer13fly on 2009-11-23
Alright, so here's the problem: Whenever I boot, I get an error from GRUB about there being no partition and it shows the GRUB rescue text area.
Here's the what I believed caused it: I had 3 OSs, 2x of Ubuntu 9.10 and 1x of XP.  I installed the 2nd Ubuntu for trying something out that I felt would mess up my primary Ubuntu setup.  After I did that little experiment, I formatted the partition it was on and I tried putting it on the primary Ubuntu partition, but I couldn't quite figure it out, lol.  So the 2nd partition of Ubuntu was formatted and the primary and XP are fine.
What happened leading up to now: So then I go to bed and now I get on today to find the error I mentioned earlier.  I quickly get out my trusty LiveCD and boot that up so I can look around for help, like I am now.
I think the problem is that somehow the primary partition somehow had it's 'Bootable' checkbox unchecked, which is what I believe is the problem (which you can see from the 1st 2 pictures).  But whenever I try to check that mark so I can try rebooting, I get this error: ```
Error modifying partition: helper exited with exit code 1: In part_change_partition: device_file=/dev/sda, start=190555094016, new_start=190555094016, new_size=8463780864, type=0x83
Entering MS-DOS parser (offset=0, size=200049647616)
MSDOS_MAGIC found
looking at part 0 (offset 32256, size 7649478144, type 0x0b)
new part entry
looking at part 1 (offset 7649510400, size 174894128640, type 0x07)
new part entry
looking at part 2 (offset 182543639040, size 8003197440, type 0x05)
Entering MS-DOS extended parser (offset=182543639040, size=8003197440)
readfrom = 182543639040
No MSDOS_MAGIC found
Exiting MS-DOS extended parser
looking at part 3 (offset 190546836480, size 9500198400, type 0x05)
Entering MS-DOS extended parser (offset=190546836480, size=9500198400)
readfrom = 190546836480
MSDOS_MAGIC found
readfrom = 190555061760
MSDOS_MAGIC found
readfrom = 199018874880
MSDOS_MAGIC found
Exiting MS-DOS extended parser
Exiting MS-DOS parser
MSDOS partition table detected
containing partition table scheme = 1
got it
Error: Invalid partition table on /dev/sda -- wrong signature 0.
ped_disk_new() failed
```So far from what I can see is that if I'd try installing Ubuntu again, I'd have to wipe my HD, which is not a good option for me.
So that's all I can say at this time and hopefully I can get some help on this issue.  If you need anymore details just ask.
Thanks guys!

(UBUNTU #1!!!:KS)

---

### Post by coffeecat on 2009-11-23
I'm having difficulty following you, but two comments.

First, if you mean the boot flag when you say 'bootable checkbox', ignore that for Linux. The boot flag is only needed for Windows. Linux doesn't need it. So I doubt that has anything to do with your problem.

The second is more serious. This does not look good:

> Error: Invalid partition table on /dev/sda -- wrong signature 0.
ped_disk_new() failedBoot up with your live CD, open a terminal and post the output of:

```
sudo fdisk -l
```Then we can see what, if anything, is showing up for your partition structure. If you have any important data on that HD that you want rescued, don't try to boot up from the HD. You need to keep writes to it to a minimum - preferably non-existent - until you've determined the extent of any damage.

**Edit:** by the way, you won't get any more out of me today. It's late here in the UK and I'm going to log off in a minute.

---

### Post by racer13fly on 2009-11-23
Here's what I got: ```
Ignoring extra extended partition 4
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         930     7470193+   b  W95 FAT32
/dev/sda2   *         931       22193   170795047+   7  HPFS/NTFS
/dev/sda3           22194       23166     7815622+   5  Extended
/dev/sda4           23167       24321     9277537+   5  Extended
```I'm not sure what it means, but it doesn't look too good to me, so idk.
Thanks.
And I think I forgot to post those pictures I mentioned, would you still like to see them?

---

### Post by coffeecat on 2009-11-24
The big problem I see is that you've got two extended partitions. That is not allowed. I don't understand how that could have happened. Brief explanation: the maximum allowed number of primary partitions is 4. To obtain more than four partitions, you can have one, but one only, extended partition. An extended partition is simply a "container" for a number of logical partitions.

Your Ubuntu root partition would have been a logical one, but as this is not showing in your fdisk output, you must consider this lost. It may be that there has been a simple corruption of the partition table, which has led to two logicals inside one extended being seen as two extendeds. In which case it would be recoverable by editing the partition table. But that's a job for an expert - it's beyond me. What I'm hoping is that if you delete the two extended partitions and re-install Ubuntu, all your problems will go away. But no guarantees.

The two extendeds and the borked Ubuntu partition explains your inability to boot up both Ubuntu and Windows. Quick explanation: grub stage 1 is on the mbr which calls stage 1.5 which is just after the partition table. That, in turn, calls grub stage 2 which is in your Ubuntu root partition - as is the grub configuration menu. No stage 2 or menu = no bootup.

Solution. This following may not be the best but this is what I would do if I was in your position:

Boot up with the live CD, go to System > Adminstration > Gparted and delete sda3 and sda4. Now run "sudo fdisk -l" again. Does it give any warnings about the partition table? If yes, then stop now, post the new fdisk output and we'll see what's what. If no, you are probably safe to proceed with a re-installation and choose 'install in continuous free space' (or whatever it says) at the partitioning stage. If the install is successful, then grub will be reinstalled and you should be able to boot into Windows again.

Caveat - do you have any CD/DVDs to reinstall Windows? sda1 looks as though it may be some sort of recovery partition, but it's always possible that any editing of partitions can go wrong, leaving you with no sda1, no sda2 and no Windows. Have a think about that.

---

### Post by QLee on 2009-11-24
[QUOTE=coffeecat]The big problem I see is that you've got two extended partitions. That is not allowed. I don't understand how that could have happened. [/QUOTE]

Probably tried to make the change, never did the "write". That would be my guess.

This was the error message from fdisk. "Ignoring extra extended partition 4 Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)"

---

### Post by racer13fly on 2009-11-24
Alright, I'll do that once I get home today.  But what about the partition with XP?  Will that be fine?  I'm able to still access it in the LiveCD and view the files, so if I can't save the XP at least I can back up all the files to a disc or stick.
And also, I've had this problem since I installed Ubuntu, but whenever I tried booting XP from GRUB when I booted, it just started the Compaq Recovery Tool, which I don't see why it's doing that, nothing is wrong with the files.  Can anyone advise on this issue?

---

### Post by Darael on 2009-11-24
I suggest using testdisk (boot a live cd and install it from the repos) - it can usually recover a borked partition table.  I know it worked for me when I screwed up mine!

---

### Post by coffeecat on 2009-11-24
> **racer13fly said:**
> whenever I tried booting XP from GRUB when I booted, it just started the Compaq Recovery Tool, which I don't see why it's doing that, nothing is wrong with the files.  Can anyone advise on this issue?

That was because your Windows grub menu entry was pointing to sda1 and not sda2. The grub installer *should* have set you up with 2 entries - one for sda1 and one for sda2. But sometimes it gets confused. If, after you have re-installed, you still only get one entry for Windows and it boots you into the recovery partitition, just post back and we'll soon get you sorted out.

You might want to download [SuperGrubDisk]("http://www.supergrubdisk.org/"), burn it to CD and keep it in your toolbox. You can use it to boot into Windows (or any OS on the hard disc) but be careful - one of the menu options on it is to repair the Windows mbr and then boot into Windows. Which means you wouldn't then be able to boot into Ubuntu and you'd have to repair grub.

---

### Post by racer13fly on 2009-11-24
And I'm also having this issue with GParted, I don't know if it's because it's booted oin the LiveCD or not, but it shows as if I have no partition, as it's all free space.  Here's a screenshot:[IMG]http://i.imagehost.org/0616/Screenshot.png[/IMG]

I'm thinking I should use the disk utility instead?

EDIT: And it's alright if I wipe my Linux partition, I  have barely anything on it now anyway.  Nothing important, I'll just move the few documents to the XP partition for now.  But the XP I'm worried if I wipe, even if I can get XP back on.
And yes, the 1st partition is a separate recovery HDD for XP.  Idk why it's saying it's part of the whole HDD when it's not, in XP it read as it being a separate HDD.

---

### Post by coffeecat on 2009-11-24
That doesn't look good. Presumably the partition table errors that fdisk reported is making Gparted think the whole disk is unallocated. You'd best bail out there and not try to make any changes. Darael's suggestion of using testdisk to repair the partition table might be the way to go, but I'd better step back now. I've not used testdisk for this, so I can't advise.

---

### Post by racer13fly on 2009-11-24
Well then I guess I had better learn up on testdisk or find someone who could help me. Or could I try the LiveCD version of GParted?  I used it once before and I still have and I guess I could try that.

---

### Post by racer13fly on 2009-11-24
Well I just got into TestDisk and it seems I can't quite use it while on the LiveCD because all it views is the disc drive, so I'll try making a LiveCD out of the .ISO available.

---

### Post by racer13fly on 2009-11-25
Well I just got a thing called Part Magic, 1 of those things you boot up in a LiveCD, and it has TestDisk on it, and TestDisk was working right.  So I quickly got on it and deleted the Linux stuff, leaving the NTFS and FAT of course, giving the XP a primary bootable setting and the FAT set itself to primary.  Then rebooted and now things are fine.
I just did the code requested earlier in the terminal and here's what I have now: ```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         930     7470193+   b  W95 FAT32
/dev/sda2   *         931       22193   170795047+   7  HPFS/NTFS
```I'll proceed with Ubuntu installation, and I'll let you know if XP boots up, too.
Thanks for the TestDisk suggestion!

---

