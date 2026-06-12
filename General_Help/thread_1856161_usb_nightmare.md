---
title: "usb nightmare"
date: 2011-10-07
forum: General Help
---

### Post by 1rancid11 on 2011-10-07
ok Im going to keep this simple. Please tell me what you need to help me.
Usb automatically mounts(any kind mp3 players drives etc..)
The problem is they are always locked and cant add add or remove info.
It always tells me im not the owner. I have read articles and tried everything suggested.
Please let me know the details you need to help me. thanks jay

---

### Post by coffeecat on 2011-10-07
Let's investigate. Plug in an mp3 player or USB flash drive, anything that mounts but gives you a permissions error. Now open a terminal and post the output of this command:

```
mount
```

You'll need to highlight the output with the mouse, right-click to copy and then paste it into your post.

---

### Post by 1rancid11 on 2011-10-08
> **coffeecat said:**
> Let's investigate. Plug in an mp3 player or USB flash drive, anything that mounts but gives you a permissions error. Now open a terminal and post the output of this command:

```
mount
```You'll need to highlight the output with the mouse, right-click to copy and then paste it into your post.

/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=600)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/j/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=j)
gvfs-fuse-daemon on /home/jason/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jason)
/dev/sdb on /media/usb0 type vfat (rw,noexec,nodev,sync,noatime,nodiratime)

---

### Post by 1rancid11 on 2011-10-08
Error opening file '/media/usb0/new file': Permission denied
This is the error im getting. Thanks jason

---

### Post by coffeecat on 2011-10-08
> **1rancid11 said:**
> /dev/sdb on [COLOR="Red"]/media/usb0[/COLOR] type vfat (rw,noexec,nodev,sync,noatime,nodiratime)

> **1rancid11 said:**
> Error opening file '[COLOR="Red"]/media/usb0/[/COLOR]new file': Permission denied

You've installed the application usbmount, haven't you? Uninstall it and uninstall any other applications that you've installed to "help" with mounting USB drives. The app usbmount is designed for GUI-less systems. It interferes with the usb automounting functionality built in to the gnome desktop of Ubuntu. USB mounting works out of the box in Ubuntu - you don't need to install anything extra.

---

### Post by 1rancid11 on 2011-10-08
Im new to this forum thing so as soon as i figure out how to close as solved i am. You are a genius. Thanks

---

### Post by jazzon on 2011-10-08
mark as solved with the "Thread Tools" link near top post.

---

