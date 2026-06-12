---
title: "USB Flash cannot be reformatted/erased."
date: 2009-08-06
forum: General Help
---

### Post by tomasrey88 on 2009-08-06
I tried to use gparted to erase/reformat my 32 gb usb flash but it wouldn't work. I set a ms dos disklabel, then when I tried to reformat it as FAT32, it gave me an error. Setting I used: primary partition, fat32, round to cylinders. Clicked apply, then it gave me an error message. Following is the error file. Please let me know how to delete my USB flash. There's a little lock shape on top of the folders in the usb flash and it wouldn't lett me drag and drop all the files into the trash. That gave an error, too. I finally managed to remove the lock shape on the usb flash by  changing the properties permissions to include create and delete files, all files are delted, but it will not allow me to save any new files. I'm guessing it is because the device is not formatted fat 32, ext3, nor any file system at all, but gparted will not allow me to do this. What should I do? Thanks. 

GParted 0.3.5

Libparted 1.7.1

   **Create Primary Partition #1 (fat32, 29.79 GiB) on /dev/sdb**  00:01    ( ERROR )             create empty partition  00:01    ( SUCCES )             [I]path: /dev/sdb1
start: 63
end: 62476784
size: 62476722 (29.79 GiB)[/I]          set partitiontype on /dev/sdb1  00:00    ( SUCCES )             *new partitiontype: fat32*          create new fat32 filesystem  00:00    ( ERROR )             ***mkdosfs -F32 -v /dev/sdb1***             [I]mkdosfs 2.11 (12 Mar 2005)
[/I]       *mkdosfs: /dev/sdb1 contains a mounted file system.*

---

### Post by Mighty_Joe on 2009-08-06
> **tomasrey88 said:**
> 
mkdosfs: /dev/sdb1 contains a mounted file system.

Unmount the drive.

---

### Post by tomasrey88 on 2009-08-06
How do you unmount it? I thought that you unmount a mounted file system by setting a new label and repartitioning/reformatting it. This will "erase" everything from before and allow new data to be placed on the usb drive. At least that's how I understand it (correct me if I'm wrong). 

The unmounting you're proposing is just something you do just before you unplug something. But just to humor you, just in case this works, I typed into the terminal: 

panda@pandamonium-desktop:~$ umount /media/KINGSTON
umount: /media/KINGSTON is not mounted (according to mtab)
panda@pandamonium-desktop:~$ ls /media/KINGSTON
ls: cannot access /media/KINGSTON: No such file or directory

Please, how do I reformat the USB flash to delete all the data so that I could reuse it? 

Thanks, 
:P

---

### Post by Bucky Ball on 2009-08-06
Right click on it and unmount. 

You can also use a terminal:

```
sudo umount /media/KINGSTON
```
Run:

```
sudo blkid
```Is it there? You could try:

```
sudo umount /dev/sd**
```

---

### Post by tomasrey88 on 2009-08-06
I solved it (yay!). I reformatted it with no format. Then, I formatted it as FAT32.

---

