---
title: "Ekiga 3.25, build OK but no more audio device detected"
date: 2009-07-15
forum: General Help
---

### Post by UranUtan on 2009-07-15
Hi,

What is the reason developers release a program in source code and the end user must go through all the cryptic steps to get it installed? Since I have learned Linux, I have never succeeded to build anything that works.

I tried to compile Ekiga 3.25 on Ubuntu 9.04 x64. Following the instructions here: [http://wiki.ekiga.org/index.php/Compiling_Ekiga](http://wiki.ekiga.org/index.php/Compiling_Ekiga)

It's a big surprise that I could end up getting all the dependencies and finally succeeded the build and could start Ekiga where the about box indicated version 3.2.5.

However, Ekiga is no longer capable of detecting Audio devices. Only the "SILENT(Ekiga/Ekiga)" device is selectable. And of course, the call went through but there is no sound. Previously, Ekiga 3.20 from Ubuntu repository was working OK. And even right now, the sound is working on other media programs such as Rhythmbox.
[COLOR="Red"]
Question 1:[/COLOR] How to tell Ekiga to detect Sound Devices?

[COLOR="Red"]Question 2:[/COLOR] How to remove the manually compiled version Ekiga 3.25 so that I can go to the repository and bring back the working 3.20 version?

EDIT: I removed Ekiga 3.20 using the Package Manager. Then I went to each directory (ekiga-3.2.5, opal-3.6.4, ptlib-2.6.4) and ran **sudo make uninstall**. But Ekiga 3.25 is still present in the Application / Internet Menu. And yet the make uninstalle made a bunch of rm -f ... but how come the program is still alive?

Thanks very much for any help,

---

