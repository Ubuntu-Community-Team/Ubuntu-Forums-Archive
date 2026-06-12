---
title: "Partitioning problem"
date: 2011-12-14
forum: General Help
---

### Post by Powergate92 on 2011-12-14
I am going to change operating systems from Zorin OS 5 to Ubuntu 11.10. I would like to backup all my stuff before I change OSs. So I used Gparted on the Ubuntu 11.10 live DVD to make the partition Zorin OS is on smaller, and create a new second ext4 partition to backup my stuff to. After that, I booted back into Zorin OS to backup my stuff using Deja Dup and Deja Dup an error message, so I tried again and it gave me a error message again. So then I tried to backup my stuff by copying and pasting to find I could not paste into the new partition. So I looked at the permissions for the new partition and it says "Owner: root" and "Group: root." What did I do wrong that the new partition is set to root and will not let me backup my stuff to it.

---

### Post by oldfred on 2011-12-14
Welcome to the forums.

If you just need a mount. 777 is the most permissive you can have, read, write & execute. you can use /mnt or /media. /media may be slightly easier as you will not have to drill down thru system to see it with Nautilus. 

sudo mkdir /mnt/data
sudo chmod 777 /mnt/data
sudo chown $USER:$USER /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
#if not known to list partitions
sudo fdisk -l

If you want to permanently mount it.

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by Powergate92 on 2011-12-17
> **oldfred said:**
> Welcome to the forums.

If you just need a mount. 777 is the most permissive you can have, read, write & execute. you can use /mnt or /media. /media may be slightly easier as you will not have to drill down thru system to see it with Nautilus. 

sudo mkdir /mnt/data
sudo chmod 777 /mnt/data
sudo chown $USER:$USER /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
#if not known to list partitions
sudo fdisk -l

If you want to permanently mount it.

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

When I go into the new partition in the file manager it mounts the new partition and shows that there is a "lost+found" folder. So I don't think mounting the new partition is the problem.

---

### Post by oldfred on 2011-12-17
The lost & found is just a default.

Nautilus may show partition, but if root is the owner only root can use it.

---

### Post by Powergate92 on 2011-12-29
> **oldfred said:**
> Welcome to the forums.

If you just need a mount. 777 is the most permissive you can have, read, write & execute. you can use /mnt or /media. /media may be slightly easier as you will not have to drill down thru system to see it with Nautilus. 

sudo mkdir /mnt/data
sudo chmod 777 /mnt/data
sudo chown $USER:$USER /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
#if not known to list partitions
sudo fdisk -l


Do I put that into the terminal all at one time or one at time?

---

### Post by oldfred on 2011-12-29
Each line is a terminal command that you have to enter and then press enter. You can copy & paste from here to your terminal.

---

