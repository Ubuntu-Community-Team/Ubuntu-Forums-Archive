---
title: "Help with install from bootable disc"
date: 2012-07-02
forum: General Help
---

### Post by jkatthehelm on 2012-07-02
Hi, I am a first time newbie and have a problem with getting going. I made a bootable disk and set the machine to boot from it. IT finds the disc ok and on screen appears "[FONT=Calibri]Starting Caldera DR-Dos [/FONT]". Then in the next line I get [SIZE=3][FONT=Calibri]"Cannot find an unsued 64K range of upper memory to use for and EMS page frame. Using Frame =NONE."[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Then it boots again, and again....!![/FONT][/SIZE]
[FONT=Calibri][SIZE=3]Any help gratefully received - I am not a computer guy, just another used fed up with slow running and crashing PCs and hoping to give Ubuntu a go, so please feel free to treat me as a know nothing - cos I am when it comes to computers!![/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Thanks anyway if you can help me[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]James[/SIZE][/FONT]

---

### Post by sudodus on 2012-07-02
Welcome to the Ubuntu Forums jkatthehelm :-)

It looks like you are booting a DOS disk, not Ubuntu.

In order to advice what flavour and version of Ubuntu to choose, please give us the specs of your computer, particularly

- CPU
- RAM
- graphics chip or card

There is info about making a boot CD or USB drive in the right column of this web page

[[COLOR="Red"]_http://www.ubuntu.com/download/desktop_[/COLOR]]("http://www.ubuntu.com/download/desktop")

---

### Post by jkatthehelm on 2012-07-02
Hi
It's a T40 IBM, Intel Pentium 1.3ghz, ATI Mobility Radeon 7500, 512 mb.
Interestingly (nor not!) I remade the disc, nowget a screen with a monkey but then this message:
'This kernel requiresthe following features not present on the CPU
pae
Unable to boot - please use a kernel appropriate for your cpu'

---

### Post by jkatthehelm on 2012-07-02
> **jkatthehelm said:**
> Hi
It's a T40 IBM, Intel Pentium 1.3ghz, ATI Mobility Radeon 7500, 512 mb.
Interestingly (nor not!) I remade the disc, nowget a screen with a monkey but then this message:
'This kernel requiresthe following features not present on the CPU
pae
Unable to boot - please use a kernel appropriate for your cpu'
Thanks again for your time!
J

---

### Post by sudodus on 2012-07-02
I have an IBM thinkpad T41, and I have beta-tested Lubuntu on that computer. It is very similar to yours, one critical feature is the non-pae cpu, so you need an OS with non-pae kernel, and Lubuntu 12.04 is such an OS, the smallest and fastest flavour of Ubuntu :-)

So I recommend that you download ***Lubuntu***. If you find it too slow (because of the limited RAM), try ***Knoppix***!

---

### Post by jkatthehelm on 2012-07-02
Many thanks, I shall do as you have suggested  - fingers crossed.
Cheers
JK

---

