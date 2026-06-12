---
title: "Windows XP won't start after I turned the HP Recovery partition into a bootable &quot;usb&quot;"
date: 2010-10-09
forum: General Help
---

### Post by SrAntonio on 2010-10-09
Dear Sirs,

I present to you the summary of my problem: I wanted to make a bootable usb with Ubuntu Netbook remix, but I ended up turning the HP Recovery partition into a bootable usb (because I unintentionally chose that partition instead of the usb device in the formatting utility program options). Now Windows XP won't boot and the system automatically boots up with the Ubuntu Netbook remix options, as if a usb device with the Ubuntu Netbook remix were always connected. 
Now, how do I get Windows XP to start?

Thanks in advance.

---

### Post by oldfred on 2010-10-09
From Ubuntu you can download lilo and install just its boot loader to the MBR as it works identically to windows.

Restore basic windows style boot loader - universe enabled from Ubuntu or liveCD
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

If you have an XP CD you can run fixMBR. 

Booting windows will not let you boot the USB type install that you made to the partition.

---

