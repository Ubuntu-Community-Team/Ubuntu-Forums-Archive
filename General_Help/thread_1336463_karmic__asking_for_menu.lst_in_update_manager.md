---
title: "karmic  asking for menu.lst in update manager"
date: 2009-11-24
forum: General Help
---

### Post by Dayofswords on 2009-11-24
specs:
toshiba satellite L305-S546
3gb ram
intel core 2 duo t6400
fresh install ubuntu 9.10

today i did an update and downloaded them, but when its installing the updates karmic is asking if i want to create a menu.lst (see screenshot)

I've never had grub 1, i have the fancy new grub 1.something beta that karmic comes with

I'm not sure what to answer here or what will happen in either answer

---

### Post by coffeecat on 2009-11-24
> **Dayofswords said:**
> I've never had grub 1, i have the fancy new grub 1.something beta that karmic comes with

I hate to ask this, but are you sure? If you look at your screenshot a few lines up from where it stopped, it says:

> Searching for default file ... found: /boot/grub/defaultThe file /boot/grub/default comes with legacy grub, not grub 2 whose default file is /etc/default/grub. Have a look around the system - make sure you haven't got both versions of grub installed.

I've just done the same kernel update on my laptop about an hour ago, and it updated my grub2 without error or prompting me for menu.lst.

---

### Post by Dayofswords on 2009-11-24
i was trying to figure out how to update grub to check for new things (just to know how, update-grub didnt work and update-grub2 said i needed some things) a few weeks ago, but i dont remember installing the older grub, is there a way to redo the update after getting grub right

also, how would i get grub working right

---

### Post by whoop on 2009-11-24
I would just let it generate the menu.lst, as it seems to want it... You can always install grub2 later. You can even install grub2 when booting doesn't work at all...

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by Dayofswords on 2009-11-24
i hit y and it did this
see screenshot

---

### Post by Dayofswords on 2009-11-24
oh and this dont look good
```
$ grub-install -v
grub-install (GNU GRUB 0.97)

```
how do i remove the olderr grub so this thing wont happen again?
should i run sudo apt-get install grub2

---

### Post by whoop on 2009-11-24
> **Dayofswords said:**
> i hit y and it did this
see screenshot

Well, that looks a bit messed up :shock:, but at least it is continuing the upgrade....
You could end up with a working grub1 setup (with some grub2 parts in it, looks like it thinks they are bootable kernels ;) )... You'll be able to fix it, after the upgrade...
Probably via removing grub2 first (which could be not even selected in synaptic as the system does not seem to be aware of it), then install grub2 with chainload (see upgrade-from-grub-legacy in [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)). Then if grub2 works when chainloading you can remove grub1.

---

### Post by whoop on 2009-11-24
> **Dayofswords said:**
> oh and this dont look good
```
$ grub-install -v
grub-install (GNU GRUB 0.97)

```
how do i remove the olderr grub so this thing wont happen again?
should i run sudo apt-get install grub2

Read [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2) thoroughly, and assume you are running grub1. 

installing grub2 is indeed one of the steps... (I would first check if it isn't installed already)...

---

### Post by Dayofswords on 2009-11-24
> **whoop said:**
> Well, that looks a bit messed up :shock:, but at least it is continuing the upgrade....
You could end up with a working grub1 setup (with some grub2 parts in it, looks like it thinks they are bootable kernels ;) )... You'll be able to fix it, after the upgrade...
Probably via removing grub2 first (which could be not even selected in synaptic as the system does not seem to be aware of it), then install grub2 with chainload (see upgrade-from-grub-legacy in [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)). Then if grub2 works when chainloading you can remove grub1.

just to note: this is a fresh install, just an upDATE. plus when it rebooted it was using grub2

---

### Post by Dayofswords on 2009-11-24
i did the "Installing (Ubuntu 9.04+)" from the wiki and it seems to be running grub2

```
$ grub-install -v
grub-install (GNU GRUB 1.97~beta4)

```

---

### Post by whoop on 2009-11-24
> **Dayofswords said:**
> just to note: this is a fresh install, just an upDATE. plus when it rebooted it was using grub2

An update of a fresh Karmic install? That's really weird... Are you multibooting with another linux os (maybe that uses grub1)?

---

### Post by Dayofswords on 2009-11-25
i'm dual booting with vista, but all seems good now

---

