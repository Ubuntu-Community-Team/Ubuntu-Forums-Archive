---
title: "Inconsistent mtab file after smbmount/smbumount a windows share"
date: 2010-07-29
forum: General Help
---

### Post by ToniVC on 2010-07-29
Hi,

I have a server with Ubuntu 8.04.4 LTS completely patched up to date.

Today I tried to mount a windows share using smbmount and unmounting it with smbumount. I did it as a non root user (let's say "someuser") and managed to mount the share without problems with "smbmount \\\\server\\share xxx" where "xxx" was a directory on the user's root. After it I could see the shared files in the xxx directory, as it was supposed to be...

The problems came when trying to unmount it. Using "smbumount \\\\server\\share xxx" didn't work giving "This utility only unmounts cifs filesystems." error message. Then I tried "smbumount xxx" and worked. I couldn't see the files in xxx directory anymore, and I could even delete xxx directory. 

But now, when looking at /etc/mtab file, I still can see the share listed as mounted! The line is: "//server/share /home/someuser/xxx cifs rw,mand,nosuid,nodev,user=someuser 0 0". Also, df command lists the share as mounted too. But, as I said, the share is not really mounted, and I can even delete xxx directory without any problem... /proc/mounts doesn't list the share as mounted either... And, obviously, fstab file has no entry for this mount.

Moreover, /etc/mtab file group changed from root to someuser!

I don't really understand what happened, but I assume some bug with smbumount or smbmount. Anyway, what does really worry me is how to fix this mess... I already changed mtab file group back to root, but I don't know how to return the mtab file to a consistent state.

My main question is: can I simply edit mtab file and remove the inconsistent line?? I know one should never have to manually edit this file, but can it really be done in a situation like the one I'm describing? What could happen if I do it?

Also, I'm worried about if I don't do something to fix the inconsistency I could have problems when trying to shutdown the computer, or in any other situation. So, should it be safe to leave things unfixed and let everything return to normality when the system is rebooted?

I really hope someone can help me!

Thanks in advance,

Toni

---

### Post by dino99 on 2010-07-29
the easiest tool ive found to deal with partitions and devices is MountManager

---

### Post by ToniVC on 2010-07-29
> **dino99 said:**
> the easiest tool ive found to deal with partitions and devices is MountManager

I'm a bit worried about using such a program when my system is on an inconsistent state. I don't know how this inconsistent mtab file can affect future operations dealing with mounts...

I would like to know if I can fix it by hand, for instance editing mtab file and removing the inconsistent entry. Would it be dangerous to do so? What could happen? Also, what can happen if I leave the mtab file on this inconsistent state? Can I have problems when rebooting the system, for instance?

Thanks for your answer.

Toni

---

### Post by dino99 on 2010-07-29
tweaking fstab and mtab by hands let me always nervous, prefer to let the system dealing directly with them. 

Mountmanager is secure and well implemented, never had issue with it (system admin mountmanager)

---

### Post by ToniVC on 2010-07-29
Well, I just tried MountManager and it can't really solve my problem (or I can't figure how to do it).

Lets make it easier: would it be safe to just remove the line with the unmounted share that appears by mistake in the mtab file? The share is unmounted for sure since it doesn't appear on /proc/mounts and I even can remove the mount point. It's only that the smbumount program did actually unmount it but just failed to update the mtab file removing the line for some reason...

I just want to know if it could give me some kind of problem after removing it. I'm almost sure it would be safe, because mtab is only an "status" file, but I would like to be completely sure.

Thanks!

---

