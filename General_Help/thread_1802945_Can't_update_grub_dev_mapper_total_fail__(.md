---
title: "Can't update grub dev mapper total fail : ("
date: 2011-07-12
forum: General Help
---

### Post by cadcam on 2011-07-12
So , i cloned an hdd partition set onto my raid 0 drives.  Promise fastrak 2300 card.  Ubuntu sees the device mapper, and I can do anything with it, but update my grub, thus making it unbootable, which makes me really unhappy.  

grub is installed on the RAID0 set, but i can't update it.  I'm in the live cd (via usb) and I chroot into the ubuntu fs and execute this command, and get these results....

```

ubuntu@ubuntu:~$ sudo chroot /media/f9891dd1-b972-43ca-8827-5411d0e967d1/
root@ubuntu:/# update-grub2
/usr/lib/grub/grub-mkconfig_lib: 38: cannot create /dev/null: Permission denied
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
root@ubuntu:/# exit
exit
ubuntu@ubuntu:~$ 


```

so lame..... can someone help me?

---

### Post by linxuser14 on 2012-01-03
2012-01-03 and nada! Good going y'all.

---

### Post by cadcam on 2012-03-07
hahah, thanks, linuxuser14

---

### Post by cadcam on 2012-08-28
this will have been obseleted by the time it's replied.  it's going to the place of unanswered questions and being shut down.

---

