---
title: "Mount Launcher for Virtualbox"
date: 2010-11-09
forum: General Help
---

### Post by Hagbard_C on 2010-11-09
hi, use have ubuntu 10 as client on a windows7 comp. have used the "shared folder" options of virtualbox to share my external harddrive, the command:

sudo mount.vboxsf J_DRIVE  /mnt/J_DRIVE

works. but when i go to make a launcher:
sudo nano /usr/local/bin/extlauncher
command: sudo mount.vboxsf J_DRIVE  /mnt/J_DRIVE

sudo chmod +x /usr/local/bin/extlauncher

everything goes fine, but upon launching my launcher ubuntu doesnt mount my external harddrive.

adding 
J_DRIVE /mnt/J_DRIVE vboxsf rw,exec,uid=1000,gid=1000,dev 0 0
to fstab also works fine.
[B]
do i need to create a launcher differently when i want it to contain a sudo command?[/B]

thanks.

---

### Post by Hagbard_C on 2010-11-09
ok i have to change the command to gksudo. i thought it might be a bit more compilicated because of the whole virtualbox thing.
cheers

---

