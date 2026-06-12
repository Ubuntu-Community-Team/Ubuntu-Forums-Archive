---
title: "Change default runlevel in Lucid 10.04.1"
date: 2010-09-28
forum: General Help
---

### Post by linuxdave1 on 2010-09-28
Thanks Canonical for taking away inittab.

How can I change the default runlevel so that X doesn't start at boot? All searches through the Ubuntu documentation refers to inittab, but they took it away darnit. :confused:

---

### Post by bodhi.zazen on 2010-09-28
First of all , Ubuntu uses upstart

[http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

With upstart the idea of a runlevel will soon be depreciated, although runlevels are still emulated, they likely will go away as more and more services are converted to upstart.

Second runlevels 2,3,4, and 5 have always been the same on Ubuntu dating as far back as Ubuntu 4.10. Ubuntu does not use runlevels the same as the distro you came from.

And to make matters worse, there are no tools to manage services any longer, graphical or command line.

I would edit /etc/init/gdm.conf and change the line "stop on runlevel [016]" to "stop on runlevel[0126]"

"runlevel" 2 is the default for Ubuntu.

---

### Post by linuxdave1 on 2010-09-29
Thanks for the reply. I'll read through that link when I have some time.

Having tools to manage and configure services is almost a must. Especially with this departure from the norm for Linux. Although I've never seen many GUI tools that really worked well (in Linux).

---

### Post by bodhi.zazen on 2010-09-29
> **linuxdave1 said:**
> Thanks for the reply. I'll read through that link when I have some time.

Upstart is a big bite when you first read up on it. With that said, it is popular and Fedora is using upstart in F13 and 14 ;)

> Having tools to manage and configure services is almost a must. Especially with this departure from the norm for Linux. Although I've never seen many GUI tools that really worked well (in Linux).

+1. The graphical tools tend to work well, at least in Fedora. They used to work well in Ubuntu as well.

I am sure they will come back, hopefully soon.

---

### Post by sisco311 on 2010-09-29
While bodhi.zazen's suggestion should work, booting with the **text** kernel parameter will also prevent display managers managed by Upstart (e.g. gdm, kdm and lxdm) from being started at boot time. 

If you are using Grub2, then in /etc/default/grub replace:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
with
```
GRUB_CMDLINE_LINUX_DEFAULT="[color=red]quiet splash[/color] **text**"
```
then run:
```
sudo update-grub
```

Remove [color=red]splash[/color] to disable the splash screen and/or [color=red]quiet[/color] to make the boot process verbose.

If you wish to create a separate boot option for the text and GUI mode then check out [post=9584414]this[/post].

---

### Post by linuxdave1 on 2010-09-29
Thanks for that info Sisco. If I change grub, will I be able to startx later?

---

### Post by bodhi.zazen on 2010-09-30
> **linuxdave1 said:**
> If I change grub, will I be able to startx later?

Of course, why would you not be able to startx later?

---

### Post by joephi on 2011-02-17
> **bodhi.zazen said:**
> Of course, why would you not be able to startx later?

true...even easier to me, as the superuser (e.g., root), enter in "start gdm" to bring up the graphical login subsystem as if you didn't add "text" to the boot command line.  And use either gdm-stop or stop gdm if you want it gone again.

---

