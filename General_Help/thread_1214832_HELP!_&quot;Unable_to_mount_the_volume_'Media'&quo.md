---
title: "HELP! &quot;Unable to mount the volume 'Media'&quot;..."
date: 2009-07-16
forum: General Help
---

### Post by sweet_regina on 2009-07-16
After a restart, I attempted to open my Media drive and this message showed up (below)...I'm still a novice when it comes to using Ubuntu so I'm pretty uncertain as to what it is telling me to do. Please help...all of my music is on here!

[SIZE=4][COLOR=Red][COLOR=Black][SIZE=3]CANNOT MOUNT VOLUME.[/SIZE]
[/COLOR][SIZE=3][SIZE=2][COLOR=Black]
UNABLE TO MOUNT THE VOLUME 'MEDIA'[/COLOR][/SIZE]

[SIZE=2][COLOR=Black]$MFTMirr does not match $MFT (record 0). Failed to mount '/dev/sbd1': Input/output error NTFS is either inconsistent, or you have hardware faults, or you have a SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows TWICE. The usage of the /f parameter is very important! If you have SoftRAID/FakeRAID then first you must activate it and mount a different device under the /dev/mapper/directory, (e.g. /dev/mapper/ nvidia_eahaabcc1). Please see the 'dmraid' documentation for the details.

[SIZE=1]thanks![/SIZE]
[/COLOR][/SIZE][/SIZE][/COLOR][/SIZE]

---

### Post by michy99 on 2009-07-16
What is the output from these commands?```
sudo fdisk -l
cat /etc/fstab
```

---

