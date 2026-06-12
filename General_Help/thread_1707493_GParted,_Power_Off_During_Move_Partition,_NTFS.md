---
title: "GParted, Power Off During Move Partition, NTFS"
date: 2011-03-15
forum: General Help
---

### Post by axlekitty on 2011-03-15
OMG I'm hoping someone can help me, I almost fainted.

Hard drive looks like this:
| [sda 5 Media] | Unalocated | NTFS C: Windows 7 |

While moving NTFS partition over to the end of Media partition My wonderdfull toddler decided to power off my power-strip. I'm maybe hoping to just use a command to tell Ubuntu that the whole space between "Unalocated" and the end of the NTFS is one NTFS partition thus recovering 99% of the remaining data. Most of the data is irreplacable so I'd like to save it. I don't know how to achieve this so I need some help please.

now it looks like:
| [sda 5 Media] |      Unknown      |

---

### Post by dragonfly41 on 2011-03-15
[SIZE=2]I'm very new to Ubuntu myself (recovering crashed data from Vista OS and moving over to Ubuntu) and there may be some magic someone else in the forum can advise you on.

But if not and your data is critical then I would look at testdisk

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

[/SIZE][SIZE=2]http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/[/SIZE]
  [SIZE=2]
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)[/SIZE]

[SIZE=2]Worst case (if there is no magic Ubuntu command) you might end up having to remove the hard disk (if corrupted) and view it as external disk in a USB container connected as slave to another windows laptop to try to recover your data.  
[/SIZE]
[SIZE=2]In such cases I've used testdisk (free) and also a program RecoverMyFiles ([www.getdata.com]("http://www.getdata.com")) which runs on Windows.


p.s. read this advice from last of the links above

[/SIZE]**CAUTION**

 You  should NOT write to the failed device, as it can worsen a hardware  failure, and overwrite existant data in case of lost files.   
Shut down the affected machine as soon as possible, and restart it from a [LiveCD]("https://help.ubuntu.com/community/LiveCD") or [LiveUSB]("https://help.ubuntu.com/community/LiveUSB").  Be certain that the "live" cd does not automatically mount any partition or swap space.

**Lost Partition**

 If  you made a mistake while partitioning and the partition no longer  appears in the partition table, so long as you have not written data in  that space, all your data is still there.


=====================================================================
[COLOR=Red]
postscript ..

post your question to this thread to see if FixParts will help ..

[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325)[/COLOR]

---

### Post by axlekitty on 2011-03-16
i think it's a lost partition, however I am not trying to offend you when I say I'd prefer to do this in linux instead of using a third party program and screwing up my drive more than it is. I am aware that if I try to write to it I will be overwriting data, I've only been on live cd until I can clear this up. I read somewhere (but am completely unsure how to do this) that I can use a program and command in linux to tell the HD the "Unknown Partition" is a different "type" or something like that.

the unalocated space and the windows NTFS partition ended up gone when I tried to move the NTFS Left to the beginning of the unalocated. I just want to tell ubu that it's one giant NTFS if that makes sense so I can recover what it was also attempting to copy over when it got shut off.

---

### Post by srs5694 on 2011-03-16
First, I'm the author of FixParts, and I can guarantee you that it will *not* be helpful in solving your problem, so don't waste your time trying it. (It's intended to solve other problems, just not yours.)

My first and ***most important*** piece of advice: Go buy a new hard disk that's as large as or larger than your current drive and do a byte-level copy of the current disk to the new one. (If you get a disk that's twice as large, you'll have some extra options, as described below.) You can do this by booting a Linux emergency CD (Ubuntu in "try it now" mode or a disc like [PartedMagic](http://partedmagic.com/) or [System Rescue CD](http://www.sysresccd.org/)) and issuing a command like the following:

```

sudo dd if=/dev/sdx of=/dev/sdy

```

You must be ***absolutely positive*** that you've got the /dev/sdx and /dev/sdy parameters right, though. The if= option must point to your *current* disk, and the of= option must point to your backup disk. Depending on the type of drive you get and how you install it, your current disk could become /dev/sda or /dev/sdb (or conceivably even /dev/hda or something else), so you should verify which is which by using GParted, fdisk, or some other tool to view the current partitions. If you get this wrong, you'll "back up" the new disk to the old one, making it 100% impossible to recover anything, so don't rush things, quadruple-check that dd command before you hit the Enter key, and if you have any doubts, get more help. Once you begin the dd command, it will take a while to run -- you may need to leave it running for several hours, during which time it will display no output.

This may sound like a lot of scary caveats for something I say you should do, and you're right; but the reason you should do this is that many possible methods of recovery are potentially destructive, so you want to have a low-level backup of your disk in case you make matters worse.

With the backup in hand, you can begin experimenting. Unfortunately, the probability is very high that you won't be able to recover your whole filesystem in one piece. You might, though, luck out with TestDisk, perhaps followed by Windows' NTFS repair utilities from an emergency Windows boot disc. If you don't have a Windows recovery disc, check [here](http://neosmart.net/blog/2009/windows-7-system-repair-discs/) for Windows 7 discs. (Even if you don't normally run Windows 7, those discs should at least be able to check the filesystem.)

If that fails, you could try [PhotoRec,](http://www.cgsecurity.org/wiki/PhotoRec) which can recover individual files. This is where having a backup disk that's twice as big can be handy; you can create a partition on the backup disk that begins after the point where the first disk would end (so that it doesn't overlap the backed-up data), then use it as a dumping ground for the files PhotoRec recovers. Unfortunately, you're likely to lose filenames if you use PhotoRec, so you could end up spending a lot of time examining individual files and renaming them. I've heard there are similar Windows recovery tools that can recover filenames, but I don't know much about them. You could look into that possibility, though.

If and when you recover your data, you can put one of your disks in an external enclosure (if you don't buy an external to begin with) and use it as a backup disk, which will help you recover from such disasters in the future.

---

### Post by dragonfly41 on 2011-03-16
[SIZE=2]Although I'm new to Ubuntu and Linux and feeling my way, in my time I've been through quite a number of crashed (Windows) disks .. I've got one right now to sort out.  

This is why I'm trying Ubuntu.

The golden rule I've followed is don't try to recover failed disks on the same machine since more likely than not you will do more damage and stand the risk of overwriting some of the files.

So if you can remove your drive and place it in an external enclosure .. USB is handy .. you can plug into another working PC and forensically analyse the data on the failed drive.

I've successfully used both TestDisk and RecoverMyFiles (which you can start in free demo mode to see if your files can be recovered).

[/SIZE]

---

### Post by srs5694 on 2011-03-16
> **dragonfly41 said:**
> [SIZE=2]The golden rule I've followed is don't try to recover failed disks on the same machine since more likely than not you will do more damage and stand the risk of overwriting some of the files.[/SIZE]

I'd have to disagree with this advice, or at least rephrase it significantly.

Recovering data from one partition to the same partition (via tools like PhotoRec) can be dangerous. Recovering data from one partition to another partition is much safer, and if a disk has no free space or most of its area is damaged, the only way to do this may be to use a second physical disk as a target for recovery.

Filesystem repair tools (such as Linux's fsck or Windows' CHKDSK) can sometimes do more damage than they fix. Thus, backing up from one disk or partition to another before running these tools on a badly damaged partition is a wise precaution. If the damaged partition is large, such a backup may require a second physical disk.

These dangers, however, apply to *disks*, not to *computers*. It's irrelevant whether the disk is attached to the computer or motherboard it normally uses or to another one. Thus, moving the disk to a new computer doesn't help with safety, and in some cases can make things considerably less safe. (For instance, if you're unused to working inside a computer, you could neglect certain precautions and physically destroy the disk by giving it an electrostatic discharge or by damaging its connecting pins.)

All of this also assumes that you're not trying to boot using the OS on the disk you're trying to repair. In a dual-boot configuration (including the one under discussion), it's sometimes possible to get away with this by booting an undamaged OS and using it to repair a damaged OS on the same disk. Trying to use an OS on a damaged partition to repair that very same partition can lead to significant problems, though, and I suspect that's the issue that's led you to think you must move a disk to a new computer. In a Windows/Windows situation, a second computer will give you a full Windows installation to use to repair a damaged one. If you've got some other way of booting, though, such as a USB-bootable installation or an emergency repair CD/DVD, you can use it to avoid touching the damaged disk except with your low-level copying and repair tools. That's precisely what I advised axlekitty to do (among other things).

---

### Post by dragonfly41 on 2011-03-17
As a Ubuntu newbie I must defer to the wiser advice of srs5694.   

My own caution arises from a situation where for example I have a crashed Vista OS on my Dell Inspiron laptop partition and I have installed Ubuntu (demo mode only) in Vista safe mode to allow me to access the file system and copy windows files to a USB drive.

There are risks that removing the disk to be slaved and recovered might actually cause more damage than *in situ* repair and also with this approach you will need another working computer and recovery software.   It is a balance of risks and costs.

---

### Post by srs5694 on 2011-03-17
> **dragonfly41 said:**
> My own caution arises from a situation where for example I have a crashed Vista OS on my Dell Inspiron laptop partition and I have installed Ubuntu (demo mode only) in Vista safe mode to allow me to access the file system and copy windows files to a USB drive.

The way you phrased this makes me think that you did a WUBI install of Ubuntu. WUBI is a way to install Ubuntu in a file that resides on a Windows partition rather than in a partition of its own, so there's no real difference between what you did and installing a very big Windows program, in terms of its effect on the filesystem.

If you'd used a Linux live CD, you wouldn't have had to write to the Windows partition at all, at least for certain types of recovery (such as PhotoRec or doing a low-level backup and then working on the backup).

---

### Post by dragonfly41 on 2011-03-17
> "If you'd used a Linux live CD, you wouldn't have had to write to the Windows partition at all, at least for certain types of recovery (such as PhotoRec or doing a low-level backup and then working on the backup)."Oh that it was that easy!   Are you sitting comfortably to hear my story?

Pre-Ubuntu .. in Vista land after it crashed I found myself in a position where my internal CR-RW device (Dell Inspiron) would not work (could not burn a Vista recovery disk) and I could only boot up in safe mode plus networking.   It was at that moment (with Vista safe mode and Internet access only) that I decided to take the plunge and try Ubuntu Windows Installer which installed Ubuntu in c:\Ubuntu.

I could then boot into either Vista safe mode or Ubuntu.

I realised that I had to stay in Ubuntu demo mode (quickly press Esc after booting into Ubuntu and choose Demo mode) to use Ubuntu (I guess you could say in "safe mode") and I found that I could access my Windows files to then backup to USB drive.   

I slipped up once by starting Ubuntu full installation (clicked on inviting Install Ubuntu 10.10 icon on desktop) and after a few seconds I powered down when I realised this full installation might wipe the partition.   But some files must have been overwritten (probably MBR) after a few seconds of installation since I could not longer get into Vista safe mode.   

There should be a health warning on the wubi approach.   However my main files seemed to be preserved and I quickly backed them up to USB drive.

Since my internal CD-RW device still refused to recognise inserted media I found that a purchased CD-RW device attached via USB port was also seen by Ubuntu but inserted disks were not seen.  Neither of the two devices could recognise inserted disks.  they could be seen with different commands.   wodim --devices.

It took me some time to learn that this external CD-RW device was not working to spec because I had it plugged into an unpowered USB port expander (using two ports, one for data the other for power).   These CD-RW devices are apparently power supply sensitive.

When I changed to plugging in directly to two USB ports on my laptop the external device could then recognise disks and I could begin to make progress by burning CD disks (including a Live CD and LiveUSB for future usage).  Since Vista was now dead I had Ubuntu as my lifeline.

I've now got burned copies of LiveCD, LiveUSB, my Windows files, Vista Recovery Disk and anything else I can think of.  

So yes if I had a LiveCD I would have taken that road.   But with no CD-RW device working at the time I had to try the wubi route.

The point is you can't plan ahead for such situations.  Just try to use your wits to get out of tight corners.

---

