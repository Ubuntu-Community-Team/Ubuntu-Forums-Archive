---
title: "Trouble sharing files on 2nd Hard Drive"
date: 2006-06-07
forum: General Help
---

### Post by JSVH on 2006-06-07
On my network I have my laptop (Dell Inspiron 8200, dual boot Win XP and a fresh install of Ubuntu 6.06), my HTPC (Asus DiGiMatrix with fresh Ubuntu 6.06 install), and several other Windows computers (roommates).

I am able to share files on my HTPC, and on my laptop in my "Home/Shared" folder via "right-click>share folder". However on my laptop I have a second hard drive that holds about 40GB worth of music in its "hdc1/Music" folder. "right-click>share folder" seems to work fine but when I go to  "Places>Network Servers" and navagate to the my "music" folder I get an "The folder contents could not be displayed. "Music" couldn't be found. Perhaps it has recently been deleted." error message.

I dont what do, I have spent several hours searching with no luck. I think the problem my be with permissions because "hdc1/Music" will not allow others to read or write. And it will not allow me to to change permissions, owner, or group even if as root.

Thanks, John.

---

### Post by stanthecaddy22 on 2006-06-07
you should be able to change permissions from command prompt, something like the following:

"sudo chmod -R 755 [foldername]" that is if you are in the directory above the music folder.

---

### Post by JSVH on 2006-06-07
It is still not changing the permissions. 'sudo chmod -R 755 Music' does not come back with any complaints but when I check the permissions via ls -l it is not changing permissions for "others" it is still drwxrw----. But if I try to go about it "sudo chmod -R =rwx,g+s Music" it comes back with a "chmod: changing permissions of 'Music': Operation not permitted". 

It is not letting me change owner or group either. the owner is 'root' and the group is 'plugdev' if that matters.

Thanks for your help.

---

### Post by JSVH on 2006-06-07
It also may be important to note that this hard drive is vfat, so I can share it with my Win XP partition. Maybe I need to change something in my fstab?

---

### Post by givré on 2006-06-07
Could you post the /etc/fstab of your laptop, please.
Permission of fat and ntfs are set via the option of mount, you cann't change it after

---

### Post by JSVH on 2006-06-07
I have not changed it sence I installed. Here is my /etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdc1       /media/hdc1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda2       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by givré on 2006-06-07
Okay, so here the problem,```
defaults,utf8,umask=007,gid=46 
```
You have to change umask=007 (= rwxrwx---) to umask=002 (= rwxrwxr-x)
Say if it is okay (your gid is also stange but it should work).
With that you will not have write access, just read, is that you want?

---

### Post by JSVH on 2006-06-08
Thank you so much! That worked! =D> 

I think I just want to be able to read, but if I want to be able to write also do I just change it to umask=000?

---

### Post by givré on 2006-06-08
[QUOTE=JSVH]Thank you so much! That worked! =D> 

I think I just want to be able to read, but if I want to be able to write also do I just change it to umask=000?[/QUOTE]
Yes you understand it. 8)

---

