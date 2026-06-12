---
title: "migrating ubuntu 10.10 settings from dual boot hard disk to wubi installation"
date: 2011-06-07
forum: General Help
---

### Post by physio_amer on 2011-06-07
:KS[FONT=Comic Sans MS][SIZE=3] Hello every one.

i started ubuntu from 9.04 now using 10.10 on my laptop. :D

problem started when my laptop motherboard got bad beyond repair,:( and i had installed ubuntu 10.10 on it along with windows 7 (grub, dual boot). now i have pc running windows 7 and installed ubuntu 10.10 using wubi. i want all the settings of my laptop ubuntu 10.10 (programs installed, themes, softwares other configurations etc) to be transferred to this new ubuntu (installed using wubi) on my pc. how to do that? 

i have attached my laptop hard disk to my pc and am able to boot that installation on my pc, but now i have decided to remove laptop hard disk and use the same settings on pc hard disk. step by step guidance would be appreciated!

thanks in advance![/SIZE][/FONT] :)

---

### Post by bcbc on 2011-06-07
Most people want to go the other way - from [Wubi to normal install]("http://ubuntuforums.org/showthread.php?t=1519354"). This is more reliable for long term use. 

Although, in theory, I think it'd be fairly easy to do a 'reverse migration', it might be simpler to manually copy /home and reinstall the programs you have on the old install. Something like what is desribed [here]("http://ubuntuforums.org/showthread.php?t=438591") (look for "[COLOR="Red"]Alternative Instructions[/COLOR]" and follow those).

PS I haven't tried using those alternative instructions

---

### Post by physio_amer on 2011-06-08
> **bcbc said:**
> Most people want to go the other way - from [Wubi to normal install]("http://ubuntuforums.org/showthread.php?t=1519354"). This is more reliable for long term use. 

Although, in theory, I think it'd be fairly easy to do a 'reverse migration', it might be simpler to manually copy /home and reinstall the programs you have on the old install. Something like what is desribed [here]("http://ubuntuforums.org/showthread.php?t=438591") (look for "[COLOR=Red]Alternative Instructions[/COLOR]" and follow those).

PS I haven't tried using those alternative instructions


thank you for prompt response! :KS

will try it and get back soon. hopefully it will work for me. i tried copying /home from my laptop hard disk, but it cannot be pasted in my wubi installed ubuntu. there is no option to paste!

---

### Post by linuxinstalledfromhdd on 2011-06-08
> **physio_amer said:**
> thank you for prompt response! :KS

will try it and get back soon. hopefully it will work for me. i tried copying /home from my laptop hard disk, but it cannot be pasted in my wubi installed ubuntu. there is no option to paste!

You are much better off doing it the other way around..  Install something like 10.10 from a disc like this:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

---

### Post by physio_amer on 2011-06-08
> **linuxinstalledfromhdd said:**
> You are much better off doing it the other way around..  Install something like 10.10 from a disc like this:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

thank you for your reply.
:KS
i dont want to do that, as i have had many problems with ubuntu after installing some necessary drivers and removing unwanted files, which caused grub corruption and could not log on to my pc! and its very difficult for me to learn terminal language and repair things in ubuntu. thats why, i have chosen to keep ubuntu in wubi, and in case of any emergency can use windows to connect internet! :D

can i back up my laptop ubuntu and restore it in wubi installation on pc? i dont wanna lose my fav themes, and configurations which i downloaded using wifi outside, now at home i use mobile to connect to internet which is a slow connection.

---

### Post by bcbc on 2011-06-09
I ran a test today - creating a new root.disk, formatting it, copying an existing non-wubi install onto it, installing lupin-support to it, modifying the fstab. It booted as far as the Gnome login and didn't go any further. I tried a few times to get it going, but trashed it soon after.

So I think that'll be a lot of effort for little gain. The best bet would be to try the method I linked to earlier (using rsync to copy /home and reinstalling programs).

---

### Post by physio_amer on 2011-06-09
> **bcbc said:**
> I ran a test today - creating a new root.disk, formatting it, copying an existing non-wubi install onto it, installing lupin-support to it, modifying the fstab. It booted as far as the Gnome login and didn't go any further. I tried a few times to get it going, but trashed it soon after.

So I think that'll be a lot of effort for little gain. The best bet would be to try the method I linked to earlier (using rsync to copy /home and reinstalling programs).

:KS
thank you for testing it for me. i think i will just install all those packages which i did on laptop again, a lot of pain again! thats what i dont like in ubuntu.  :-x   any ways, yesterday i was trying to upgrade to sabily 11.04 (ubuntu 11.04) but there's a bug, and now i started using terminal to upgrade. :(

---

