---
title: "help updating bios"
date: 2012-03-30
forum: General Help
---

### Post by tatmark1 on 2012-03-30
can anyone help me update my bios? hp dv1000 running 10.10

---

### Post by jerome1232 on 2012-03-30
Goto the manufacturers website, many of them provide a way to create bootable media to flash your bios with, the question is, do you really *need* to flash your bios. If all they provide is a windows exe, you can try creating a bootalbe usb of freedos, and use it to run the exe.

[http://www.freedos.org/](http://www.freedos.org/)


(this is coming from a guy who just accidentally flashed his bios with the wrong image, and is waiting for a new bios chip so he can enjoy his computer again)

---

### Post by tatmark1 on 2012-03-30
i did that... i went as far as installling windows 7 on the hd and tried to do it from there and nothing would install keep saying it was not the right bios while it was

---

### Post by Manyette on 2012-03-30
I just updated my BIOS this morning on an ACER machine. You should be able to find a flash rom file in the updates or support sections of the HP site. I have found that a USB stick with DOS is the best and fastest way to do it.

---

### Post by tatmark1 on 2012-03-30
also the reason i want to do this is i am not given the option to boot from usb and i need too

---

### Post by Manyette on 2012-03-30
It seems to me many years ago when I had windoze that they had a win executable that would load a new BIOS update.  If you can't make that work, then you need to talk to their support folks I guess.

---

### Post by jerome1232 on 2012-03-30
> **tatmark1 said:**
> i did that... i went as far as installling windows 7 on the hd and tried to do it from there and nothing would install keep saying it was not the right bios while it was

Your positive it's the right bios? IF you do manage to flash it with the wrong bios you will brick your computer, and you'll have to buy a new flash chip to replace the one you failed to flash.

Try these steps outlined to figure out what bios update you need.

[http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&dlc=en&docname=c00042629&lc=en&product=500515#N313](http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&dlc=en&docname=c00042629&lc=en&product=500515#N313)

---

### Post by spcwingo on 2012-03-30
You can boot from USB if your bios supports booting from a CD...kinda.  ;)  Have a look here for more info.

[http://www.pendrivelinux.com/boot-from-usb-without-bios-support-via-plop-cd/]("http://www.pendrivelinux.com/boot-from-usb-without-bios-support-via-plop-cd/")

[COLOR="Red"]EDIT:[/COLOR]  I just found out that the download link on the above listed site is dead.  Here is an alternate one:

[http://download.plop.at/files/ploplinux/4.2.0/ploplinux-4.2.0-i486/ploplinux-4.2.0-i486.iso]("http://download.plop.at/files/ploplinux/4.2.0/ploplinux-4.2.0-i486/ploplinux-4.2.0-i486.iso")

After booting the CD, at the prompt select "Plop Boot Manager" then on the next screen select "USB".

---

