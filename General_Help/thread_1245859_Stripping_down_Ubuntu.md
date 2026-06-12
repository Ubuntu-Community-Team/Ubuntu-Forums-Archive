---
title: "Stripping down Ubuntu"
date: 2009-08-21
forum: General Help
---

### Post by MechWarrior001 on 2009-08-21
How hard would it be to strip down ubuntu to the point 
where the system requirements rival that of Windows 98(SE)?

---

### Post by bchurchill on 2009-08-21
I did this just yesterday, and had quite a bit of fun:

[http://www.howtoforge.com/minimal-ubuntu-8.04-server-install](http://www.howtoforge.com/minimal-ubuntu-8.04-server-install)

The instructions are old, but work fine.  Just replace 'hardy' with 'jaunty'.  You'll find this is a very barebones installation: you'll get no GNOME, no KDE, no X, just a command prompt.  You'll need to add all the software you want.  After that you can install what you want.

**Do a complete backup first!!**

---

### Post by MechWarrior001 on 2009-08-21
Would drivers and gaming-related packages be able to work? or would I have to install a ton of dependencies?

Would that also be capable of running a tremulous dedicated server in terminal despite lack of Desktop environment and drivers?

---

### Post by ibutho on 2009-08-21
Drivers for most hardware on Linux based systems are already included in the kernel or are installed as kernel modules, so depending on your hardware, you may not need to install any drivers. What do you mean by a Tremolous dedicated server? You do not need a desktop environment to run a webserver. In fact most Unix and Linux servers are run without a GUI at all.

---

### Post by MechWarrior001 on 2009-08-21
thats good, but would it be possible to install and play anything like AssualtCube or Tremulous or the Nvidia 177-latest drivers?

---

### Post by bchurchill on 2009-08-21
> **MechWarrior001 said:**
> thats good, but would it be possible to install and play anything like AssualtCube or Tremulous or the Nvidia 177-latest drivers?

You can install anything you need to in addition to the base system.  In fact, you could even manually install all the components of a standard Ubuntu install.  However, if you add things like gnome you might find that the original speed increase is not very much.

A warning if you want to install more packages: not all the repositories will be enabled by default, you'll have to modify a config file to access most of them.  You'll get a lot of package-not-found responses from apt-get until you do.  I already forget what it is, you'll need to google it.

---

### Post by MechWarrior001 on 2009-08-21
So would it act like the debug screen when you have a improper graphical setup and you get that black x for a mouse and it allows you to open gedit to fix something?

---

### Post by malachi1990 on 2009-08-21
To run games, you'll need an X server, and the nvidia drivers.

The quickest way to grab these is via:

sudo apt-get install xorg

sudo apt-get install nvidia-180-kernel-source

sudo apt-get install nvidia-180-modaliases

sudo apt-get install nvidia-settings

The attachement is something I've started writing for a few of my friends who want a stripped down ubuntu as well.  It's a first draft, but it covers most of the bases.


As to the repos that tremulous is likely in, you'll need to enable them in your /etc/apt/sources.list .

The easiest way is to try and install them via a gui package manager (like synaptic or the add/remove utility).  That will automatically enable them for you.

---

