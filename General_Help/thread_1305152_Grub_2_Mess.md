---
title: "Grub 2 Mess"
date: 2009-10-29
forum: General Help
---

### Post by vahnx on 2009-10-29
I have a desktop and netbook, all with Leopard, Win7, and Ubuntu. For some reason only the netbook cannot boot Leopard. Why is my Dell Mini 10v on OS X freezing at a blue screen since I installed Karmic? I still hear error sounds when I hit invalid keys so I think Leopard is just not displaying anything. Also, both machines boot verbose but at least my desktop works. Everything was fine with a previous grub which I may have to find a way to revert back to.

---

### Post by hal8000 on 2009-10-29
Have a look here to edit grub2, main file is now grub.cfg

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

Your boot manager may be Darwin if you are using a Mac though, and
you have have to configure Darwin to contro, grub (I'm not a mac  user
though).

---

### Post by twright on 2009-10-29
> **hal8000 said:**
> Have a look here to edit grub2, main file is now grub.cfg

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

Your boot manager may be Darwin if you are using a Mac though, and
you have have to configure Darwin to contro, grub (I'm not a mac  user
though).
You should never edit grub.cfg, instead edit /etc/default/grub

---

### Post by vahnx on 2009-10-29
> **hal8000 said:**
> Have a look here to edit grub2, main file is now grub.cfg

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

Your boot manager may be Darwin if you are using a Mac though, and
you have have to configure Darwin to contro, grub (I'm not a mac  user
though).

I'm using a Dell Mini 10v. Is there some Grub2 GUI editor where I can add/remove entries etc?

---

### Post by twright on 2009-10-29
> **vahnx said:**
> I'm using a Dell Mini 10v. Is there some Grub2 GUI editor where I can add/remove entries etc?
If you are running KDE there is else everything should be automatic.

---

### Post by vahnx on 2009-10-29
> **twright said:**
> If you are running KDE there is else everything should be automatic.

I'm running Karmic with Gnome. It was automatic but I'd like to re-arrange my entries and rename them and it would make sense to have a GUI front-end for this and with a GUI front-end maybe it would fix my OS X verbose boot.

---

### Post by twright on 2009-10-29
> **vahnx said:**
> I'm running Karmic with Gnome. It was automatic but I'd like to re-arrange my entries and rename them and it would make sense to have a GUI front-end for this and with a GUI front-end maybe it would fix my OS X verbose boot.
There is no way to rearrange them. Someone could write a GUI some time though.

---

### Post by seamuso on 2009-10-29
how to re-arrange your entries ... 

/etc/grub.d

the entries are numbered

l0_linux
20_memtest86+
30_os-prober

if you notice the grub menu layout, linux is first, memtest is second, win7 (xp, vista, etc) are last

change the number order ..

10_os-prober
20_linux
30_memtest86+

then 

sudo update-grub

that will re-arrange your entries

note that they are also executable .. if you want to disable them from the menu, 

sudo chmod -x <filename>

---

### Post by vahnx on 2009-10-29
I try renaming any of the files and I get "Misplaces _ in number at eval 1) line 1. But yeah I now understand how the boot order is. Still unsure how to solve the OS X verbose and renaming the entries.

---

