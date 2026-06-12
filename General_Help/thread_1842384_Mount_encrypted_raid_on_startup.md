---
title: "Mount encrypted raid on startup"
date: 2011-09-11
forum: General Help
---

### Post by mcemsi on 2011-09-11
Hi guys

can anybody tell me how to mount an encrypted software raid on system startup?

if I do it by hand i use the following commands:

mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1[FONT=monospace]
[/FONT]cryptsetup luksOpen /dev/md0 encrypted
mount /dev/mapper/encrypted /storage

I somehow have to assemble the raid and decrypt the partition before fstab is execute, right?

Thanks a lot!

---

### Post by Basher101 on 2011-09-11
try editing your fstab file. use with caution as you can mess up your mounting...just google some guides

---

### Post by mcemsi on 2011-09-11
Thanks for your reply.

I know how to put the entry into the fstab, but 
I need to assemble the raid and decrypt it  before i can mount it.

(Before there is no entry in /dev/mapper)

---

### Post by Basher101 on 2011-09-11
well i have no raid setup...i dont even know what raid is so i cant help ya :/

---

