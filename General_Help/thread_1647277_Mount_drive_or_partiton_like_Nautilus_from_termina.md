---
title: "Mount drive or partiton like Nautilus from terminal"
date: 2010-12-17
forum: General Help
---

### Post by COKEDUDE on 2010-12-17
Does anyone know how to Mount drive or partiton like Nautilus from terminal. Normally when you mount a drive or partition from Nautilus it will be mounted at **/media/<disk>**. The **<disk>** being a bunch of random numbers. I would like to be able to do this in a simple way from the terminal. 

Yes I know I can do this. I am hoping there is a simple way to do this all at once. 

```
sudo mkdir /media/<disk>
sudo mount fstype /dev/sda1 /media/<disk>
```

---

### Post by ajgreeny on 2010-12-17
Using terminal to mount a partition requires specific mount points to be available, so once you have the mount point made you will remove the need for that part of the mount process.

However you still need to specify a particular partition with a device name of some kind, either /dev/sdx# or the UUID.

I don't think there is a simpler way, I'm afraid.

---

### Post by COKEDUDE on 2010-12-18
Does anyone else know a way?

---

### Post by efflandt on 2010-12-18
There is a lot more that goes on behind the scenes than you realize with a click of the mouse.  That "random" number is actually the fixed and hopefully unique UUID of the partition (or partition label if it has one).  But whatever you use, you first need to create a mount point (sudo mkdir /media/something), then need to mount it there using the mount command with appropriate options (minimally: sudo mount /dev/sdx1 /media/something).

If you are going to frequently mount a partition from terminal or console, and have already created a directory to mount it on, then you can either configure a line in /etc/fstab to mount it automatically, or a line with noauto as one of its options, so it easily mounts only when you tell it to.

See **man mount** and **man fstab**.

---

### Post by Morbius1 on 2010-12-18
Let's say that /dev/sda1 is an ntfs partition that holds your Windows OS:

[1] Create a home for your partition to live in:
```
sudo mkdir /media/WinC
```[2] Mount the partition
[LEFT][COLOR=#000000]```
sudo mount -t ntfs /dev/sda1 /media/WinC
```It would be a lot easier if you had this in fstab so that you wouldnt need to keep mounting them from a terminal. Then you could add a line as simple as this in /etc/fstab:
```
/dev/sda1 /media/WinC ntfs defaults 0 0
```For NTFS you could add options to futher define exactly how you want it to mount but for a basic mount both of these will produce a partition that is owned by root but with permissions for everyone to read and write. Once you have it in fstab the next time you boot it will automatically mount sda1 to /media/WinC.

[URL="http://www.ehow.com/how_2180742_manually-mount-drive-linux.html#ixzz18VYwYJs2"]
[/URL][/COLOR][/LEFT]

---

