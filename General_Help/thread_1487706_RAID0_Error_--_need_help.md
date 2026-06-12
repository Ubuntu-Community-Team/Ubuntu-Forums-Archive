---
title: "RAID0 Error -- need help"
date: 2010-05-19
forum: General Help
---

### Post by XtremeGamer99 on 2010-05-19
Hello,

I've been working on my server adding a few disks to the LVM. This required some of the files that I usually back up to the server to be moved to my main computer -- a BIOS (fake) RAID0 array that uses two 160GB Hitachi disks. The disk manipulation on the server, oddly enough, went fine. After I was done working on it, I turned back to my computer to find an incredibly slow desktop (was booted into Windows 7) -- it eventually crashed and I had to perform a hard reboot.

When booting, it shows an error on the RAID disk. it won't boot into either Linux or Windows 7. On Windows 7, it sometimes gets to teh logo. On Linux, it seems to read at least a little from the drive because it tries to mount the raid array via dmraid. It says, among other things, "ERROR: isw: wrong number of devices in RAID set "isw_bicdeefigd_Volume0" [1/2] on /dev/sda. It then goes on to say that device mapper failed, blah blah blah, and drops me to a recovery shell.

If I'm not mistaken, for it to get that far would require it to read from /boot, correct? If I remember correctly, everything was on the RAID0 array (ie: I did NOT have a separate partition for /boot) so it successfully reads at least part of the disk... Correct me if I'm wrong.

Considering that I have my backups on this RAID array due to unfortunate timing, it's somewhat crucial I'm at least able to access some files if not be completely bootable.

I have a Ubuntu installation that I can boot off my flash drive to perform recovery if need be. The drives are SMART enabled if that would help at all.

Can anyone help me? I know that RAID0 is not the smartest thing to use, but it's usually safe since I make backups to the server. It's just that, due to me working on the server, the backups are on the array. I've never done any sort of data recovery, so I'm not really sure where to start... I've read that I could try to disable the RAID on the BIOS and recreate it on Linux via dmraid. I've also read that performing a few simple diagnostics would clear errors, allowing it to boot. But I'm going blind here and would really like some assistance.

Thank you so much to whoever can help!

---

