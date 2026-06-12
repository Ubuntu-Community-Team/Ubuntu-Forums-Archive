---
title: "Blank screen...but not with external monitor"
date: 2012-05-13
forum: General Help
---

### Post by OllieGab on 2012-05-13
Now I really need some help!
Installing Ubuntu10.04 on my Aspire 5336, no problem, upgraded to 10.10, no problem, upgraded to 10.10; blank screen at boot up. Same with 11.04, 11.10 and now also 12.04.
(I have tried to install 12.04 with a clean install; no difference)
Have tried several things recommended in various forums. I can boot in recovery mode or by using 'i915.modeset=0' as added booting option. But that gives me a totally incorrect resolution and no options to change it.
If I connect an external monitor to my laptop after booting it up normally (with a blank/black screen) it works straight away, with various  resolutions to chose from should I wish to change.
Running 'lspci -v | less' at CL gives:
'Intel Corporation Mobile 4 Series Chipset'
Looking at System Settings --> Details says 'Graphics: unknown'
I've installed the latest intel drivers - as described by someone at a forum - but still no luck.
Help! I can't be the only one with this problem!!??

---

### Post by OllieGab on 2012-05-15
Surely someone must have had a similar problem?!
I've also got Debian installed on the same machine, which doesn't cause me any problem. However, Debian uses kernel 2.35.xx - which works fine for Ubuntu and Mint as well.
Does this mean that whenever Debian's kernel reaches 3.xx or thereabouts; will I get the same problem again?

---

### Post by OllieGab on 2012-05-15
Well, I say solved! I've got it to work but don't really know why, or how...yet!
Tried what was said here
[http://askubuntu.com/questions/28848/what-does-the-kernel-boot-parameter-set-acpi-osi-linux-do]("http://askubuntu.com/questions/28848/what-does-the-kernel-boot-parameter-set-acpi-osi-linux-do")
and it did work on my laptop as well.
Now, I'll look into what this actually** means!**

---

### Post by steeldriver on 2012-05-15
Interesting - thanks for posting that.

I was about to reply that I'd had similar issues on an old Thinkpad with Intel 82830 graphics - which also uses the i915 driver - some 2.x.x kernels worked and some didn't. I didn't find much info on the issue at the time (about a year ago) except that iirc the Xorg  folks insisting that it was a kernel bug and the kernel folks insisting  that it was an Xorg bug. Sorry I can't remember the details. 

It boots fine on my current 11.10 setup (Xubuntu, kernel 3.0.0-19-generic) but the LCD backlight never turns back on when it comes out of sleep mode (and yes I tried all the things suggested on thinkwiki) - I will try those grub parameters. 

[FWIW my understanding of why i915.modeset=0 'kind of' works is that the current Intel driver simply doesn't support anything except KMS - so disabling it forces Xorg to unload the driver and use a fallback VESA driver instead.]

---

