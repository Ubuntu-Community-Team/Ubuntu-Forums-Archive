---
title: "Install XP in a new partition and dualboot"
date: 2011-12-10
forum: General Help
---

### Post by dpolancom on 2011-12-10
Hi, I have Ubuntu 11.10 installed and I want to create a new partition, install XP on it and have the dualboot option
Could you please help me to do this?
Thx in advance

---

### Post by pengyou on 2011-12-10
First you are going to need to **use a partition editor** **to resize** your Ubuntu partition, so that you have a new partition to put that install on.
I recommend **gparted**.
You can
```

sudo apt-get install gparted

```
if it isn't already installed. (it should be)
You should **be very careful with this, or you could end up losing your data.**
Everyone says **you should back up your data**, too. So you should probably do that.
I don't, but I can live with the loss of everything on my computer, can you?

If you just **want to run some Windows XP applications though,** I recommend **VirtualBox **
[https://www.virtualbox.org/](https://www.virtualbox.org/)
or
**WINE**
[http://www.winehq.org/](http://www.winehq.org/)
instead. It is a lot less of a headache.

Oh and of course **for all of this you will need a copy of Windows XP.**
[]("https://www.virtualbox.org/")

---

### Post by gennatolls on 2011-12-10
Installing windows will wipe out GRUB so you will need to GRUB rescue with a live cd. Virtualbox looks like a good option unless you plan on doing anything cpu intensive.

---

### Post by Mark Phelps on 2011-12-10
The advice you were given to install Gparted -- won't Work!

Why? Because in order to use it, the partition containing it has to be mounted -- and you can't make changes to a mounted partition.

Instead, what you need to do is boot from an Ubuntu desktop CD, and THEN use GParted to resize the Ubuntu partition.

---

