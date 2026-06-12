---
title: "Unable to mount WD mypassport HD"
date: 2010-01-04
forum: General Help
---

### Post by ljh07002 on 2010-01-04
I received a WD 750gb My Passport hard drive for Christmas, after using karmic for a few months. However, when I plug in the drive, I get an error message that says "Unable to mount My Passport", followed by: 

Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

And I have no clue what this means. I figured that this would be a good first place to ask for help, as my roommate (who is my go-to for help with all things Linux) is also home for winter break. I would appreciate any help that can be given.
Thanks,
Luke

---

### Post by cariboo on 2010-01-04
There seems to be an error on your hard drive, If you have a windows partition, it may be a good idea to do what the error message says, boot in to windows and run chkdsk /f on the drive.

---

### Post by ljh07002 on 2010-01-04
Hmmm, no windows partition here... this is the first time I have felt like I needed one. Can I use the same check disk command in Ubuntu?

---

### Post by todak on 2010-01-04
If you have no data on the drive, then open gparted and simply reformat as NTFS and then mount.

---

### Post by Gizenshya on 2010-01-04
I've had that message a few times.  Mostly it is when using old, failing drives, or after unplugging drives during file transfers.  It is always best to unmount first, but sometime I get annoyed... especially if there isn't anything important on the drive.

I usually just force mount and be done with it.

---

### Post by jamesisin on 2010-01-04
I second the reformat notion.  No sense in fretting over a new drive and what the manufacturer did 'for the benefit of the consumer'.  Just scrap their partition and create your own.  If you only use Ubuntu, then you could use ext3 or ext4.  If you use other operating systems, then you should probably use FAT32 on that drive.

---

### Post by ljh07002 on 2010-01-05
Ok, using gparted to reformat the drive... should I use ext3, ext4, or NTFS? Why one over the others?

---

### Post by bodhi.zazen on 2010-01-05
> **ljh07002 said:**
> Ok, using gparted to reformat the drive... should I use ext3, ext4, or NTFS? Why one over the others?

If you use windows you can use ntfs

If you no longer use windows I suggest ext4

---

### Post by jamesisin on 2010-01-05
If you intend to share with Mac and Windows, you'll likely want FAT32 (be mindful of its limitations).  If you share with Windows only you can get by with NTFS.

I'd probably just format it with ext3 or ext4 and then use a Samba share to offer items to the Windows machines though.

---

### Post by TryingLinuxAgain on 2011-07-06
Just wanted to throw my experience in here:

I just purchased a 1TB WD Blue "My Passport Essential SE".  I Formatted it in Ubuntu with NTFS because I intend to backup two Linux machines and two windows machines with this drive.

Started copying files from an older 400Gb USB drive and, after about 1 hour of copying, received the error mentioned at the beginning of this email.

Brought it to a windows PC and did a chkdsk /f on it and it did find and fix errors.  Ran chkdsk again and found no errors.

Brought it back to the Ubuntu PC and restarted a copy.  After about 30 minutes, errors started appearing again.  Although, at this point it is still mounted after I chose "skip".  Certainly some of these problems could be caused by the "source" 400Gb drive, but I've never had any problems at all with that drive.

At this point I'm suspecting the 1Tb WD drive.  I'll return this and try another.  If the same problems persist I might get one for windows (formatted with NTFS) and use another for Linux (formatted with EXT4).   I'll update this forum with my experience.

Thanks as always to the great Ubuntu support community!
Dave

---

