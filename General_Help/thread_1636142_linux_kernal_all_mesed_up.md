---
title: "linux kernal all mesed up"
date: 2010-12-02
forum: General Help
---

### Post by stber321 on 2010-12-02
i was running apt-get dist-upgrade and my computer turned off in the middle of it now i can boot into ubuntu but i can not type and the mouse will not move. if i try to boot into the recovory console it stops booting and  will not take keyboard input. is there a live CD i can use to reinstall the linux kernel?

also ubuntu is in low grafics mode(the gnome do window looks weird)

and compiz will not start on start up:sad::sad::sad:

---

### Post by HiImTye on 2010-12-02
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by stber321 on 2010-12-04
> **HiImTye said:**
> [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
I do not want to reinstall ubuntu I want to fix it I found ubuntu rescue remix and have a live cd but i do not know how to reinstall the Linux kernel from the live cd

---

### Post by questioned on 2010-12-04
My Kernel is also messed up. I have linux mint 10 32-bit. Since I booted linux the first time, there was a kernel error message on boot. This message disappeared, but still the kernel is messed up. I'm stuck too :(

---

### Post by stber321 on 2010-12-15
> **questioned said:**
> My Kernel is also messed up. I have linux mint 10 32-bit. Since I booted linux the first time, there was a kernel error message on boot. This message disappeared, but still the kernel is messed up. I'm stuck too :(

i figured it out:
1. create a live cd of ubuntu rescue remix
if you want to attempt to fix the kernel try: [http://www.ubuntudoctor.com/content/blog/02/Re-Install-a-Linux-Kernel](http://www.ubuntudoctor.com/content/blog/02/Re-Install-a-Linux-Kernel)

if that does not work i recommend you mount the partition using:
```

fdisk -l      //find the linux partition to mount (in this example i use /dev/sda1)
mkdir /mnt/os
mount /dev/sda1 /mnt/os

```then go ahead mount a usb device (or some other storage device)

```

fdisk -l      //find the partition to mount (in this example i use /dev/sdb1)
mkdir /mnt/usb
mount /dev/sdb1 /mnt/usb
cd /mnt/usb

```than back up everything
```
tar czvf osbackup.tar.gz /mnt/os/*
```

then reinstall or change to another distro (i changed to fedora and had some driver isues becouse there were no free drivers for my wireless card, so i went to Linux Mint and i love it)

---

