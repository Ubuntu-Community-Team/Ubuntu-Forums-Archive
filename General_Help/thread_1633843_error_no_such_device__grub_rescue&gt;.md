---
title: "error: no such device :????????????? grub rescue&gt;"
date: 2010-11-29
forum: General Help
---

### Post by themanfromiac on 2010-11-29
Hi Everyone,
I have recently decided to try out Ubuntu(Lucid Lynx) using wubi. Everything was absolutely superb....and realising that I have a lot to learn and looking forward to it.
Everything was fine until I updated and ticked 2 boxes for updating grub and restarted and couldn't boot into anything. I have xp on 80gb 2.6 celeron, and Ubuntu loaded through wubi on 320 gb external hard drive.

error: no such device:???????????????????
grub rescue>

I am a total novice and appreciate all the help I can possibly get.

It may seem a little slow for me to put to the test your responses, because I will have to disconnect the PC that I am using and use those connections on the 2.6.
This one I am using at the moment is 400hz p3

Thanks in advance

---

### Post by bcbc on 2010-11-29
You need to reinstall the windows bootloader. Only the bootloader.

Boot a windows repair cd to a command prompt and run
fixmbr (on XP)
or
bootrec.exe /fixmbr (on vista/7)

[https://bugs.launchpad.net/wubi/+bug/610898](https://bugs.launchpad.net/wubi/+bug/610898)

---

### Post by themanfromiac on 2010-12-01
> **bcbc said:**
> You need to reinstall the windows bootloader. Only the bootloader.

Boot a windows repair cd to a command prompt and run
fixmbr (on XP)
or
bootrec.exe /fixmbr (on vista/7)

[https://bugs.launchpad.net/wubi/+bug/610898](https://bugs.launchpad.net/wubi/+bug/610898)
Hi bcbc,

Will try this  but having burning problems at the moment.

Will post reply as soon as is possible

Thanks

---

### Post by themanfromiac on 2010-12-08
Thanks again bcbc,

Absolutely spot on. It was a lot easier than I was expecting.

Thankyou

---

