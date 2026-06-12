---
title: "Error Mounting Drive??"
date: 2010-06-26
forum: General Help
---

### Post by Anonymous Rain on 2010-06-26
Error Message:
[B]
Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdc1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.[/B]

Why am I seeing this? I can't access my external 1TB hard drive :(

---

### Post by gzarkadas on 2010-06-26
The message is self-explaining and quite detailed, full with instructions. You only have to break it in its subcases and then match one of them with your configuration. So, you must tell us what is your configuration:

1. You use the drive to dual boot with windows?
2. You have a raid on the drive and if yes what type of raid?

In addition, how do you mount your drive, ie what are the lines in your /etc/fstab that mount the drive look like?

---

