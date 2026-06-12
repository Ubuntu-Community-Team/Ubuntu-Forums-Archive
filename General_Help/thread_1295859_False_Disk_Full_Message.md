---
title: "False Disk Full Message"
date: 2009-10-20
forum: General Help
---

### Post by ananswam on 2009-10-20
Hi guys,

I am running Ubuntu 9.04 64-bit on a Dell Latitude D630. I have a dual boot with Windows XP using GRUB. Recently, when I try to save files on my computer, Ubuntu will tell me there is not enough disk space. However, according to both the disk usage analyzer and the filesystem properties menu, I have plenty of free space. Here are the results of fdisk -l and df -h. Thanks for the help. /dev/sda5 is mounted as root.

```
******@******:~$ fdisk -l
******@******:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              16G  8.1G  6.7G  55% /
tmpfs                 993M     0  993M   0% /lib/init/rw
varrun                993M  116K  993M   1% /var/run
varlock               993M     0  993M   0% /var/lock
udev                  993M  164K  993M   1% /dev
tmpfs                 993M   84K  993M   1% /dev/shm
lrm                   993M  2.5M  991M   1% /lib/modules/2.6.28-15-generic/volatile
******@******:~$ 

```

---

### Post by P4man on 2009-10-20
thats.. odd
Is this a wubi install?

---

### Post by ananswam on 2009-10-20
No, this is a straight dual boot. Do you mean that the problem is odd or that the results to those commands is odd? Thanks.

---

### Post by P4man on 2009-10-20
> **ananswam said:**
> No, this is a straight dual boot. Do you mean that the problem is odd or that the results to those commands is odd? Thanks.

Well both I guess. Weird that you cant write to your home folder when you got plenty of free space. Weird cause ive never seen those tmpfs and lrm mounts.  Googling on the lrm filesystem mounted in /dev/shm seems to suggest its some kind of Ram disk. Which makes me wonder if its related to your problem? Seems almost like its the output of a livecd session? Im confused :confused:

---

### Post by lavinog on 2009-10-20
the tmpfs is normal
I think you need to use sudo with fdisk -l

Try forcing a fsck by:
```

sudo touch /forcefsck
```
then reboot

---

