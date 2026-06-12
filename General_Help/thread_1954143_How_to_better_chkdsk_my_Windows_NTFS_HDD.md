---
title: "How to better chkdsk my Windows NTFS HDD"
date: 2012-04-07
forum: General Help
---

### Post by mizifih on 2012-04-07
Hi folks! I have this HDD that's presenting some problems. When I chkdsk (/parameters) using Windows prompt (terminal), it get stuck at a point and don't finish checking the disk. I know, that's not good, chances are there's a problem on that sector or something like that making the chkdsk stop right there.

I know my disk is probably going kaput :(

What I need is a tool to run with Ubuntu Boot Disk to really check and make the HDD isolate that bad sector, letting me use the disk for a while.

What's the best tool available I should use?

Thanks ;)

---

### Post by oldfred on 2012-04-07
Generally it is best to use Windows tools to fix Windows and Linux tools for Linux.

I did find that Windows 7 version of chkdsk worked better on my XP NTFS partition than the XP version. But it wrote a Windows 7 Bootsector and I had to use Windows 7's bootsect.exe to create a new XP boot sector. I used testdisk to compare boot sectors and could see it wanting to boot with bootmgr not ntldr. 

Also you may have to run chkdsk multiple times as it does not fix everything on one pass.

If MFT issues see this:
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

---

### Post by Herman on 2012-04-07
Sometimes CHKDSK can appear to be stuck and eventually complete after a few days. Maybe you just need to wait a lot longer?

I agree with oldfred about Windows7 CHKDSK seeming better than Windows XP CHKDSK for Windows XP, I think so too. I didn't have the boot sector problem but I don't doubt it could happen. Windows DVDs seem to vary according to computer makes an models.

Most of the time GParted will refuse to work on a partition with a bad file system and I always recommend running CHKDSK before resizing partitions containing NT file systems.
On more than one occasion though, I have been able to fix Windows problems mysteriously by resizing the Windows partition a little with GParted. I can't explain why. It doesn't seem to make any sense, but it has worked for me a couple of times. 

On one occasion it did make sense. I was copying somebody's Windows from a damage hard disk to a new hard disk. The command I was using was making a perfect copy including the corruption from the damaged area of the disk. No matter what else I tried the new copy of Windows in the new disk would only boot to a blue screen. The owner of the computer hadn't made a recovery CD and the recovery partition was no good either. I managed to find out somehow, (probably from running the badblocks command), that the damage was confined to a small area somewhere close to the middle of the hard disk. (Where the heads crashed on the platters). Eventually I decided to try shrinking the partition away from the damaged area of the hard disk with GParted and then copy to the new disk, run CHKDSK and then boot it. It worked!

EDIT: I really think it's CHKDSK that ultimately fixes Windows though.

If you really think your hard disk is failing it's best to back up your files right away and move the operating system(s) to a new hard disk as soon as possible as it can be unpredictable how quickly or slowly a hard disk might fail completely once it starts to go.

---

