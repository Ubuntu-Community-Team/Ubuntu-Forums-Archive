---
title: "Boot problem"
date: 2012-07-30
forum: General Help
---

### Post by cmckdub on 2012-07-30
I have a boot problem that caues something like this to come up...
```

mount:mounting ..... No such file or directory
mount:mounting ...
mount:mounting ...
....
No init found. Try passing init=bootarg.
BusyBox v1.13....
Enter 'help' for a list of built-in commands.
(initramfs)
```

The help was not overly helpful. I have never seen this before. I understand that I am supposed to run boot info script. The output file is attached.
I was trying to get into 10.04.

---

### Post by cmckdub on 2012-07-30
OK. I see from the output of the "Boot info script that i should also try to run:
```
ubuntu@ubuntu:~$ dmesg | tail
[ 1941.739743] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on lvds encoder (output 1)
[ 1941.739752] [drm] nouveau 0000:01:00.0: Calling LVDS script 6:
[ 1941.739759] [drm] nouveau 0000:01:00.0: 0xC2D1: Parsing digital output script table
[ 2520.356437] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on lvds encoder (output 1)
[ 2520.356445] [drm] nouveau 0000:01:00.0: Calling LVDS script 2:
[ 2520.356453] [drm] nouveau 0000:01:00.0: 0xC332: Parsing digital output script table
[ 2520.487461] [drm] nouveau 0000:01:00.0: Calling LVDS script 5:
[ 2520.487467] [drm] nouveau 0000:01:00.0: 0xC2C2: Parsing digital output script table
[ 2555.560141] usb 4-2: USB disconnect, device number 2
[ 2555.561986] Bluetooth: hci0 urb e94ce3c0 submission failed

```

But I can't see how that helps. I have also found that the live CD will not let me browse into the Hard drive. Did I just have my Hard drive die?:(

---

### Post by cmckdub on 2012-07-30
I got the same information following diffeent advice rather than boot info script, and it does not look good:
```
root@ubuntu:/home/ubuntu# install -d /mnt/radicula
root@ubuntu:/home/ubuntu# mount /dev/sda1 /mnt/radicula
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
Is there anyone with a way out?

---

### Post by ajgreeny on 2012-07-30
So do you actually get to your operating system, or does everything just end with the busybox message?

Has this just started happening and does it follow a crash of your system, ie a hard reboot?

I presume you are running from a live CD or USB at the moment, so from that try running ```
sudo e2fsck /dev/sda1
```This assumes your ubuntu root partition is sda1, which it appears to be from the RESULTS.txt file.

---

### Post by cmckdub on 2012-07-30
Thanks. Yes it only just happened and I became stuck at the Busybox thing.

I have now run 
fsck -r /dev/sda1
and that fixed it. Able to mount and I am now back in. Thanks.:D

---

