---
title: "broken bootsplash-plymouth bootsplash not activating"
date: 2010-07-17
forum: General Help
---

### Post by betlog on 2010-07-17
by tinkering with either startupmanager or splashy I have managed to mess up my Lucid 10.04 bootsplash screen.
I have managed to get rid of splashy... but I can't fix my bootsplash.
[IMG]http://imagebin.ca/img/kCQ1AyY.jpg[/IMG]
 Can anyone tell me how to fix this?

I have installed several plymouth themes and  attempted to initialize them ```
sudo update-alternatives --config default.plymouth && sudo update-initramfs -u
``` but none of them actually work afterr i select them and reboot...

---

### Post by wallpaper_thief on 2010-07-28
> **betlog said:**
> by tinkering with either startupmanager or splashy I have managed to mess up my Lucid 10.04 bootsplash screen.
I have managed to get rid of splashy... but I can't fix my bootsplash.

I have installed several plymouth themes and  attempted to initialize them ```
sudo update-alternatives --config default.plymouth && sudo update-initramfs -u
``` but none of them actually work afterr i select them and reboot...

I had that same screen when I was playing with the plymouth bootsplash themes. It turns out this happened to me twice, once because my theme.plymouth tried to access the fedora version of the plymouth theme directory instead of /lib/plymouth/themes

and another time because I tinkered with making it access a Usplash plugin as a plymouth plugin, which it didn't allow.

---

### Post by betlog on 2010-07-28
i see. Well this is just a regular kubuntu install with no other OS, so I'm not sure how it can (in my case) go wrong like you described.
hmm
Iv'e just been ignoring it recently, but I would like to know how to fix it. It's not very comforting when somehting like that appears to be inherently broken and cant even self repair when I go back through the process of setting a theme.

---

### Post by wallpaper_thief on 2010-07-29
> **betlog said:**
> i see. Well this is just a regular kubuntu install with no other OS, so I'm not sure how it can (in my case) go wrong like you described.
hmm
Iv'e just been ignoring it recently, but I would like to know how to fix it. It's not very comforting when somehting like that appears to be inherently broken and cant even self repair when I go back through the process of setting a theme.

well, i've been tinkering with plymouth theme files and I know a little of how they work, so if you want some assistance, can you post the following?: 

1. the contents of /lib/plymouth/themes/default.plymouth
2. the contents of /lib/plymouth/themes directory

---

