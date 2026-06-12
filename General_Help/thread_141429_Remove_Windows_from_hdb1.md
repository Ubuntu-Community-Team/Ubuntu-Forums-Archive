---
title: "Remove Windows from hdb1"
date: 2006-03-08
forum: General Help
---

### Post by londonboi2k3 on 2006-03-08
Hi guys, I have two HDs , hda with ubuntu and hdb with windows on it, I have copied over all my files from windows to the linux drive!

What I want to do is create a folder called /data on the root of the file system which is auto mounted at boot to hdb. How do I format and mount the file system to ext3 and have it auto mounted so it is read write enabled?

I also would like to remove the swap partition on hda and place this on hdb, have been told that this creates better system performance. (is this correct?)

Thanks 

Londonboi

---

### Post by taurus on 2006-03-08
If you have /dev/hdb1 mount at boot, you have to unmount it first before you can format it...
```

sudo umount /dev/hdb1
sudo mke2fs -j /dev/hdb1
sudo mkdir /data
sudo gedit /etc/fstab
(remove the old entry for /dev/hdb1 and add a new one for /dev/hdb1 so it will be mounted automatically upon boot...)

```

I don't think it will improve your system performance whether you have swap on the first HD or the second HD...

---

### Post by dcstar on 2006-03-09
[QUOTE=londonboi2k3]
......
I also would like to remove the swap partition on hda and place this on hdb, have been told that this creates better system performance. (is this correct?)
......[/QUOTE]
Having your swap space on a separate drive from where you do most of you activity will improve performance - if you end up being a significant user of swap space (my system has sufficient RAM to rarely go to swap, so it wouldn't be much use to me).

It basically means that the swap drive can work in parallel with your other drives, instead of one waiting for the other when swap space is on the same drive as you may be using for normal work.

If you want to improve things even more, move your other drive to your second IDE channel, then your main (hda) drive will have exclusive use of the first channel without having to share that resource.

---

