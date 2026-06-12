---
title: "Problem running fsck off LiveCD"
date: 2010-12-23
forum: General Help
---

### Post by madddonkey255 on 2010-12-23
My computer got hung up restarting after an update yesterday so I switched it off and back on, which led to the error message "No init found. Try passing init= bootrag", looking that up I found a thread that recommended running fsck to fix the errors.  

I first went to disk utility and did the check filesystem and repair button but that just had a pop-up that said "File system is NOT clean."  So I went and tried fsck on the drive which gave me the error message 
"fsck.ext4: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?"

Figuring this may have been caused by the disk utility I restarted and tried fsck again without opening any other program, and I still get the same error message.  What is causing this?  Swap?  What can I do to get fsck running to fix the original problem?

---

### Post by ridetheteapot on 2010-12-23
you can run fuser -m /dev/sda1 to find out whats running

---

### Post by madddonkey255 on 2010-12-23
Thanks for the reply, when I run that I get 
"Cannot stat file /proc/4135/fd/40: Stale NFS file handle"

What exactly does that mean?

---

### Post by madddonkey255 on 2010-12-23
I looked around and it looks like one of the standard quick fixes for the "stale NFS file handle" error is to unmount and mount the problem area so I did "sudo umount -a" and got the following busy devices:

/var/run
/tmp
/dev/shm
/rofs
/cdrom
/dev
/:

So now what can I do to fix the stale nfs file handle error, so I can fix the fsck problem, so I can actually fix my main problem? Ha

Thanks

---

### Post by madddonkey255 on 2010-12-27
I managed to get fsck to run off Systemrescuecd, and that fixed the problem temporarily, but now after a day or so the drive becomes read-only and then when I reboot it goes back to the "no init" problem, which is temporarily fixed by fsck.  What could the underlying cause be?  Is my hard-drive dying?

---

### Post by mcduck on 2010-12-27
> **madddonkey255 said:**
> I managed to get fsck to run off Systemrescuecd, and that fixed the problem temporarily, but now after a day or so the drive becomes read-only and then when I reboot it goes back to the "no init" problem, which is temporarily fixed by fsck.  What could the underlying cause be?  Is my hard-drive dying?

Could be. Use the Disk Utility and check the SMART status of the drive (if it supports SMART).

---

### Post by efflandt on 2010-12-27
See if the drive manufacturer has a utility that could check the drive for bad sectors and other issues.  I know that Western Digital (wdc.com) has one that can boot from CD or floppy.  And seagate.com might have something like that for their SeaTools for Seagate and Maxtor drives.

If you actually see bad sectors on a drive, that is usually a bad sign.  A drive normally reserves some space to automatically transparently remap good sectors in place of bad sectors, but if all the error sites get used up, the drive can only get worse.

---

