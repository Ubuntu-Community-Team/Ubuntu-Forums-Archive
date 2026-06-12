---
title: "visiting places soon..need advice"
date: 2010-05-04
forum: General Help
---

### Post by rahilm on 2010-05-04
I'll be visiting my grandmother's places for a few days. My cousin lives there. He has got a computer on which i installed SuperOS 9.10 last time i visited, which is basically a remastered ubuntu. I don't have a laptop, so i have decided to install ubuntu on my external hard disk but i don't know if it can boot in other people's computer.
Also i need to know how to install Lucid on his computer and the codecs and all since there is no internet access there.

Can i just plainly copy by /usr without problems??

---

### Post by jbrown96 on 2010-05-04
Shared libraries on Linux make installing stuff w/o internet a complete mess. You could try aptoncd. You would also need to copy /lib among other things, not recommended.

---

### Post by uberlinuxnerd on 2010-05-04
> **rahilm said:**
> I'll be visiting my grandmother's places for a few days. My cousin lives there. He has got a computer on which i installed SuperOS 9.10 last time i visited, which is basically a remastered ubuntu. I don't have a laptop, so i have decided to install ubuntu on my external hard disk but i don't know if it can boot in other people's computer.
Also i need to know how to install Lucid on his computer and the codecs and all since there is no internet access there.

Can i just plainly copy by /usr without problems??


[LIST=1]
[*]Plug USB hard disk in
[*]Boot off ubuntu disk
[*]Install to USB disk
[*]Install boot loader to USB disk
[*]Unplug USB disk
[*]Goto Grandmothers house
[*]Plug USB disk in
[*]Boot off USB disk
[/LIST]
Install the restricted-extras for codecs and your good to go.

---

### Post by jbrown96 on 2010-05-04
> **uberlinuxnerd said:**
> [LIST=1]
[*]Plug USB hard disk in
[*]Boot off ubuntu disk
[*]Install to USB disk
[*]Install boot loader to USB disk
[*]Unplug USB disk
[*]Goto Grandmothers house
[*]Plug USB disk in
[*]Boot off USB disk
[/LIST]
Install the restricted-extras for codecs and your good to go.

Makes absolutely no sense...

---

### Post by rahilm on 2010-05-04
> **jbrown96 said:**
> Makes absolutely no sense...
agreed.. btw, i should have made clear that i want to install codecs, vlc on my cousin's computer..

and i tried aptoncd once,.. in times of jaunty if i remember correctly, it didn't work then and i was left with a cd that was completely usless...

i'll keep looking.. plz tell me if anyone has any ideas..
i could test them while installing to my usb hard drive.

---

### Post by jbrown96 on 2010-05-04
As long as you both are running the same architecture (any x86 should be fine-ish, or definitely 64-bit), then you should be fine copying everything from your Ubuntu installation, except /proc, /dev (vitual file systems), /home, /boot, /bin, /var (no need to copy these). 

This may work, but no guarantees. 

You can also try to download all the .debs, but that gets messy from all the dependencies. packages.ubuntu.com can help you find the packages, but you will need to be sure to download all of depenencies, which gets annoying. I would put them all on a USB stick, and then on your friend's computer, run ```
sudo dpkg -i USB/PATH
``` but expect to get errors that will be frustrating.

---

### Post by rahilm on 2010-05-04
I will be trying this: [http://www.omgubuntu.co.uk/2010/05/with-all-new-installing-of-ubuntu-and.html](http://www.omgubuntu.co.uk/2010/05/with-all-new-installing-of-ubuntu-and.html)

i will reply if i get results.

---

### Post by uberlinuxnerd on 2010-05-04
What doesn't make sense... 

Install Ubuntu to the USB disk from the CD. And boot off the USB Disk at your Grandmothers house....

Whats difficult?

---

### Post by rahilm on 2010-05-09
i just arrived here. The bad news is that the hard disk on which i installed ubuntu isn't booting. Grub2 shows error unknown filesystem.. I dont know what 2 do .. I m posting this on expensive mobile gprs so i cant google

---

### Post by rahilm on 2010-05-09
well i am really frustated here... Plz help

---

