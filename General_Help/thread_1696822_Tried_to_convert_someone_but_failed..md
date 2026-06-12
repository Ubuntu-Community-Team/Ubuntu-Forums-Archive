---
title: "Tried to convert someone but failed."
date: 2011-02-27
forum: General Help
---

### Post by Metaxa on 2011-02-27
My sister wanted to give Ubuntu a try. She has a Fujitsu laptop, AMD64x2, 2gb ram running 32-bit Vista. I burned her an image of 10.1032bit to try as a live CD. When inserted while windows is active, windows sees it as a blank disc. On my Ubuntu laptop it reads just fine. 

I tried to boot from the live CD, after adjusting the BIOS settings to boot from the CD. It went straight to windows.

Not sure what to try next.

---

### Post by rg4w on 2011-02-28
It's normal that Windows won't recognize a Linux-formatted CD.

As for booting the CD, double-check that BIOS.  Sometimes BIOS settings can be laid out in stupid ways that make it unclear what the boot order is, but chances are once you get that going you'll at least be able to boot from the CD.

That is, if the CD itself is good.  Can you boot from it on your own machine?

---

### Post by Krytarik on 2011-02-28
CDs are usually formatted in ISO9660, not ext* or another linux-type-fs, but check the settings of your burning tool.

And +1 for checking the BIOS, CD and the CD-drive of the target machine.

---

### Post by Metaxa on 2011-02-28
I tried the Live CD 10.10 32bit on my machine and it worked fine. When I start up her machine, I hear the Optical drive accessing the disk. After what feels like 1 minute, the machine begins to boot into windows.

Anything else I should try?


Thanks

---

### Post by Matt__ on 2011-02-28
Try a live usb? as the fujitsu dosnt seem to like the cd.

You will need a 2gb usb drive, plug it in and go to admin/starup disk creator,

Again set it in the bios to boot from usb (and i think you may be able to hit F12 to access boot options too)

If it fails the first time reboot with the usb still in and go via the bios again to make sure its detected and a bootable option.


/edit: what exact model is your sisters laptop?

---

### Post by Krytarik on 2011-02-28
You could try a DVD instead of a CD. A had an issue with the 10.04.1 image a while ago, though at least it tried to boot, but failed during the boot process. After burning the image to a DVD, it booted fine.

---

### Post by Metaxa on 2011-03-01
Your laptop is Lifebook A3210, Fujitsu.

---

### Post by mastablasta on 2011-03-01
sometimes they just don't want to recognise it. oh and 1 Gb flash drive is enough for live disk.
 
i made a USB live with persistency and this USB simply won't get recognised by my computer. while another one works fine. also the USB works well on another computer. so i guess you just have to give a try to more devices.

---

### Post by debd on 2011-03-01
what i did to install ubuntu from usb drive is by creating a netbootin live usb drive. find the software [here]("http://unetbootin.net/").

and then i used PLUP bootmanager which i downloaded from [here]("http://download.plop.at/files/bootmngr/plpgenbtldr-0.8.zip").

you can find the installation tutorial of PLUP on [their site]("http://www.plop.at/en/bootmanager.html")

or just see the text file attached.

PLUP actually forces the sys to boot from an usb drive. After installing, it will 

show the usb drive(if attached while booting) as "Disk 2". select it and voila!

but one word of caution; once grub is installed, dont try to install plup 

bootmngr again. it'll overwrite grub.

---

### Post by Mark Phelps on 2011-03-01
Since your PC reads the CD just fine, and the other PC will not -- that implies a hardware problem with the other optical drive.

Have you tried an audio CD? (Yeah, I know audio on "CD" is so last-century! -- but it's worth a shot.)

Do you have any other data CDs you can try?

---

### Post by Metaxa on 2011-03-01
It appears that the CD drive is the issue. I inserted a DVD, it is a DVD drive, it recognizes it as a DVD, tries to execute player program but fails to read data from disc. 

Some Background of what I am trying to do.

Her Laptop: AMD Turion 64x2, 2bg ram Windows Vista 32bit.

Problem: the machine has come to a crawl performance wise. She mainly streams Netflix, browses the net, facebook and the like. Wanted to give Ubuntu a try because of How my laptop runs compared to her machine.

My Machine: Intel Celeron 1.6 mobile 2.5 bg ram Ubuntu 10.10

From all the responces I have read seems like USB is the way to go. While I was in the BIOS, I saw a mark listing removeable media boot option as being disabled, may need to find the option to replace that.

Should I try the 32bit verion of Ubuntu or 64bit for her machine?


Thanks in advance.

---

### Post by lisati on 2011-03-01
Interesting...... This is more an observation than an actual suggestion of what to try next: all the "DVD" drives I've used have been able to cope with CDs.

---

