---
title: "Error when installing to USB memory stick"
date: 2011-01-18
forum: General Help
---

### Post by Deddly on 2011-01-18
When using the Universal USB Installer and following the instructions according to the Ubuntu web site, I get the following error:

an error () "occurred while executing syslinux. Your USB drive won't be bootable"

There is no number between the brackets and I has no problem with a previous version of Ubuntu netbook remix. Can anyone help?

--
Deddly

---

### Post by Hippytaff on 2011-01-18
How big is the usb stick....have you tried [Unetbootin]("http://unetbootin.sourceforge.net/")
 
Also syslinux is used to boot from FAT filesystems, so is the pendrive formatted to fat?

---

### Post by scott_tiger on 2011-01-18
[FONT=Arial]Click->System->Administrator->Startup disk creater[/FONT] and follow the instructions given there..
See the space in your usb or update ur system once..
read more on syslinux [http://syslinux.zytor.com/wiki/index.php/SYSLINUX](http://syslinux.zytor.com/wiki/index.php/SYSLINUX)

---

### Post by Deddly on 2011-01-18
> **Hippytaff said:**
> How big is the usb stick....have you tried [Unetbootin]("http://unetbootin.sourceforge.net/")
 
Also syslinux is used to boot from FAT filesystems, so is the pendrive formatted to fat?

Hi, I appreciate the help. The UBS stick is 2gb and FAT formatted. I have used this exact USB stick for a previous Ubuntu netbook remix installation. Unetbootin looks good but doesn't seem to support Ubuntu netbook remix.

:(

--
Deddly

---

### Post by Deddly on 2011-01-18
> **scott_tiger said:**
> [FONT=Arial]Click->System->Administrator->Startup disk creater[/FONT] and follow the instructions given there..

Thanks for the information, but I'm running Windows (tragically)...

--
Deddly

---

### Post by Hippytaff on 2011-01-18
I thought 4Gb was the minimum for bootable pendrives?

---

### Post by Deddly on 2011-01-18
> **Hippytaff said:**
> I thought 4Gb was the minimum for bootable pendrives?

It says 2Gb here: [http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)

Those are the instructions I followed to the letter...

---

### Post by Hippytaff on 2011-01-18
> **Deddly said:**
> It says 2Gb here: [http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)
 
Those are the instructions I followed to the letter...
 
Then please ignore my ignorance - have you tried a different pendrive?

---

### Post by Deddly on 2011-01-18
> **Hippytaff said:**
> Then please ignore my ignorance - have you tried a different pendrive?

I only have this one and another identical to it, so I've only been able to try it on this particular one. Do you think it would make a difference?

--
Deddly

---

### Post by Deddly on 2011-01-18
> **Hippytaff said:**
> Then please ignore my ignorance - have you tried a different pendrive?

I only have this one and another identical to it, so I've only been able to try it on this particular one. Do you think it would make a difference?

--
Deddly

---

### Post by Hippytaff on 2011-01-18
It's always worth trying a different one if there's one lying around if it doesn't work properly. Might be worth trying a liveCD and checking that the iso isn't corrupt by checking the [MD5SUM thing ]("https://help.ubuntu.com/community/HowToMD5SUM")(or just try downloading another one if you can't be bothered checking) first

---

