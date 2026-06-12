---
title: "Any ideas what to put on a USB that cannot be made into a live USB?"
date: 2011-05-12
forum: General Help
---

### Post by polardude1983 on 2011-05-12
Yeah that's right for some reason this USB I have cannot have a linux OS installed on it don't know why.

So I ask what all files or apps do you suggest me to put on it?

---

### Post by noah++ on 2011-05-12
Do you want help attempting to make it a bootable USB? Otherwise, I'm afraid I don't understand the parameters of your question. It's as if you were to ask us what we thought you should place atop a wooden table. (Whatever you want!)

---

### Post by polardude1983 on 2011-05-12
If somehow i can make it have a linux OS on it would be wonderful.

Right now its just a blank USB and it mounts fine.

If i try to put linux on it either through Unetbootin or the startup disk creator. It installs it but the USB no longer mounts anymore + when i try boot from it, it just bypasses it and goes the the OS on the hard drive.

But when i format the USB it mounts again :/

---

### Post by noah++ on 2011-05-12
It's odd that it should become unmountable after UNetbootin. You insert it, and the icon doesn't appear on your desktop? What model of USB drive is it? What ISO are you using?

---

### Post by wilee-nilee on 2011-05-12
Find the key prompt for getting to the per-session boot from menu, mine is f12.

Unetbootin has a mechanism that stops it from being read after first time use, but will the any next times. Maybe the process even though not booting is kicking this in.

The not read after the first use I think is a insurance policy so people don't reboot to the thumb automatically. Not every user is aware of all the processes, most want plug and play I suspect.

What is the thumb manufacturer and size?

---

### Post by polardude1983 on 2011-05-12
Yeah I insert it and it no longer shows up on my desktop but it does in gparted.

Its a generic usb

I was trying to burn 10.04.2 iso which i know works its the same iso i used to install on this pc.

---

### Post by polardude1983 on 2011-05-12
Though on the USB it has this

dev/sdi Generic Flash Disk 4.9GB
dev/sdi1 5.2 GB Filesystem 4.9GB 4.0GB

Thought it only let me isntall the OS onto sdi1. So when i took it to a different pc. I plug the usb in i wait for the screen to hit Esc, which brings me into the boot options. it says usb detected and it shows only Generic Flash Disk i select that it and just booted right into windows.

---

### Post by wilee-nilee on 2011-05-12
> **polardude1983 said:**
> Yeah I insert it and it no longer shows up on my desktop but it does in gparted.

Its a generic usb

I was trying to burn 10.04.2 iso which i know works its the same iso i used to install on this pc.

If you find that per-session boot key that will give you a answer. The menu comes up there is no countdown you use the arrows to choose the usb and if it will boot it will boot from there. Mine is f12 immediately at powering on, yours may be different.

Make sure you are correct with the the partition in gparted, when loading it, you probably are, just saying.;)

---

### Post by polardude1983 on 2011-05-12
> **wilee-nilee said:**
> If you find that per-session boot key that will give you a answer. The menu comes up there is no countdown you use the arrows to choose the usb and if it will boot it will boot from there. Mine is f12 immediately at powering on, yours may be different.

Make sure you are correct with the the partition in gparted, when loading it, you probably are, just saying.;)

when you say the per session boot key, you mean the whatever key you have to hit for boot options. If that is the post above for the pc i tried it on is Esc. but when it comes up i select the only option Generic Flash Disk. which is technically sdi. But it only lets me install on sdi1.

---

### Post by wilee-nilee on 2011-05-12
> **polardude1983 said:**
> when you say the per session boot key, you mean the whatever key you have to hit for boot options. If that is the post above for the pc i tried it on is Esc. but when it comes up i select the only option Generic Flash Disk. which is technically sdi. But it only lets me install on sdi1.

If your getting this menu outside of the bios then I have done the best I could do.

But if you are confusing the bios boot choice where you move the boot choices up or down like say the cd reader if you had one to the top to boot first, then you haven't got there yet.

So you can access both correct? they act differently in the bios you move the stanzas, in the other  I suggest you move to the choice then hit boot.

---

### Post by mastablasta on 2011-05-12
hmm this might be the solution ot my no boot issue. although it strange that it doens't boot only on one computer. but then again BIOS is different. I need to make complete format and then install it again. then see what happens. because i noticed last time when i made a new ISO of 11.04 that it actualyl never formated the drive and data stayed on the key.

---

### Post by polardude1983 on 2011-05-12
Well i tried to install a live usb on this usb again through the startup disk creator and it was successfull this time. I went to and hit the boot options selected the usb and it sorta actually worked but i got an error

uncompression error

  -- system halted

Any ideas?

---

### Post by C.S.Cameron on 2011-05-12
A couple things you can do with it are format it ext2 and name the partition casper-rw so it can be used for persistence with a Live flash drive.
Install vbox on another Live flash and put the virtual machine on this flash drive.
I mainly use my flash drives to carry around movies as avi's

---

