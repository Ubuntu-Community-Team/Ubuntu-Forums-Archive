---
title: "Errors In backing up data"
date: 2010-03-07
forum: General Help
---

### Post by Enevel on 2010-03-07
My windows xp recently got bugged and I can't access any of my files, so I am using ubuntu to try to do a backup. When I try to open my hard drive from ubuntu i get the error message: 

Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to calculate free MFT records: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

Also, I have tried using the information on this site to do the backup:
 [http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)

When I enter the command: mkdir /media/disk
I get the message: mkdir: cannot create directory '/media/disk': File exists

What do I do????

---

### Post by dE_logics on 2010-04-21
Why don't these questions have answers??

---

