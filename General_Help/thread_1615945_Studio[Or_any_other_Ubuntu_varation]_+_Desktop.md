---
title: "Studio[Or any other Ubuntu varation] + Desktop"
date: 2010-11-07
forum: General Help
---

### Post by Sidar on 2010-11-07
Hi there,

I decided to give Ubuntu another try and installed the Studio version. During my installation it asked whether I wanted the Realtime kernel or not. I chose yes as I figured it could come in handy when I work with audio.

However since this version isn't exactly Ubuntu 10.10 as promoted , I decided to install Ubuntu Desktop on top of it (trough apt-get). For the full experience. ( im not even sure if it just installed extra software and added some folders)

Now my questions are:
 
1:The Realtime kernel is it now overwritten by any other kernel that came with the Desktop installation?

2: How will the updates handle my installation once i want to upgrade to, lets say, 11.04.
I'm not really sure about how the system will look at things to upgrade. Will it look at my Desktop installation or my Ubuntu Studio? ( concerning the Realtime kernel as well).

Just to add some more: I'm a total Linux Noob(although im not scared to use the Terminal)!

thanks for taking your time,

Sidar

---

### Post by Sidar on 2010-11-08
Bumperly bump.

---

### Post by cek on 2010-11-08
ubuntu-desktop is a "meta-package", meaning its not really a package itself, but installs all of the packages that make up ubuntu-desktop.

I don't know off hand if ubuntu-desktop installs a different kernel, though if it does, it likely made that kernel the default.  In order to boot different kernels you can simply configure GRUB to show the list of available choices at boot, by default it chooses the "default" kernel to boot.

As far as updates go, when packages get new versions in the repositories the updates will simply be available to your system, there is no real downside to installing ubuntu-desktop over ubuntu studio if you really want to have those packages -- it's the same as adding each package individually.

---

### Post by Sidar on 2010-11-09
Thanks,

That makes sense. Grub is already showing Kernels I can pick from.
Ubuntu studio does ask whether you want to install the RealTime kernel..but its not really showing of such thing in Grub...it just says Generic(?).

If only my wifi would work now ...*keeps searching on google*

And thanks =).

---

