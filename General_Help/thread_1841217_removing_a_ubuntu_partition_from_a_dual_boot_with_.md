---
title: "removing a ubuntu partition from a dual boot with 2 ubuntu versions"
date: 2011-09-09
forum: General Help
---

### Post by Vrael on 2011-09-09
Hi,
  So I had a normal dual-boot machine with windows 7 and maverick installed on different partitions. Then, for a project, I needed lucid, so i installed it in parallel to these 2, on its own partition.
  Now, I'm done with the use of lucid and I want to remove it and have the disk-space back.(I know lucid is LTS, but I've tuned my maverick very painstakingly and so I don't want to remove it).
  So, how do i remove Lucid safely, without deleting the grub(so that i can still access win 7 and maverick afterwards)? there are many tutorials which show you how to do so from inside windows, but they would delete the grub and reinstall windows mbr.
Wouldn't that mean that I lose access to any linux partitions present?

---

### Post by garvinrick4 on 2011-09-09
First boot into your maverick install and open a terminal:
```
sudo grub-install /dev/sda
``````
sudo update-grub
```That will make your maverick in control of grub. So you can now remove lucid and do whatever
you want with the space it leaves.

Most use gparted as a partitioning tool.
```
sudo apt-get install gparted
```In your maverick install:

Now type in terminal (while in maverick:)
```
df -h
```That will tell you your maverick sda#  that will be the one you want to keep.

Below is a gparted site I had in my bookmarks, always be careful and focus with partitioning tools.
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

#If you need further help just post that you do.

---

### Post by Vrael on 2011-09-09
and i'm guessing the dev/sda partition should be the one on which maverick is installed?

---

### Post by garvinrick4 on 2011-09-09
> **Vrael said:**
> and i'm guessing the dev/sda partition should be the one on which maverick is installed?
No,
/dev/sda is the drive and where the grub is installed. 

/dev/sd[COLOR=Red]xy[/COLOR]  are the partitions.
[COLOR=Red]x[/COLOR] being the drive number a,b,c,d  and so on down the line.
[COLOR=Red]y[/COLOR] being the partition number such as 1, 2, 3 and so on.
For example If you had a second drive lets say plugged in to USB port would be drive sdb  and its first partition sdb1 then sdb2 and so on.

Run this in a terminal and look at your drive.
```
sudo fdisk -l
``` Lower case L

And if while in maverick you look at the output of.
```
df -h
```will show your partition number for maverick.

---

### Post by raja.genupula on 2011-09-09
> **Vrael said:**
> Hi,
  So I had a normal dual-boot machine with windows 7 and maverick installed on different partitions. Then, for a project, I needed lucid, so i installed it in parallel to these 2, on its own partition.
  Now, I'm done with the use of lucid and I want to remove it and have the disk-space back.(I know lucid is LTS, but I've tuned my maverick very painstakingly and so I don't want to remove it).
  So, how do i remove Lucid safely, without deleting the grub(so that i can still access win 7 and maverick afterwards)? there are many tutorials which show you how to do so from inside windows, but they would delete the grub and reinstall windows mbr.
Wouldn't that mean that I lose access to any linux partitions present?
```

sudo os-prober
``` 

gives you at what partition you have installed the all the OS's .

boot to the ubuntu os which you want .

then do this 

```
sudo dpkg-reconfigure grub-pc
```
this will install grub for this current os , from disk utility menu you can format that unwanted ubuntu  OS . then 

```
sudo update-grub
```

everyhting will be fine

---

### Post by Vrael on 2011-09-09
Thanks everyone for the help. 
I have the system working fine with the needed free space.

---

