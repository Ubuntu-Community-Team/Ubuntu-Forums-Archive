---
title: "Switching casper-rw file?"
date: 2009-08-23
forum: General Help
---

### Post by rogueleader12345 on 2009-08-23
I have a flash drive with Jaunty on it via Create a USB Startup Disk. Being dumb, I moved the casper-rw file off of it and back on it, and now it comes up with the Live CD screen, but when you try to get into ubuntu, it says "Boot Error". So I was wondering if I could save my casper-rw file and reload Jaunty onto the flash drive and just replace the casper-rw file with my own. Basically I'm looking for a way to save my data, so if anyone else knows a way to do it, feel free to let me know.

---

### Post by rogueleader12345 on 2009-08-23
For those wondering *why[I]*[/I] I removed the casper-rw file it's because I have an install on Intrepid that can't connect to the internet and I was trying to get it to recognize my Jaunty as a software source so I could take all the packages I wanted off of my flash drive instead of having to download them all.

---

### Post by juniorkiddo on 2009-08-23
I'm passing by and I'll try to help. I even created an account just for you ^^

2 solutions u can try

SOLUTION 1

[LIST=1]
[*]After your up and running in Linux, insert the flash  drive that contains your **casper-rw** file
[*]Type **dd if=/dev/zero of=casper-rw bs=1M  count=[COLOR=#FF0000]1024[/COLOR]**
(replacing **[COLOR=#FF0000]1024[/COLOR]** with  the "size in MB" you wish to use for saving changes persistently)
[*]Type **[COLOR=#000000]mkfs.ext3 -F casper-rw[/COLOR]**
[*]Copy the new **casper-rw** file to your USB flash  drive
[*]Restart your computer, booting from the USB flash drive and enjoy the expanded storage for saving changes
[/LIST]
SOLUTION 2
[http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/)
download the casper loop file from the bottom of the page and extract it in your thumb drive.

Not sure it can work though..

---

