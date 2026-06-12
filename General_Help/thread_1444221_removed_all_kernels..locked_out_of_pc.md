---
title: "removed all kernels..locked out of pc"
date: 2010-04-01
forum: General Help
---

### Post by arclinux on 2010-04-01
i accidently removed all my kernels instead of just old ones.
and realised thsis on my next reboot.
what to do now..
tried using live cd. mounted / and /home and /boot 
but sudo didnt worked
any suggestions

---

### Post by Chronon on 2010-04-01
You should be able to do a chroot and install ubuntu-desktop.

```
NAME
       chroot - run command or interactive shell with special root directory

SYNOPSIS
       chroot NEWROOT [COMMAND [ARG]...]
       chroot OPTION

```

Here's a post describing doing this in Knoppix, but you should be able to just use the Ubuntu LiveCD too.
[http://ubuntuforums.org/showpost.php?p=903240&postcount=1](http://ubuntuforums.org/showpost.php?p=903240&postcount=1)

---

### Post by oldfred on 2010-04-01
Desktop is the window manager, you want the kernels

Of course you must first know what partition you want to mount, in this example I'm using sda3:

sudo mount /dev/sda3 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf #(may or may not be necessary to establish an internet connection)
sudo chroot /mnt
#Then run whatever other commands needed - no sudo needed (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).

apt-get update
sudo apt-get update && sudo apt-get upgrade  #this updates everything
apt-get install linux-image-generic 
apt-get dist-upgrade     #would upgrade you to the latest kernel in the repositories

#When done:
exit
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt

---

### Post by Chronon on 2010-04-01
Thanks for the detailed answer.  I guess I wrongly assumed that ubuntu-desktop would pull in a generic kernel.

---

### Post by john newbuntu on 2010-04-01
Ahh golden lessons: Never pull the rug from under your feet.

---

### Post by no2498 on 2010-04-01
i do not get rid of any of them
if i get a bad update restart push esc down arrow go down 2 or 3
play a day or 2 restart im good as new
i see it as a back up
let the system have time to adjust

---

