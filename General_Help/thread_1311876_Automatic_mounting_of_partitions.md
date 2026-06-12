---
title: "Automatic mounting of partitions"
date: 2009-11-02
forum: General Help
---

### Post by Pingster on 2009-11-02
On my triple boot system I have some partitions that I want read/write access to at boot from Ubuntu 9.10.  Originally I had to type in my password to mount the drives so I installed pysdm, following the instructions [here]("http://dizzietech.wordpress.com/2009/10/19/pysdm-a-user-friendly-application-to-automount-your-disk-in-ubuntu/") to make them mount at boot.  I keep unchecking the **Mount file system in read-only mode**, but I still can't edit or delete anything on the drives.  Another odd thing is that when I tell Storage Device Manager to unmount the drive I can still access the drive (still no writing to it, though).

Can anyone tell me how to auto-mount the drives at boot, retaining read/write permissions?

In case it's helpful to know, I'm a power Windows user but just recently getting into Linux.

---

### Post by Zoot7 on 2009-11-02
Can you post the output of 
```
sudo fdisk -l
```
and 
```
cat /etc/fstab
```

---

### Post by Matt__ on 2009-11-02
Is it windows partitions you are looking at?
If so you could just install NTFS config tool from the add/remove menu.[more info]("http://www.ntfs-3g.org/")
or you may wish to use the terminal [Like This]("http://ubuntuforums.org/showthread.php?t=217009")

enable write support when prompted...very simple and rw access.
They also show up with their original names as per windows rather than sda/whatever.

---

### Post by Pingster on 2009-11-03
Thank you for posting such valuable information for me.  I'm not sure what I did, but I kept playing around with pysdm and got the drives to mount at boot with write permissions.  Your post will be very helpful, I'm sure, when something goes wrong again.

---

### Post by albannach1 on 2009-11-03
I had a similar problem recently. I just added to partitions and drives that I wanted to be auto mounted into the fstab file. There are options in fstab that allow you to specify how you want to mount the drive (read/write permissions, etc.)

This link was very helpful in setting up my fstab:
[http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html")

---

