---
title: "syncing ipods to ubuntu"
date: 2010-08-03
forum: General Help
---

### Post by Ajansen1 on 2010-08-03
hey guys i have my entire music library on my rythmbox/harddrive i just dont know how to sync the ipod to ubuntu or how to work it without itunes

any help is appreciated

---

### Post by drpjkurian on 2010-08-03
Hi 
try [this]("https://help.ubuntu.com/community/PortableDevices/iPod") link

---

### Post by Ajansen1 on 2010-08-08
thanks for that link, but i still cannot get this to work properly, i have a thrid generation ipod touch.

rythmbox recognizes the ipod and i can delete files off the ipod jsut fine using rythmbox.

but i cannot move new music to the ipod in rythmbox.

gtkpod does not recognize the ipod

---

### Post by tim.sargent on 2010-08-17
I am having a similar situation with a 1st generation iPod Touch (firmware 3.1.3).  It mounts itself when plugged in but cannot be recognized by gtkpod.

---

### Post by maghreb on 2010-08-17
After looking on google for some time  and reading what was said there (no answer really), i found an answer to  my "error transferring track: permission denied" problem while copying  tracks to ipod.

I found a working (for me) answer here:

[http://davesource.com/Solutions/2008...read-only.html]("http://davesource.com/Solutions/20080225.iPod-linux-read-only.html")

For the lazy or in case of link failure, I'll write it here.

Find where is your ipod (/dev/sdXX/):
```
df
```After, find the UUID of ipod's partition (on Karmic)
  ```
ls -l /dev/disk/by-uuid
```*use the UUID of the partition, not the disk.

Add an entry to /etc/fstab:
```
UUID=DEVICE_UUID_HERE      /media/iPod     auto  rw,user,noauto  0   0
```*You want to use UUID because /dev/sdX is not constant and may change when pluging other devices.

Then created the mount point:
```
mkdir /media/iPod
```Safely removing ipod the reconnecting it and Voilà!

hope it helps!

mag

---

