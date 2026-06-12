---
title: "Mount dvd in chroot enviroment"
date: 2010-02-13
forum: General Help
---

### Post by Jenkins1 on 2010-02-13
Hi,

I have discovered the fun of custom ubuntu install/live cds. I can create one following [http://www.debuntu.org/how-to-customize-your-ubuntu-live-cd](http://www.debuntu.org/how-to-customize-your-ubuntu-live-cd) or using Ubuntu customization kit. I can download packages like skype using wget. 

I would like to be able to install Matlab which I have on dvd and have to use for uni. How do I mount the dvd in the chroot enviroment? Or how can i copy the files from the dvd to the chroot environment?

---

### Post by sisco311 on 2010-02-13
[list]
[*]mount the /dev directory & mount the dvd in the chroot environment.

in the host run:
```
sudo mount --bind /dev ~/livecd/custom/dev
sudo mount --bind /dev/pts ~/livecd/custom/dev/pts
```

in the chroot environment run:
```

mkdir /media/dvd
mount -o loop /dev/dvd /media/dvd

```


[*]or mount the dvd in the host  &  bind it:

in the host run:
```

sudo mkdir /media/dvd
sudo mount -o loop /dev/dvd /media/dvd
sudo mkdir ~/livecd/custom/media/dvd
sudo mount --bind /media/dvd ~/livecd/custom/media/dvd
```  

[/list]

---

### Post by Jenkins1 on 2010-02-14
Thanks sisco311 silly question how do i unmount it? I don't think I was un-mounting right.

---

### Post by sisco311 on 2010-02-14
> **Jenkins1 said:**
> Thanks sisco311 silly question how do i unmount it? I don't think I was un-mounting right.

You're welcome!

You can unmount the cd/dvd with the umount command or eject it:
```
sudo umount /dev/dvd
sudo eject /dev/dvd
```
Instead of the device name you can use the mount point as well:
```
sudo umount /media/dvd
sudo eject /media/dvd
```

---

### Post by Jenkins1 on 2010-02-15
Thanks sisco311

---

