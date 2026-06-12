---
title: "Quick questions"
date: 2012-05-16
forum: General Help
---

### Post by ryanyeah on 2012-05-16
So I am using Ubuntu 12.04 and have a few questions:

- why doesn't ubuntu mount drives by default, and what is the best way to enable this? 
- what is the best way to schedule programs to start at boot up, as well as schedule commands to execute? I tried added something to crontab with @reboot as the time but it didn't work.
- whenever i plug in my kindle or android device, the files are always read only. How can I change this?

---

### Post by ryanyeah on 2012-05-17
Anyone?

---

### Post by steeldriver on 2012-05-17
- by default, it mounts everything you told it to during the install - if you want to add other devices/partitions later you need to manually edit the /etc/fstab file (or use autofs - which may be a better option depending on what and where the other devices are)

- it should be possible to do stuff at boot time via /etc/rc.local

- I don't know, it would likely be something to do with the mount options for /media/usb

---

### Post by forrestcupp on 2012-05-17
Usually, your Linux partitions will be mounted. So if you happen to be talking about your Windows NTFS partitions, there is a graphical tool in the repos that makes it easy to set those NTFS partitions to be automatically mounted. Either install it by finding it in the Software Center, or open a terminal and type
```
sudo apt-get install ntfs-config
```

---

### Post by timgood on 2012-05-17
Start up programs can be added using Start Up Applications which is accessed by clicking on the cog wheel by your user name, top right.

Hope this helps.

---

### Post by idoitprone on 2012-05-17
> **ryanyeah said:**
> So I am using Ubuntu 12.04 and have a few questions:

- why doesn't ubuntu mount drives by default, and what is the best way to enable this? 
- what is the best way to schedule programs to start at boot up, as well as schedule commands to execute? I tried added something to crontab with @reboot as the time but it didn't work.
- whenever i plug in my kindle or android device, the files are always read only. How can I change this?

 to mount partitions on boot look at these docs [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

