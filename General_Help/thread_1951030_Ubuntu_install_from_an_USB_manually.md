---
title: "Ubuntu install from an USB manually?"
date: 2012-04-01
forum: General Help
---

### Post by Maxitj on 2012-04-01
Woah i am really disappointed how people do things. I did not find 1 single tutorial how to do this manually. I see load of some usb pendrive programs that do automatically everything in a few secs, and people actually do make tutorials for such things :---). Can anyone of you explain how, lets say unetbootin(i think it's named like this) actually work. I used this to see what will happen, on the first sight seems like it just extracted the iso file on usb(actually to tired to get in deep by myself). My mainly reason why i wanna this cuz i don't like formatting my pendrive second day.

---

### Post by zvacet on 2012-04-02
I think purpose of unetbootin is to put iso image to usb and allow you to run it in live mode or install on HD.

---

### Post by Maxitj on 2012-04-02
> **zvacet said:**
> I think purpose of unetbootin is to put iso image to usb and allow you to run it in live mode or install on HD.

Yeah but allowing to install on hd or running in live mode is a process composed of some things. That's what i need, these things to know how does it fully function

---

### Post by Maxitj on 2012-04-05
Anyone of tha ubuntu pro's? :popcorn:

---

### Post by solocommand on 2012-04-05
If you want to install from a usb stick, you will need to format the flash drive. The usb device needs a boot sector in order to load the installer or the live environment. Just adding the files contained in the ISO is not good enough.

---

### Post by 2F4U on 2012-04-05
I don't know how programs such as unetbooting work, but if you are on a machine running Linux you can simply do

```
dd if=name_of_ubuntu_iso of=/dev/sdc bs=4M
sync
```

This works with Ubuntu 11.10 onwards and assumes that the usb stick is mounted as /dev/sdc.

---

### Post by fiatveritas on 2012-04-05
There's two ways to install Ubuntu on your system: the first assumes that you don't have Ubuntu installed at the beginning, meaning, you need to install the Ubuntu ISO manually or with a program (my favorite, [Universal USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/")); the other way assumes that you're using Ubuntu to make a live USB. In Ubuntu hold down the Windows key while pressing 'a' and search for 'Startup Disk Creator' app in Ubuntu. Startup Disk Creator is a program native Ubuntu that makes your live CD/USB from an ISO image. Hope this helps...

---

### Post by Cheesemill on 2012-04-05
From the Unetbootin home page:

**How does UNetbootin work, and what does it do?**
 For the Live USB creation mode, UNetbootin downloads and extracts an  ISO file to your USB drive, generates an appropriate syslinux config  file, and makes your USB drive bootable using syslinux.

So to do this yourself simply extract the ISO file to your USB drive, then install and configure syslinux using the instructions here:
[http://www.syslinux.org/wiki/index.php/SYSLINUX](http://www.syslinux.org/wiki/index.php/SYSLINUX)

---

### Post by Maxitj on 2012-04-07
Thanks for the info, gotta research some more. Cheesemill i stumbled upon syslinux thingie you talked about also :P

> **2F4U said:**
> I don't know how programs such as unetbooting work, but if you are on a machine running Linux you can simply do

```
dd if=name_of_ubuntu_iso of=/dev/sdc bs=4M
sync
```

This works with Ubuntu 11.10 onwards and assumes that the usb stick is mounted as /dev/sdc.
This comes fine, but in my case im mostly on windows

---

### Post by Cheesemill on 2012-04-07
> **Maxitj said:**
> This comes fine, but in my case im mostly on windows

In that case use dd for Windows:
[http://www.chrysocome.net/dd](http://www.chrysocome.net/dd)

---

