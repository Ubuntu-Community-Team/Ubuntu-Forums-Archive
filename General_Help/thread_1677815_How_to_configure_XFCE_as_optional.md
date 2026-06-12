---
title: "How to configure XFCE as optional"
date: 2011-01-29
forum: General Help
---

### Post by Duke_N on 2011-01-29
hello folks ...

I'm fairly new to Linux (BSD background) - Xubuntu my first exposure. 

I'm running Xubuntu 10.10
Xfce 4 Desktop Environment
version 4.6.2 (Xfce 4.6)

I would like to boot Xubuntu to a Virtual terminal by default, and have the options of running (testing) various window managers - blackbox, e.g. using "startx" from the CLI.

Is there a way that I can reconfigure my current install to do that? I use Grub to boot. TIA ....
--
Duke_N

---

### Post by sisco311 on 2011-01-29
Hi and welcome to the forums!

The preferred method for disabling the display manager is to boot with the **text** kernel parameter. 

Edit the file **/etc/default/grub** and replace the line **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** with **GRUB_CMDLINE_LINUX_DEFAULT="text"**, then generate a new Grub2 config file:
```
sudo update-grub
```

I'm not sure how you can change the session started by startx as a regular user, but as root you can use:
```
sudo update-alternatives --config x-session-manager
```

As a regular user you can use xinit. For example, to start gnome on vt7 and lxde on vt8, you could run something like:
```
xinit /usr/bin/gnome-session -- :0 vt7
```
```
xinit /usr/bin/startlxde -- :1 vt8
```

---

### Post by Duke_N on 2011-01-29
@sisco311

Thanks for the detailed tips. I'll give them a try this weekend. Have a good one!
--
Duke_N

---

### Post by Duke_N on 2011-01-29
> **sisco311 said:**
> Hi and welcome to the forums!

The preferred method for disabling the display manager is to boot with the **text** kernel parameter. 

Edit the file **/etc/default/grub** and replace the line **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** with **GRUB_CMDLINE_LINUX_DEFAULT="text"**, then generate a new Grub2 config file:
```
sudo update-grub
```

OK! understand that ...

> 
I'm not sure how you can change the session started by startx as a regular user, but as root you can use:
```
sudo update-alternatives --config x-session-manager
```Not sure what this is all about? is this about choosing another window manager, after I've logged in and using a particular one? If not, when should I issue this command?

> 
As a regular user you can use xinit. For example, to start gnome on vt7 and lxde on vt8, you could run something like:
```
xinit /usr/bin/gnome-session -- :0 vt7
``````
xinit /usr/bin/startlxde -- :1 vt8
```So this is simply a way of test-driving various "wm"?
--
Duke_N

---

### Post by andrew.46 on 2011-01-30
> **Duke_N said:**
> I would like to boot Xubuntu to a Virtual terminal by default, and have the options of running (testing) various window managers - blackbox, e.g. using "startx" from the CLI.

You are describing the default behaviour of Slackware :)

---

### Post by Duke_N on 2011-01-30
> **andrew.46 said:**
> You are describing the default behaviour of Slackware :)

Could be! However, does Slackware have something as cool as Synaptic Package Manager? ;)

---

### Post by andrew.46 on 2011-01-31
> **Duke_N said:**
> Could be! However, does Slackware have something as cool as Synaptic Package Manager? ;)

Well I guess Slackware has installpkg, upgradepkg, removepkg and friends but I am not sure about the cool factor of these :)

---

