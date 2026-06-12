---
title: "Hard drive permission from Live CD"
date: 2010-06-24
forum: General Help
---

### Post by Drop D on 2010-06-24
For some reason, Ubuntu 10.4 LTS cannot boot normally, so I have reverted to a live CD, no concern, I can just reinstall, what I am concerned with is the fact that I get my music.  I load up the live CD, and I am able to access my hard drive, but I as I found my music folder, I cannot copy and past and/or move ANY folders into a flash drive.  It says I do not have permission.  

I need some help as soon as possible.

---

### Post by Drop D on 2010-06-24
Anyone?!?

---

### Post by SoFl W on 2010-06-24
Everyone with a problem needs help as soon as possible.

Did you try coping the files as root?

---

### Post by garvinrick4 on 2010-06-24
Give command in terminal

```
ls -la
```scroll down to Music and see what permissions are.
drwxr-xr-x is normal.( let me know if it does not say this).

Can you download anything to flash drive or just Music gives you trouble.

If it is the flash drive:

given my login name is rick and my flash drive label is hp (change to your own)

```
sudo mkdir /media/hp
```  (making a directory)

```
sudo chown -R rick:rick /media/hp
```  (giving rick (me) ownership instead of root)

Use your own login name and your Label if do not have a label can give one in gparted with right click or Disk Utility under Edit File System Label.

---

