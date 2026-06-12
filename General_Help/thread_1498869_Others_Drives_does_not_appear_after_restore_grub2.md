---
title: "Others Drives does not appear after restore grub2"
date: 2010-06-01
forum: General Help
---

### Post by xtreme1 on 2010-06-01
I have installed Windows XP and Ubuntu 10.04 in my pc , when I installed a new windows xp the grub deleted, so from ubuntu 9.10 live cd i tried this to restore grub
```

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# mount /dev/sda7 /mnt
root@ubuntu:~# grub-install --root-directory=/mnt/ /dev/sda
Installation finished. No error reported.
This is the contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)    /dev/fd0
(hd0)    /dev/sda
root@ubuntu:~# 

```then restarted the computer, after that when opened ubuntu 10.04 i just saw 3 drives in my computer !!!

but i have 5 drives where's the other drives??? they doesn't appear

but they appears in windows xp
thanks

---

### Post by dino99 on 2010-06-01
sudo grub-mkconfig
sudo update-grub

mountmanager deals with the partitions and devices

---

### Post by xtreme1 on 2010-06-01
> **dino99 said:**
> sudo grub-mkconfig
sudo update-grub

mountmanager deals with the partitions and devices
make these commands from live cd or from my ubuntu 10.04 ?
i tried them from ubuntu live cd but that is what happend

```

ubuntu@ubuntu:~$ sudo grub-mkconfig
grub-probe: error: cannot find a device for /.

ubuntu@ubuntu:~$ sudo update-grub
grub-probe: error: cannot find a device for /.

ubuntu@ubuntu:~$ 


```

---

### Post by xtreme1 on 2010-06-01
i tried these commands in ubuntu 10.04 but drives doesn't appears too :(

---

### Post by dino99 on 2010-06-01
seem you have not defined a boot partition when you made them

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by xtreme1 on 2010-06-01
brother, they were all appears, but after the new restore of grub2 they're now doesn't appears
thx

---

