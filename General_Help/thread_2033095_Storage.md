---
title: "Storage"
date: 2012-07-25
forum: General Help
---

### Post by adschem on 2012-07-25
Hello! 

Does anyone know if it is possible to have /home on an SSD so that access to the program information etc. is fast and keep all files such as documents and music etc...on a separate partition such as /data on a 1TB HDD? 

Thanks 
Adam

---

### Post by Cheesemill on 2012-07-25
Yes, that's exactly what I do.

All of my media folders in /home are symlinks to directories on my mechanical drive.

```
rob@precise:~$ df -h -t ext4
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        40G   16G   23G  42% /
/dev/sda3        20G  4.5G   15G  24% /home
/dev/sdb1       882G  364G  475G  44% /data
rob@precise:~$ ls -lh
total 4.0K
drwxr-xr-x 2 rob rob 4.0K Jul 25 15:35 Desktop
lrwxrwxrwx 1 rob rob   16 Jul 25 15:33 Documents -> /data/Documents/
lrwxrwxrwx 1 rob rob   15 Jul  6 11:53 Downloads -> /data/Downloads
lrwxrwxrwx 1 rob rob   15 Jul 13 21:55 Emulation -> /data/Emulation
lrwxrwxrwx 1 rob rob   10 Jul 25 04:29 ISOs -> /data/ISOs
lrwxrwxrwx 1 rob rob   11 Jul  6 11:53 Music -> /data/Music
lrwxrwxrwx 1 rob rob   15 Jul 25 15:33 Pictures -> /data/Pictures/
lrwxrwxrwx 1 rob rob   12 Jul  6 11:51 Videos -> /data/Videos
lrwxrwxrwx 1 rob rob    9 Jul  6 11:54 VMs -> /data/VMs
```

---

### Post by adschem on 2012-07-25
That is good news! :) How did you set this up? Was it as easy as create the partition create the folders within it and then set up links to these in Nautilus? 

Sorry bit of a newbie.

---

### Post by Cheesemill on 2012-07-25
Yes.

Except I created the links using the terminal using:
```
ln -s /data/Videos
```
etc..

But Nautilus should work just fine.

---

### Post by adschem on 2012-07-25
Silly question now, am I right in thinking that this will remove the link to /home/Videos? 

If so I will defiantly do it that way 

Thanks for your help!

---

### Post by Cheesemill on 2012-07-25
You need to delete the standard Videos folder first before creating the link.

Just make sure you've copied any data to the new location first before deleting the folder.

---

