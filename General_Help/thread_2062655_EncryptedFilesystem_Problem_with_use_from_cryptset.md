---
title: "EncryptedFilesystem :Problem with use from cryptsetup"
date: 2012-09-25
forum: General Help
---

### Post by saeedsssss on 2012-09-25
HI
I do this works for my goal.my goal is a encrypted partition(/dev/sda3) that want me password in time booting system.
1- apt-get install cryptsetup
2- cryptsetup luksFormat /dev/sda3 
3- cryptsetup luksOpen /dev/sda3 st
4- mkfs.ext3 /dev/mapper/st 
5- st /dev/sda3 non luks to /etc/crypttab
6- mkdir /mnt/st
7- /dev/mapper/st /mnt/st ext3 defaults 0 1 to /etc/fstab
8- restart

but when restart my compuer , I see this error 
"The disk drive for /mnt/st is not yet ready or not present"

what's reasen this error ?

---

