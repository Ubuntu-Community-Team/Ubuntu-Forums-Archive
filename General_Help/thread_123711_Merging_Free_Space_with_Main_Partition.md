---
title: "Merging Free Space with Main Partition?"
date: 2006-01-30
forum: General Help
---

### Post by Protex on 2006-01-30
Hi guys, I recently re-sized my swap drive. (It was 2.2 GB for some reason?!) and I want to allocate the free space to my main drive, how would I do that without damaging any data. Keep in mind that the drive is in use constantly, as it is my main drive.

Thanks guys.

---

### Post by MetalMusicAddict on 2006-01-30
If I remember right its not possiable in Linux. Maybe with Partition Magic. I know gParted cant do it. Was the reason for me to do a new install. I got some free space also.

---

### Post by Jiketsu on 2006-01-30
It is very possible in Linux. I would recommend using a program called **parted** .

If you are using Ubuntu 5.10 it should already be installed. If you are somewhat resourceful and can figure things out on your own, then you should be able to get along okay. To get started, using a terminal:

```
sudo parted
```You will now be inside the parted program. Type... ```
help
```...to get a list of options available to you. To start, use the command... ```
print
```...to see what your current setup is like. If you cant figure out how to proceed from there let us know. I might not reply back again but if I come around I will help you out.

BTW: It should be safe to resize your hardrive while Linux is running, that is, as long as you are allocating unused space to the partition and not shrinking your current one, as I don't think **parted** moves the memory to make room. *Just make sure that if it asks you to format you say **no***. You may need to use your **Ubuntu Live CD** (If you have one) to perform this task, it would be much safer for your case.

Good luck.

-Ji

---

### Post by az on 2006-01-30
You cannot change the size of a mounted partition.  Gparted *can* of course make these changes, but you have to be running from a live cd.  Booting the ubuntu live cd and using gparted would require that you unmount your swap

swapoff -a

The free space is at the end of your drive, correct?  You need to delete the swap space, extend your "/" partition and the filesystem on it and then recreate the swap with the remaining space.  You should not need to change your fstab, since the drive naming will not change.

You should be able to do this safely, but always back up your data to be prudent.

---

### Post by R3linquish3r on 2006-02-25
I used the method in post 3 to icrease the size of my extra drive were I store extra files. Now when I try to mount it it says:

```
ed@ubuntu:~$ sudo mount -a
mount: special device /dev/sda1 does not exist
```

---

### Post by dcstar on 2006-02-26
[QUOTE=R3linquish3r]I used the method in post 3 to icrease the size of my extra drive were I store extra files. Now when I try to mount it it says:

```
ed@ubuntu:~$ sudo mount -a
mount: special device /dev/sda1 does not exist
```[/QUOTE]
Start your X session as normal, then do:

System-Administration-Disks and look at the partitions listed for your drive.

---

### Post by R3linquish3r on 2006-02-26
Ok I'm looking at the Drive in the windows you said. It still has the correct label, but Under size it says "(Free Space Not Available)" and on status it says "Inaccessible". I tired pressing enable but nothing happens.

---

