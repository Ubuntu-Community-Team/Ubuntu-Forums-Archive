---
title: "Can't find menu.lst on grub after 9.10 installation"
date: 2009-11-16
forum: General Help
---

### Post by eulnuj on 2009-11-16
so i want to edit the boot list but i can't find the menu.lst

---

### Post by coldReactive on 2009-11-16
Did you upgrade or fresh install?

If you fresh installed: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by bodhi.zazen on 2009-11-16
Ubuntu 9.10 uses grub2

[Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2")

---

### Post by capscrew on 2009-11-16
> **bodhi.zazen said:**
> Ubuntu 9.10 uses grub2

[Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2")

I believe that you have a choice if you upgrade to keep Grub-legacy.  I think that is why **coldReactive** asked the question.

---

### Post by coldReactive on 2009-11-16
> **capscrew said:**
> I believe that you have a choice if you upgrade to keep Grub-legacy.  I think that is why **coldReactive** asked the question.

No, the 9.10 upgrade will use grub 1.5 if you upgrade from a lower version. There's no choice.

---

### Post by capscrew on 2009-11-16
> **coldReactive said:**
> No, the 9.10 upgrade will use grub 1.5 if you upgrade from a lower version. There's no choice.

Then [this ]("http://icewalkerz.blogspot.com/2009/10/ubuntu-karmic-changes-between-grub-1x.html")is incorrect.  I don't know.  I'm not disputing your knowledge.  Just want the correct info for myself and others.

Actually, I'm using Hardy.  I will wait for Lucid.  :D

---

### Post by coldReactive on 2009-11-16
> **capscrew said:**
> Then [this ]("http://icewalkerz.blogspot.com/2009/10/ubuntu-karmic-changes-between-grub-1x.html")is incorrect.  I don't know.  I'm not disputing your knowledge.  Just want the correct info for myself and others.

Actually, I'm using Hardy.  I will wait for Lucid.  :D

I can't use hardy on my system as my graphics card won't play nice with it. :(

---

### Post by capscrew on 2009-11-16
> **coldReactive said:**
> I can't use hardy on my system as my graphics card won't play nice with it. :(

Heh, [_**[COLOR="DarkSlateGray"]what about the comment of this blogger who writes that grub-legacy can be retained[/COLOR]**_]("http://icewalkerz.blogspot.com/2009/10/ubuntu-karmic-changes-between-grub-1x.html").

---

### Post by provoko on 2009-11-16
> **eulnuj said:**
> so i want to edit the boot list but i can't find the menu.lst

If you installed 9.10 fresh, you should be editing grub.cfg in /boot/grub.  What files do you have in your /boot/grub folder?

---

### Post by Iowan on 2009-11-16
[This]("https://help.ubuntu.com/community/Grub2#File%20Structure") (from **bodhi.zazen's** link) describes the new file structure.

---

### Post by eulnuj on 2009-11-16
> **coldReactive said:**
> Did you upgrade or fresh install?

If you fresh installed: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
yes i did a clean install and yes i see now.

but in this new grub, the link states that the new menu.lst is not to be edited.

then how do i edit the list?

---

### Post by coldReactive on 2009-11-16
> **eulnuj said:**
> yes i did a clean install and yes i see now.

but in this new grub, the link states that the new menu.lst is not to be edited.

then how do i edit the list?

boot/grub

grub.cfg should be in there. You have to edit it instead.

---

### Post by drs305 on 2009-11-16
> **eulnuj said:**
> yes i did a clean install and yes i see now.

but in this new grub, the link states that the new menu.lst is not to be edited.

then how do i edit the list?

For the basics, this is probably enough information:
[GRUB 2 - 5 Common Tasks]("http://ubuntuforums.org/showthread.php?t=1302743")

See the GRUB2 link in my signature line if you want the full monty.

---

### Post by ranch hand on 2009-11-16
@ drs305
What is wrong with you?  The graphics are much better on blogs.

All you have is information that works, from someone who has not only actually seen grub2, but uses it.

---

