---
title: "DEAD windows need help with unbutu"
date: 2010-01-23
forum: General Help
---

### Post by Galater on 2010-01-23
i have a unbutu live cd i think but it wont start when i put it in computer it just says windows xp professional and recovery what do i do

---

### Post by tjsummers51l on 2010-01-23
Make sure that your computer is set to boot from cd first.

---

### Post by Sef on 2010-01-23
> i have a unbutu live cd i think but it wont start when i put it in computer it just says windows xp professional and recovery what do i do

If you downloaded the Desktop CD, then you have the Live CD.

---

### Post by Galater on 2010-01-23
> **tjsummers51l said:**
> Make sure that your computer is set to boot from cd first.
 i do but it still goes to the windows xp thing

---

### Post by mick222 on 2010-01-23
you need to go into the bios and change the boot order to boot from cd dvd. On my computer i can press f11 and choose from there as well but other computers use different keys for this.

---

### Post by Ordes on 2010-01-23
did the cd work in the first place? Did u try it after u burned it?

I had a friend who downloaded the iso burned it and couldnt boot the CD, becuase he burned the ISO&#12288;as data, not as an Image. Means if you u look at the cd you will just see xxx.iso.

Beside that there could be a lot of other "burning" errors that just messed up your CD.

It also could be that your BIOS is not set to boot from CD first. Also check the boot hierachry order.

You have any other boot disks you could try? If they dont work either, than u know its either BIOS or CD-ROM. If they boot up your problem is on the CD.

---

### Post by Galater on 2010-01-23
> **Ordes said:**
> did the cd work in the first place? Did u try it after u burned it?
 
I had a friend who downloaded the iso burned it and couldnt boot the CD, becuase he burned the ISO&#12288;as data, not as an Image. Means if you u look at the cd you will just see xxx.iso.
 
Beside that there could be a lot of other "burning" errors that just messed up your CD.
 
It also could be that your BIOS is not set to boot from CD first. Also check the boot hierachry order.
 
You have any other boot disks you could try? If they dont work either, than u know its either BIOS or CD-ROM. If they boot up your problem is on the CD.
 yea i tried the cd on my laptop and it worked

---

### Post by d3v1150m471c on 2010-01-23
...are you putting in the windows cd or the ubuntu cd? Secondly, you have to set your bios menu to boot from cd.

---

### Post by Jackzor on 2010-01-23
When you first start your computer there should be some option and one of them will say enter setup or bios. You need to change the boot order. the key to press will be something like delete or f2 f12 something like that

---

### Post by Ordes on 2010-01-23
when the cd works on other machines. than the problem is either the BIOS settings or the CD-ROM.

As said before,
check if 
1) Bios boot cd is enabled
2) check boot hierarchy; sometimes the cd is below the hdd, so it will boot first from hdd instead of cd, change this so CD is first.
3) using boot setup.. mostly by f2, f8, f12

if its still not booting, there might be a hardware problem with your CD-ROM, or mobo...

---

### Post by Jackzor on 2010-01-23
If anything you can unplug your hard drive and try booting to the cd.

Does it boot when you do not have a hard drive?

---

### Post by Galater on 2010-01-23
> **Jackzor said:**
> If anything you can unplug your hard drive and try booting to the cd.
 
Does it boot when you do not have a hard drive?
 it will just say disk error  and it wont start
 
 
 
> **Ordes said:**
> when the cd works on other machines. than the problem is either the BIOS settings or the CD-ROM.
 
As said before,
check if 
1) Bios boot cd is enabled
2) check boot hierarchy; sometimes the cd is below the hdd, so it will boot first from hdd instead of cd, change this so CD is first.
3) using boot setup.. mostly by f2, f8, f12
 
if its still not booting, there might be a hardware problem with your CD-ROM, or mobo...
i put boot from cd first
and that didnt work 
i think there it is  a hardware problem because i did all that.Is there a way to fix it

---

### Post by Ordes on 2010-01-24
mhm...might be the cd-rom than.. 

but still weired. your mobo does find the cd-rom otherwise you couldnt see in your bios settings. on the hand it wont boot from the rom and keeps trying the hdd...

can your mobo boot from usb? u could put the image on a usb and try to boot from there...

load up ubu on your laptop, the live one is ok too, in system > administration > usb startup creator.. use this tool to put the iso on a usb..

---

### Post by Galater on 2010-01-26
cant load from usb

---

### Post by Ordes on 2010-01-26
??

can u be more specific..

like my motherboard cannot load from usb > it does not has the function

or,
it fails to load from usb?

----
if it fails to load, check if you enabled usb boot, in bios. and also that when the usb is plugged in u put it on top of the booting hierarchy. Some mobos need to load over the bios boot menu, one of mine triggers this with f8....
----
if u did all the above and still cannot load, than probably your mobo has problems. As it does not load from CD nor USB....
----
Just curious, what trashed your windows in the first place? Perhaps its not even the problem of windows.....but hardware sided

---

### Post by Galater on 2010-02-08
it fails to load

---

### Post by Galater on 2010-02-26
if i get a new hardrive and put ubuntu on it will my comp work

---

### Post by Galater on 2010-04-09
Well i fixed my comp and have ubuntu installed now

---

