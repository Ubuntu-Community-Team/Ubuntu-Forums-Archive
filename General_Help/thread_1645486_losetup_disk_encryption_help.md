---
title: "losetup disk encryption help"
date: 2010-12-14
forum: General Help
---

### Post by mrmooge88 on 2010-12-14
In 10.04 I was using the following commands to mount an encrypted disk image:

```
sudo losetup -f
```
Which tells what loop back device block is available
Then I'd type:
```
sudo losetup -e aes /dev/loop0 /home/user/crypt.img
```
and then enter the device's password
```
sudo mount -t ext4 /dev/loop0 /media/crypt
```

I've tried this in 10.10 and it hasn't been working (I can't remember if I did anything in 10.04 to make it work).
I've installed the loop-aes-utils package and restarted my machine. Every time I try the 2nd step, after entering the password I get:
```
ioctl: LOOP_SET_STATUS: Invalid argument, requested cipher or key length (128 bits) not supported by kernel
```
Any ideas? Thanks! :)

---

### Post by mrmooge88 on 2011-03-16
Just in case anyone else runs into this problem. You need to load the cryptoloop module into the kernel.

method 1 (temporary solution)

```
sudo modprobe cryptoloop
```

method 2 (long term solution)
You can have it automatically loaded when the system starts.

```
gksu gedit /etc/modules
```

then add:

cryptoloop

to the end of the file. Save and exit.

---

