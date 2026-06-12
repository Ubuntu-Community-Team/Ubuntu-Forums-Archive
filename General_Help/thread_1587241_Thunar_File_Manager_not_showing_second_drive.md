---
title: "Thunar File Manager not showing second drive"
date: 2010-10-03
forum: General Help
---

### Post by Foxmaster1 on 2010-10-03
How do I get Thunar File Manager to reference second hard drive in desktop PC? I see teh C drive but have a second hard drive that say Exaile will reference but need to copy files around from second drive to main drive. New to Xubuntu not sure how to achieve

---

### Post by searchfgold6789 on 2010-10-03
Welcome to the forums.
Your second [or non-system] hard drive is the second one, am I correct?
The way I do this is to open up a terminal and
[replace the /dev/sdb1 with the drive you want to appear]
```

sudo mkdir /media/second
sudo mount /dev/sdb1 /media/second

```Now go into thunar, click on your main system disk, click on the folder "media", and click on the folder "second" and your files will appear there. The files are not copied to your main hard disk, they are simply appearing there...
Now if you want this secondary hard drive to mount every time you run the system you will have to follow the instructions on [this page]("https://help.ubuntu.com/community/Fstab") to add it to your /etc/fstab file.
Have fun!

---

