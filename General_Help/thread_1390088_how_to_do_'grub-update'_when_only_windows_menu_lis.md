---
title: "how to do 'grub-update' when only windows menu list is presented"
date: 2010-01-25
forum: General Help
---

### Post by newway on 2010-01-25
I have a vista/ubuntu 9.10 duel boot laptop. Last week the screen was broken
so it went back to the manufacture. Before that I rename the /etc/grub.d/10_linux
file and ran grub-update so that Grub will only show windows boot menu
(in case it confuses the repairman)

now I have the laptop back and I am eating my own medicine...
how to restore my ubuntu boot menus? I can now only boot into 
windows, although it seems like I can go to my ubuntu partition and change back my grub.cfg (which I did not backup!!!)
but I can't remember the menuentry details.

Is there any way, other than manually change my grub.cfg, 
so that I can boot into ubuntu again?

thx.

---

### Post by amsterdamharu on 2010-01-25
In the menu press c for commandline and issue the following commands:

```

#old grub uses find/menu.lst and the command looks like this:
#find /boot/grub/menu.lst
search /boot/grub/grub.conf
#this could give you something like (hd0,2) use it for the next commands
root (hd0,2)
search (hd0,2)/boot/vmlin(press tab)
#this should give you a number of options of kernels to choose, choose one
#you need to know what partition your root system is on (what is / )
#single means recovery mode, from there you can fix x or just continue booting
#old grub doesn't use linux but kernel, the command looks like this:
#kernel        /boot/vmlinuz-2.6.24-26-generic root=/dev/sda3 ro single
linux        /boot/vmlinuz-2.6.24-26-generic root=/dev/sda3 ro single
&#65283;now choose initrd pressing tab will give you a list of what's in /boot
search (hd0,2)/boot/init(press tab)
initrd        /boot/initrd.img-2.6.24-26-generic
boot

```Now you should be on your way of booting Ubuntu. If not try another root (or leave it out and see if that works)

---

### Post by pbrane on 2010-01-25
Probably the easiest way is from the liveCD. Have a look at this link [https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD"). I think that once you get the root filesystem mounted and chroot into it you should be able to rename that file and run update-grub.

---

### Post by tom4everitt on 2010-01-25
You have to do what you're normally not supposed to do: edit /boot/grub/grub.cfg directly. 

This bypasses the grub-update command. 

Essentially you should just be able to copy-paste the entry in your backed up 10_linux file to the /boot/grub/grub.cfg. (One way to do access the file is by booting from a live cd, mount your ubuntu hard drive, run chmod u+w on the grub.cfg file, and then edit it with gedit.)

Here you can read more about the exact format of grub.cfg:
[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)

EDIT: The previous posters suggestions probably works as well.

---

### Post by pbrane on 2010-01-25
> **tom4everitt said:**
>  run **chmod u+x** on the grub.cfg file, and then edit it with gedit.

I think you meant **chmod u+w** ?

---

### Post by tom4everitt on 2010-01-25
> **pbrane said:**
> I think you meant **chmod u+w** ?

You are quite right. It went a bit fast there. Thanks for the correction!

---

