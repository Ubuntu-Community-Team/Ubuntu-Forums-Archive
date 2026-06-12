---
title: "modify menu grub"
date: 2010-02-08
forum: General Help
---

### Post by davidtuti on 2010-02-08
Hi,
Recently I've installed grub2 1.98 experimental in my kubuntu 9.10.
I have problems to boot because it gives ma error in ubuntu and in windows.

I've saw what is the problem that I have, when I am in the grub menu I must modify a line, pressing 'e' and then I have to boot with Ctrl+X. The problem is that every time I boot I have to do this, I would like to modify the menu to don't have to do this every time I boot.

Any help? 
Many thanks and sorry for my english!

---

### Post by captainpotato on 2010-02-08
Just been through the same thing as you - this is the page that I found helpful:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by lordskid on 2010-03-03
did you ever get to solve your problem...

I might be having the same problems as you. When I boot, grub2 experimental from fzielcke's ppa, everything is okay, the theme comes out nice. but when I select the entry I want to boot. it gives me an error stating I need to load a kernel first... so I press e...
press the arrow down key until it goes to the last character of the last line I noticed that generic is missing a 'c'

so I put the missing c and press ctrl-x and everything is fine.

as a workaround I manually edited my grub.cfg and put an extra c after the last lines of every menuentry. such that

initrd.gz(version number)-generic becomes 
initrd.gz(version number_-genericc

I am still trying to find out what is the exact cause of the problem but I believe it has something to do with the graphics card limitation...

are you by any chance using a netbook with a max 640x480 screen in console mode?

---

