---
title: "First Time Linux User...little help with Hard Drive Recognition needed..."
date: 2009-08-05
forum: General Help
---

### Post by imasterxx on 2009-08-05
Ok, so this is the first time I've been gung-ho about Linux.  In the past, I haven't had the warm and fuzzy feeling when it came to linux supporting my legacy hardware, but now after trying Ubuntu I'm pretty comfortable... comfortable enough to make a 15GB dual boot partition to play around in until I decide whether to convert 100% to linux...

keep in mind that I've been using Windows since 3.1, so getting use to all the binaries/packages/mounting/etc.. is still fairly new to me...

So to my question.  I have 4 hard drives:

160GB- Dual Boot - 145GB = Windows NTFS Main Drive & 15GB Ubuntu partition
200GB- IDE Hard Drive - NTFS formatted for downloading torrents :)
1.5TB- Mirrored Drive (3TB total) formatted as NTFS = Windows recognizes this mirror set correctly.  Ubuntu saw both hard drives separately (not as a Raid pair) - I'm not worried about this right now.  But Ubuntu DID see both hard drives (and I was able to connect)

160GB- Recently formatted as FAT32 with Partition Magic in Windows.  This is the hard drive I want Ubuntu to see and write to; but after I formatted it, only Windows saw it...

Right now Windows can see all 4 Hard drives, and Ubuntu can only see 2 of my 4 hard drives.  It can only see my 160GB Dual Boot hard drive and the 200GB IDE hard drive (NTFS formatted).

What I'd like to know is why that 1.5TB set all of a sudden disappeared and why some hard drives are recognized by Ubuntu and some are not.  And I don't want to run any utilities that might jeopardize the contents of these other hard drives if that's what's needed.  

So I'm at a loss.  Ultimately, what I'd like to have is a dual boot where both XP and Ubuntu can recognize the hard drives and torrent files so I can download/upload on both OS's.  I know that might not be possible (as i'm adding torrent software and reads/writes to the mix..), but at the very least I would like to have all NTFS drives readable by Ubuntu and to have my only FAT32 drive readable AND writable by Both OSs.

Can anyone help?

---

### Post by imasterxx on 2009-08-05
update to my NTFS mirror set:  what's also strange is that initially ubuntu was able to see both my 1.5TB hard drives (that were suppose to be raided as a mirror set).  well now it recognizes them as unparitioned space.  and there's no way in hell i'm gunna partition them in linux and lose all my data.  but its weird that before i was able to mount and read the files but not anymore.  the last thing i remember doing was a Bunch of updates online.  maybe that had something to do with it... like 150gb worth of updates.

---

### Post by lensman3 on 2009-08-06
From a command line do "more /proc/scsi/scsi". That psuedo file shows what HD's the OS sees at the hardware level.  That doesn't mean what file systems each disk has.  That is what mount does. It associates a piece of hardware with a file system.

After that, start doing a "fdisk -l /dev/sda" (with the list flag. This command will tell you what file systems are on each of the disks as well as the partitions.

---

