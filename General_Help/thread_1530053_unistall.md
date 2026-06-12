---
title: "unistall"
date: 2010-07-13
forum: General Help
---

### Post by cowboy7305 on 2010-07-13
i have winsows7 and 9.1 ubuntu and 10.04 ubuntu on computer on same disk
i want to completely remove 10.04 from disk also the grub loader files that 10.04 uses 
is there a way of doing this ,i dont like 10.04 its playing up on my computer not as solid at 9 ,i know others will disagree but thats my findings 
many thanks

---

### Post by lordskid on 2010-07-13
if your partition number for karmic (e.g. sda4) is lesser than that of lucid (e.g. sda5) then boot to karmic... if not use a livecd any will do. backup ur files from lucid (if any) then just delete the partition.

WARNING do not shut down at this point!!!

drop to a terminal and type the following:
```

sudo install-grub /dev/sda (if using grub as default bootloader or add the partition number if using windows bootloader)
sudo update-grub

```
if you are using grub as default bootloader ur good to go. if using windows bootloader...
lets assume karmic is in /dev/sda4 and windows in /dev/sda2
```

sudo mount /dev/sda2 /mnt
sudo dd if=/dev/sda4 of =/mnt/karmic.ldr bs=512 count=2
cd /mnt
sudo echo c:\\karmic.ldr=\"Ubuntu\" >> boot.ini

```
just unmount the drive and you can reboot now.

---

