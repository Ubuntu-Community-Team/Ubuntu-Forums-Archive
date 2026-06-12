---
title: "How can i manually create grub 1.5"
date: 2010-02-07
forum: General Help
---

### Post by aviramof on 2010-02-07
i want to create grub 1.5 for ubuntu 10.04 because what ever they got there doesn't work.
 
how can i do that?
 
thanks in advance.

---

### Post by jocko on 2010-02-07
> **aviramof said:**
> i want to create grub 1.5 for ubuntu 10.04 because what ever they got there doesn't work.
 
how can i do that?
 
thanks in advance.
There is nothing called "grub 1.5". Older ubuntu versions used grub 1, and newer versions use grub 2. Grub 1.5 has never existed.
Why do you keep posting new threads about this? People are already trying to help you in your other 3 threads about this same problem (and since you are using lucid lynx, which is still in alpha, you should post in the 10.04 development section).
But to make it simple for you, I repeat the instructions you got in a link in at least one of the other threads:

1. Boot from a live cd.
2. chroot into your installed ubuntu. I assume you have ubuntu on the first partition on your first hard drive (/dev/[COLOR=Blue]sda1[/COLOR]) and your computer's bios is set to boot from the first hard drive (/dev/[COLOR=Blue]sda[/COLOR]). If you have ubuntu on another partition you have to change the commands accordingly:```
sudo mkdir /media/[COLOR=Blue]sda1[/COLOR]
sudo mount /dev/[COLOR=Blue]sda1[/COLOR] /media[COLOR=Blue]/sda1[/COLOR]
sudo mount --bind /dev/ /media/[COLOR=Blue]sda1[/COLOR]/dev
sudo mount --bind /dev/pts /media/[COLOR=Blue]sda1[/COLOR]/dev/pts
sudo mount -t proc none /media/[COLOR=Blue]sda1[/COLOR]/proc
sudo mount -t sysfs none /media/[COLOR=Blue]sda1[/COLOR]/sys
sudo mount -o bind /etc/resolv.conf /media/[COLOR=Blue]sda1[/COLOR]/etc/resolv.conf
sudo chroot /media/[COLOR=Blue]sda1[/COLOR]
```3. Make sure grub 2 is installed:```
apt-get install grub-pc
```4. Install grub 2 in the mbr of your first hard drive and update the grub configuration:```
grub-install /dev/[COLOR=Blue]sda[/COLOR]
update-grub
```5. Exit the chroot:```

exit
```6. Reboot.

---

### Post by aviramof on 2010-02-07
that more like it sending me to countless command didn't helped very much i hope this will and maybe you haven't noticed but no one in the developers forum care to help me in my thread there.
 
but now let me ask you something my first HD is the one with windows 7 and ubuntu installer recognize it as /dev/sdb1 and ubuntu is installed on 
my second drive and ubuntu installer recognize it as /dev/sda1 do is it ok because ubuntu 8.10 didn't have a problem with that with grub 1 is it 
possible that the problem is that grub 2 doesn't like it?and if so what can i do about it?

---

### Post by aviramof on 2010-02-07
thanks for the help but it just doesn't work nothing does i'll just wait for the final version or install a diffrent linux edition or what ever it's called.

---

