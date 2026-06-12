---
title: "Serious HDD Problem"
date: 2010-12-07
forum: General Help
---

### Post by Kyluke on 2010-12-07
Guys I have a serious issue here.
My bro yanked out my HDD (1TB NTFS) while I was copying a lot of stuff.

It won't mount anymore when I run 
```
sudo mount /dev/sdc1 /media/1
```the output is:
> 
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdc1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.But inside of windows the drive is not even recognized. Not even when I right click and select manage... etc

Gparted picks uo the drive and I can recreate the MBR but that will wipe the data.
Can I somehow run a chkdsk /f equivalent in ubuntu or can I simply repair the MBR without wiping the drive (it's possible with hirens but I don't have access to hirens)

Can some genius please help me all of my music is on there :(

---

### Post by oldfred on 2010-12-07
You really need to run chkdsk and run it until you get no errors as it does not fix everything in one pass.

Vista/7 CHKDSK
chkdsk [drive] /f /r
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

Only if chkdsk does not work:
If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

---

### Post by rubylaser on 2010-12-07
You could install ntfsprogs, and then run ntfsfix.
```
sudo apt-get install ntfsprogs
```
```
sudo ntfsfix /dev/sdc1
```

Using the Windows disk is probably the safer way to do this though.

Hope that helps.

---

### Post by Kyluke on 2010-12-08
omg oldfred test disk worked :D :D 
Thank you so much!! My music lives once again :D

---

### Post by oldfred on 2010-12-08
Glad it worked.

You can post as solved so others searching Forum for similar issues may find thread and know something that works.

---

### Post by wannabegeek on 2010-12-08
ntfsprogs...cool...I love Ubuntu....

This is a warning to you Kyluke to learn how to back up your files...HDs go on sale before and after Xmas...

I do it from terminal with rsync, but there may be better way when you're first learning. You'll never have a 
panic attack again...just the usual angry frustration :)

wbg

---

