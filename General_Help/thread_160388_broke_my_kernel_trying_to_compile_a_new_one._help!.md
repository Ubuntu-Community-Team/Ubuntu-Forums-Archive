---
title: "broke my kernel trying to compile a new one. help!"
date: 2006-04-14
forum: General Help
---

### Post by JacksonL on 2006-04-14
Hey guys. I was trying to compile my own kernel when I encountered a series of problems that I tried to solve on my own. That in itself was a bad idea because I'm really new at Linux and I know pretty much nothing. Anyway, I ended up completely screwing up my /usr/src/ and I was wondering if there's some way to just reinstall the default ubuntu kernel so I can fix this huge mess. thanks!

---

### Post by az on 2006-04-14
[QUOTE=JacksonL]Hey guys. I was trying to compile my own kernel when I encountered a series of problems that I tried to solve on my own. That in itself was a bad idea because I'm really new at Linux and I know pretty much nothing. Anyway, I ended up completely screwing up my /usr/src/ and I was wondering if there's some way to just reinstall the default ubuntu kernel so I can fix this huge mess. thanks![/QUOTE]
By default, there is nothing in /usr/src

Can you boot your system6?  If not, do you know how to boot the installer in rescue mode and chroot into your ubuntu partition?

From there, run

sudo apt-get install --reinstall linux-image-2.6.12-9-386 

(or whatever version of kernel you had running)

---

### Post by JacksonL on 2006-04-14
thanks. that did *something*. now after GRUB loads it says

Uncompressing Linux... Ok, booting the kernel.
[4294670.598000] Kernel panic - not syncing: VFS: Unable to mount root fs (it cuts off here because the resolution is messed up)
nown-block(0,0)
[4294670.598000]

---

### Post by JacksonL on 2006-04-14
nevermind about that last problem. I fixed it.
but my graphics drivers are broken. I'm using an nvidia 6800GS. I think I might have broken my ndiswrapper and nvidia-kernel modules because I tried to compile them with my new kernel but of course that didn't work. I guess I should just reinstall them via apt. no?

---

### Post by Ramses de Norre on 2006-04-14
That would be the easiest solution I think, yes.
Use sudo apt-get install --reinstall package_name

---

### Post by az on 2006-04-14
[QUOTE=JacksonL]nevermind about that last problem. I fixed it.
but my graphics drivers are broken. I'm using an nvidia 6800GS. I think I might have broken my ndiswrapper and nvidia-kernel modules because I tried to compile them with my new kernel but of course that didn't work. I guess I should just reinstall them via apt. no?[/QUOTE]
Reinstall linux-restricted-modules for your kernel, too.

Then run

sudo dpkg-reconfigure xserver-xorg

---

### Post by JacksonL on 2006-04-14
oh man.. now I have a new problem. I haven't done anything since getting the nvidia drivers to work because I had to leave for a while. now when I try to log in to GNOME it gives me an error saying something like "libgail-gnome wasn't found and is needed to load GTK+" and "libatk-bridge is needed to load something or other and was not found". I tried installing these packages via apt but they aren't in the repositories. any ideas?

ps. thanks for all the help so far. you guys are awesome.

---

### Post by JacksonL on 2006-04-15
bump

---

### Post by towsonu2003 on 2006-04-15
I found these:
```
--> username@host:~$ apt-cache search libgai
**libgail-common** - GNOME Accessibility Implementation Library -- common modules
**libgail-dbg** - Gail libraries and debugging symbols
libgail-dev - GNOME Accessibility Implementation Library -- development files
libgail-doc - documentation files of the Gail library
[/b]libgail-gnome-dbg[b] - libgail-gnome library and debugging symbols
libgail-gnome-dev - Development files of libgail-gnome
**libgail-gnome-module** - GNOME Accessibility Implementation Module for GnomeUI/BonoboUI
libgail17 - GNOME Accessibility Implementation Library -- the shared libraries
--> username@host:~$ apt-cache search libatk
**libatk1.0-0** - The ATK accessibility toolkit
**libatk1.0-dbg** - The ATK libraries and debugging symbols
libatk1.0-dev - Development files for the ATK accessibility toolkit
libatk1.0-doc - Documentation files for the ATK toolkit
libatk1-ruby - ATK bindings for the Ruby language

```
I bolded the ones you might need. My synaptic is doing an update (dial up), so I don't know which ones are installed by default... 

I don't understand how system got messed up like that with a kernel compilation though?

---

