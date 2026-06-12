---
title: "Trouble with 10.04 install : computer freezes"
date: 2010-04-30
forum: General Help
---

### Post by drunkskater on 2010-04-30
I have trouble installing 10.04 on my laptop :

when I boot my computer on the CD, I get a purple screen with two icons. I have to press the Enter key for a menu to appear (but apparently that's normal)

Then I have several choices : Try without installing, install, check disc for defects.... But none of them seems to work : whenever I select one of these options and press Enter, the computer just freezes. The CD start spinning for a few seconds then stops. The light saying that the processor is working stays on forever.

I have an Extensa 5235 laptop with a Intel Celeron 900 processor.

Here is what I did to try to solve the problem so far :

- I thought it might be a problem of CD, althought the ISO image I had downloaded had the right MD5 sum and althought the burning had no problem. So I burned another CD but witht the 32-bit version this time. It seemed to work on another computer...

- I thought it might be a problem of 64-it compatibility. But I'm having exactly the same problems with the 32-bit version.

- I had had trouble getting Karmic on my laptop because of problems of compatibility with the screen resolution ( 1366x768 ) : I had to do "i915.modeset=0" whenever I was starting the computer before I added that command to the GRUB. So, I tried it. I also tried the "nomodeset" mode, but that makes no difference...

So I really don't know what to do. I think my CDs are ok, but how can I be sure ? And anyway does the problem really come from the CD, since it works on another computer ?

---

### Post by sedaturca on 2010-05-03
The same problem.. I downloaded the final Kubuntu Lucid this morning, burned it to a cd-rw at 24k speed;then rebooted the pc to install Kubuntu.. everything was normal here...

when the pc booted with newly-burned Lucid; language selection list came. first I selected Turkish, then entered the option "try without installing" but did not work... the pc frozen just at the time I hit the enter key...the processor led is always on, no signaling.. I had to reboot again...

then pc rebooted again and again, I selected english, then entered the all options "try without installing, install Kubuntu, check cd and memtest"... none of them worked but "boot from the primary harddisk worked only and it passed to the grub list of the Debian Lenny installed on my pc before...

by the way, there was no problem while I was installing Debian last night... everything went well; but what is the problem of Kubuntu? (I should mention that I experienced the same problem when I tried to install Lucid beta about 20 days ago, but solved the problem after some reboot)

so, anybody else experiencing this frustrating problem? I want to enjoy new Kubuntu but I cant... who can help us? my pc is Acer Travelmate 2423 with an intel centrino-m 1.60 processor and 1276 kb of ddr2 ram... please keep me posted if someone solved it... thanks...

---

### Post by dino99 on 2010-05-03
[http://ubuntuforums.org/showthread.php?t=1467891&page=2](http://ubuntuforums.org/showthread.php?t=1467891&page=2) post 14

---

### Post by Taus on 2010-05-03
you might also wanna try acpi=off by hitting F6 (i think) on the boot menu.. worked for me on a few laptops

---

