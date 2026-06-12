---
title: "Question about GRUB if I uninstall Ubuntu."
date: 2006-02-14
forum: General Help
---

### Post by Leiki on 2006-02-14
I know that if Ubuntu gets uninstalled, the GRUB loader will look for it and it will say an error every boot-up. I'm wondering if that would happen since I moved my Windows parition to the top of the GRUB list? Since Windows is the first thing it goes to, I'm thinking that I wouldn't have to use my restore discs or whatever and put the boot sector back to normal.

So, basically I'm asking if this is right or not?

---

### Post by heimo on 2006-02-14
That's not correct. Parts of grub are located in /boot/grub directory, including the configuration and 1.5 and 2nd stages. If you remove these, it won't work.

---

### Post by dcstar on 2006-02-14
[QUOTE=Leiki]I know that if Ubuntu gets uninstalled, the GRUB loader will look for it and it will say an error every boot-up. I'm wondering if that would happen since I moved my Windows parition to the top of the GRUB list? Since Windows is the first thing it goes to, I'm thinking that I wouldn't have to use my restore discs or whatever and put the boot sector back to normal.

So, basically I'm asking if this is right or not?[/QUOTE]
Boot Windows with Grub, then "fdisk /mbr" in a cmd shell will restore the Windows booting.

---

### Post by alfonz on 2006-02-14
You could comment out the Linux entries in /boot/grub/menu.lst with "#"

or another option would be if you uninstall Ubuntu, boot into Windows safe mode with command promt and type fixmbr.

---

### Post by alfonz on 2006-02-14
awe he beat me to it... shucks :(

---

### Post by Leiki on 2006-02-14
Wow, thanks for all the help. I decided to keep Ubuntu, because I really like working with the terminal and I heard it's really good with C++ (which I'm studying) so that's good. I know there's another thread here, but I'm curious as to why you guys use linux instead of another OS?

---

### Post by heimo on 2006-02-14
[quote=Leiki]I'm curious as to why you guys use linux instead of another OS?[/quote] 
Initially I had same kind of reasons as you - [gcc]("http://gcc.gnu.org/"). Linux based operating system is excellent platform for programming, but nowadays it's also very good everyday desktop operating system. (And of course very good as a server.) Debian based linux distributions suite me best as I love having several thousand applications available for free - in a matter of minutes, when needed (deb-packaging system rocks). Also it's very open system in many sense. It's _very_ flexible system and runs on _so_ many architectures. Also once you know Linux, you will be able to do many tasks on pretty much any unixlike system - this has helped me to get employed.

EDIT: btw, Leiki, I really like your country (although I don't know much about it) and want to visit at least once sometime in the (hopefully not so) distant future.

---

### Post by nanotube on 2006-02-14
heh, interesting question on os use.
well, depends on what you mean by "another os"
i use it instead of windows cuz i like the "no viruses no crapware" bit and of course having access to a terminal and a bunch of apps in apt is a good plus. 
i use it instead of freebsd/openbsd because it is much better prepared for desktop use, with all the hardware support, etc (bsd's are really great for servers, though).
i use it instead of macos because macs are really expensive. :)
and i guess that about covers it.

---

