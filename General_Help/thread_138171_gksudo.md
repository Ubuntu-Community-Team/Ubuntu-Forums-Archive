---
title: "gksudo"
date: 2006-03-01
forum: General Help
---

### Post by tadashi on 2006-03-01
I was reading the sudo FAQ and it stated never use sudo in a terminal to pull up a graphical program and to use gksudo instead.  I am not sure if I am doing something wrong but when I use gksudo kedit I just get a blank document.  However, when I use sudo kedit it works fine with no errors.  Is the FAQ old or did I miss a configuration setting?

---

### Post by earobinson on 2006-03-01
im pretty sure the that in kde you would use kdesu

also can you link to the doc that you read that in because I always do a sudo synaptic.

---

### Post by tadashi on 2006-03-01
[https://wiki.ubuntu.com/RootSudo?action=show&redirect=UsingSudo](https://wiki.ubuntu.com/RootSudo?action=show&redirect=UsingSudo)

It is toward the middle.  Then again after rereading it I think they meant to say do not use sudo to start x windows.

---

### Post by gingermark on 2006-03-01
As a general rule I think you use sudo for terminal commands (ie apt-get) and kdesu for graphical apps (like kate).

Some graphical apps will work fine with sudo, but you risk some nasty permissions errors (like the .ICEauthorty error that could prevent you from logging in in the future).

'kdesu kedit' would open kedit with root privs (with no document open), 'kdesu kedit /etc/apt/sources.list' (for example) would open sources.list in kedit with root privs.

---

### Post by earobinson on 2006-03-01
[QUOTE=gingermark]Some graphical apps will work fine with sudo, but you risk some nasty permissions errors (like the .ICEauthorty error that could prevent you from logging in in the future).[/QUOTE]

Thanks gingermark I have been using sudo and getting ICEauthorty  errors, easy to work around just log on in the command line and chmod it but now I know why :)

---

### Post by msak007 on 2006-03-01
Thanks for the clarifcation and the link to the wiki. I really didn't know there was a difference between sudo and kdesu and used them interchangeably. I got a .ICEAuthority error once and didn't know why, and sometimes I got errors when I tried to run graphical apps using sudo so I just ran them using kdesu not knowing that there was a difference. Now I know :)

---

### Post by earobinson on 2006-03-01
[QUOTE=msak007]Thanks for the clarifcation and the link to the wiki. I really didn't know there was a difference between sudo and kdesu and used them interchangeably. I got a .ICEAuthority error once and didn't know why, and sometimes I got errors when I tried to run graphical apps using sudo so I just ran them using kdesu not knowing that there was a difference. Now I know :)[/QUOTE]
you and me both

---

### Post by gingermark on 2006-03-01
I should stress this is as I understand things, I don't totally understand the reasoning behind it.

I know that gedit works fine with sudo - this is why "sudo gedit" is a common command in many of the guides. But kate, which is really the only gui text editor that one can assume a Kubuntu user has on their system, really needs to be used with kdesu. I think :)

---

### Post by aysiu on 2006-03-01
KWrite also works with sudo (not just Gedit).
Kate does not work with sudo, though. You need kdesu.

---

### Post by gingermark on 2006-03-01
[QUOTE=aysiu]KWrite also works with sudo (not just Gedit).
Kate does not work with sudo, though. You need kdesu.[/QUOTE]

The problem is that the only gui text editor installed by default in Kubuntu is Kate. Which can leave new users confused, when they are told to use Kedit or Kwrite, or when they are told to type 'sudo kate' and then have problems.

Such instructions seem commonplace on the forums. I would be interested to know why some gui apps work with sudo and others do not.

Still using kdesu for all graphical apps I need to run as root seems the safe bet.

---

