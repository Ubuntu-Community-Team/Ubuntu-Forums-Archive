---
title: "busybox and initrfms error"
date: 2010-12-29
forum: General Help
---

### Post by h3llb0y~ on 2010-12-29
[ATTACH]179622[/ATTACH]
This is the error I am getting when I (try to) boot. Im running ubuntu lucid on a Lenovo G550 (about 1 yr old)
I read around on google, and it seems that the grub needs to be updated, but im not sure. A little background about the problem:
>Was working just fine 5 hrs ago.
>I rebooted, and it just showed an error saying /dev/sda1 (this is my root filesystem "/") is mounted in read-only mode, at the same time dropping to command prompt (which is default for me, I prefer CLI).
>Since I use it only in CLI mode, i could not start gdm ("sudo gdm") or start x ("startx")
it said some temporary file could not be created in /tmp
>On another reboot, it gave the above error

any inputs will be appreciated :)

--Aniket

---

### Post by karthick87 on 2010-12-29
Is that WUBI installation??

---

### Post by h3llb0y~ on 2010-12-29
Nope, its a "hard-install". I dont have windows.

---

### Post by karthick87 on 2010-12-29
Boot from a live cd and post the results of [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) with code(#) tags.

---

### Post by h3llb0y~ on 2010-12-29
Not booting into a USB startup disk either (a live CD is not available immediately).
It gets stuck at the login splash with the dots changing colours....
I'll get one ASAP

---

