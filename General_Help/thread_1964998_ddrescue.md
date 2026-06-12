---
title: "ddrescue"
date: 2012-04-24
forum: General Help
---

### Post by sperian on 2012-04-24
hey,
i have a hard drive /dev/sda with 2 partions on it 1, /dev/sda1 and /dev/sda2. I have some files on sda2 which i lost and have been able to recover on windows but with limited luck. 
im trying to use ddrescue with code 
ddrescue -r 3 /dev/sda2 /dev/sda1/image /dev/sda1/logfile.
but all i get i get is 
ddrescue: Can't open input file: Permission denied
i decided to mount the drive and go to its properties where i found 
under permissions it say "you are not the owner so you can not change these permissions and in gparted under file system is says its unknown. 
maybe when i set up ubuntu 11.10 to allow me to view partioned hard drives i did it wrong. i partioned the hard drive on windows 7. i think its a fat or fat32 partion.
can i get some help, i really want to get the pictures of the hard drive.
cheers

---

