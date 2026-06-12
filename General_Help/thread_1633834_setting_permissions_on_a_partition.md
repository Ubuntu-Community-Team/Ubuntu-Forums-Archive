---
title: "setting permissions on a partition"
date: 2010-11-29
forum: General Help
---

### Post by steveredshaw on 2010-11-29
I have just formatted a partition that had contained a windows OS, it is now formatted to ext4 and is dev/sda1


dev/sda2 contains my Ubuntu OS and all files


although the empty partition shows up in Nautilus I cannot write to it as it is owned by root


I have done some research on changing the permissions on this, but am none the wiser!! eg [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)


this article contains this warning


[IMG]https://help.ubuntu.com/community/IconsPage?action=AttachFile&do=get&target=IconWarning3.png[/IMG]
    **Enabling the root account is rarely  necessary.  Almost everything you need to do as administrator of an  Ubuntu system can be done via sudo or gksudo. If you really need a  persistent root login, the best alternative is to simulate a root login  shell using the following command...**


I cannot find gksudo and do not know what commands to use in the terminal to achieve my goal. I am in totally unfamiliar territory here, and need some fairly simple  explanation and guidance to be able to claim my empty partition so I can  read from and write to it....

---

### Post by TeoBigusGeekus on 2010-11-29
Try
```
sudo chown yourusername /dev/sda1
```

---

### Post by steveredshaw on 2010-11-29
> **TeoBigusGeekus said:**
> Try
```
sudo chown yourusername /dev/sda1
```

nope, this doesn't change anything!!

---

### Post by TeoBigusGeekus on 2010-11-29
Have you added the partition to fstab?

---

### Post by steveredshaw on 2010-11-30
> **TeoBigusGeekus said:**
> Have you added the partition to fstab?

no I haven't added the partition to fstab, I have had a look around and come up with this

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
but the information is a bit above my level of understanding!

I have also tried to change settings for that partition with the Storage Device Manager, but when I try to write files to the partition it is still telling me that permission is denied

---

### Post by TeoBigusGeekus on 2010-11-30
Unmount the device.

Create a folder in media where the hd will be mounted.
```
sudo mkdir /media/disk
```

Edit your fstab file
```
gksu gedit /etc/fstab
```
and add this line
```
/dev/sda1 /media/disk ext4 relatime 0 2
```
at the end of it.

Reboot and give
```
sudo chown yourusername /media/disk
```

Post back with results.

---

### Post by WorMzy on 2010-11-30
You don't need to add it to fstab; if you've manually mounted it, just open a terminal and run ```
sudo chown -R <USERNAME>:<GROUP> /path/to/mountpoint
```
e.g.
```
sudo chown -R steve:steve /media/storage
```

Of course, this only works for partitions formatted as a filesystem which supports linux permissions. NTFS and FAT both need an fstab entry with the permissions declared in it.

---

### Post by steveredshaw on 2010-11-30
thanks so much, I looked in the media/ folder and found the partition had a directory there - media/sda1

so this did the trick - 
sudo chown -R steve:steve /media/sda1

---

