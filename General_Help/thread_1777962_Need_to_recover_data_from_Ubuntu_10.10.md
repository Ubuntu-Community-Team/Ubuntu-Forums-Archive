---
title: "Need to recover data from Ubuntu 10.10"
date: 2011-06-08
forum: General Help
---

### Post by Erdr1ck on 2011-06-08
I've been using Ubuntu 10.10 on my EEE-PC for most of my thesis research, but I left it running a python script overnight and now I can't get it to login.  I was running low on disk-space, and I think the problem is that the script generated a lot of text files and used up all of the available hard drive space. 

Now, whenever I try to boot the machine, it reaches the user-select/login screen, but logging in just causes it to go black for a second before returning to the login screen.

I have Ubuntu 11.04 on a USB, and Ubuntu Rescue Remix on another, and both allow me to boot up my machine, but I can't see my hard-drive - neither in /mnt/ nor in /media/ - in order to copy my thesis files or to delete some excess text files to free up some hard-drive space.

Any suggestions would be greatly appreciated - I really need to recover this data for my Thesis as soon as possible.

-Brett

---

### Post by wojox on 2011-06-08
You have to mount your hardrive's partition. Run:

```
sudo fdisk -l
```

Find the partition which you need and 

```
sudo mount /dev/sdaX /mnt
```

Replace X with whatever number and look again.

---

