---
title: "HP Pavilion DV7-4150ea"
date: 2011-07-12
forum: General Help
---

### Post by [MAG] BamBam on 2011-07-12
Hi all,

I wonder if anybody could possibly help me with my new laptop.

I bought a new HP Pavilion DV7-4150ea about a month ago with windows 7 x64 cough cough, hate windows and would love to be able to get Ubuntu 11.04 working on my laptop or any other version that will be ok.

What happens, when I install either live usb or install to hard drive from DVD, it locks up when I do a restart or shut down, it all seems OK until then.

Could it be the video cards installed on this laptop, as there is two 1 x 1GB ATI Mobility HD 5650 and 1 x Intel HD Graphics. Any help would be great as I love Linux and prefer it to windows every time.

If you need more info then please ask, love to get this working with linux.

Cheers.

---

### Post by wildmanne39 on 2011-07-12
> **'[MAG] BamBam said:**
> Hi all,

I wonder if anybody could possibly help me with my new laptop.

I bought a new HP Pavilion DV7-4150ea about a month ago with windows 7 x64 cough cough, hate windows and would love to be able to get Ubuntu 11.04 working on my laptop or any other version that will be ok.

What happens, when I install either live usb or install to hard drive from DVD, it locks up when I do a restart or shut down, it all seems OK until then.

Could it be the video cards installed on this laptop, as there is two 1 x 1GB ATI Mobility HD 5650 and 1 x Intel HD Graphics. Any help would be great as I love Linux and prefer it to windows every time.

If you need more info then please ask, love to get this working with linux.

Cheers.Hi, yes that is most likely the cause try what this link suggests.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by [MAG] BamBam on 2011-07-13
Hi,

Thank you for your info, I will go away and try the suggestion. fingers crossed.

I will let you know how I get on.

---

### Post by [MAG] BamBam on 2011-07-13
Hi,

Tried with usb ubuntu 11.04 pressed tab key and typed nomodeset. then when loading up I had some sort of error on screen which was very fast so I couldn't see it all. and once in desktop It was the old style desktop like in 10.04.

Everything worked, then tried restart and it locked up just as before.

---

### Post by wildmanne39 on 2011-07-13
> **'[MAG] BamBam said:**
> Hi,

Tried with usb ubuntu 11.04 pressed tab key and typed nomodeset. then when loading up I had some sort of error on screen which was very fast so I couldn't see it all. and once in desktop It was the old style desktop like in 10.04.

Everything worked, then tried restart and it locked up just as before.Hi, that is because it was only set to work once.

You have to follow the directions on that page I gave you to make it persistent.

It is used to first let you boot into ubuntu so you can try to fix what is wrong, which is usually video card. I have seen a lot of people have to disable on of there cards to be able to boot properly.

Enter the nomodeset again when you get to the ubuntu desktop click on additional drivers and see if there is a driver for your ati card in there, you will have to be connected to the internet first.

The reason you get the old desktop is because you have not installed your driver for your video card yet. The intel card should work with out any driver needing to be installed but the other card will need a driver, but I still am not sure you will be able to use them both at the same time.

---

### Post by [MAG] BamBam on 2011-07-14
Hi,

Thanx, will give it a try and let you know.

---

### Post by wildmanne39 on 2011-07-14
> **'[MAG] BamBam said:**
> Hi,

Thanx, will give it a try and let you know.Hi, your welcome!

---

