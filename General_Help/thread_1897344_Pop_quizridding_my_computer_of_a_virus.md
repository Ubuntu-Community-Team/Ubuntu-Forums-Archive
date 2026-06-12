---
title: "Pop quiz/ridding my computer of a virus"
date: 2011-12-19
forum: General Help
---

### Post by Cyked on 2011-12-19
On my windows machine...

Long story short my mother is renowned for effing up computers.  My windows 7 box ended up with Win32/Agent.SDG.Gen trojan on it.  While it didn't render my machine useless (it would still boot) I ended up using an Ubuntu live CD and ran shred to overwrite 5 or so times on my OS disks.  Then I did this:

> Erase MBR

I had Linux with GRUB installed on a machine. I needed to get rid of it and put Windows on the machine. I used a Ghost recovery disk to restore Windows on it, but Ghost didn't restore the MBR. GRUB was still lurking in the Master Boot Record. On boot GRUB would try to start but would error out. Wiping out the MBR fixed the problem. This will wipe out the MBR of a disk (sda in this example) but keep the partition table and disk signature:

```
**dd if=/dev/zero of=/dev/sda bs=440 count=1**
```


I got everything back up, connected my other drives one by one and ESET still finds this on one of my drives.  Now, I can probably sort this out with some spare drives lying around, but I'd prefer a one and done.  If I run the above on this one disk still infected, is it going to hose the drive and I'll lose everything?

Am I better of getting the data off and running the above with shred just to make sure?

Thoughts?

---

### Post by seawolf167 on 2011-12-19
If I'm reading your post correctly - all you want to do is get rid of Grub as the MBR and have the Windows MBR present?

Why not simply use the Windows 7 cd and overwrite the boot loaders with the following commands in a rescue prompt?

```
bootrec.exe /fixboot
bootrec.exe /fixmbr
```

---

### Post by Cyked on 2011-12-19
Sorry.  I want to completely wipe the MBR.  I have 3 500gb drives plus 2 37gb raptors I have striped.  I ran shred and the above command on the raptors, restored windows with ghost, popped in my windows disk to fix MBR/boot on that.  Then I started connecting the 500gb drives one by one.  Only one of the 3 is still setting ESET off.  All 3 of the 500gb drives are non-boot drives, data storage only.  Is there really an MBR on that disk if there is no OS installed it?  If "yes", can I run the above command and be ok.  If no, I would then guess that I need to backup the important stuff that is not already backed up and run shred on the drive.

---

### Post by seawolf167 on 2011-12-19
If you had ever used that drive as a boot drive there could be a MBR still on it - I'm not familiar with the Windows tools you mentioned, but provided you keep this part

```
bs=440
```strictly less than or equal to 446, it'll remove the MBR but keep the partition table on the drive and you should be good to go.

I'd highly suggest backing up with [Clonezilla ]("http://www.clonezilla.org")before you do this just in case.

---

### Post by Cyked on 2011-12-19
ESET?  Its nod32 virus scan.

The drive has never had an OS on it, which is why I'm scratching my head over it.

---

### Post by Cyked on 2011-12-21
Well eff me sideways.  I got greedy, mostly because I have no time and was looking for a quick fix (12+ hour days at work and a 19 m.o. and a 8 week old at home).  I copied over the really important stuff that wouldn't have been in the most recent backup.  I ran the command above with bs=440 on the drive, rebooted and the drive is now RAW.  So I just added a good chunk of hours to recovery time.

It does seem that I need to shred the drive.  Even after running that and it being RAW antivirus still says there's an issue.  Luckily, this was the least important drive.  I don't even know what I had on it, save for pictures and music, both of which I backup.  And those are the only things I have probably accessed the drive for in the past year.

---

