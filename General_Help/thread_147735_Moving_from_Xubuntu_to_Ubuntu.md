---
title: "Moving from Xubuntu to Ubuntu"
date: 2006-03-20
forum: General Help
---

### Post by kryptondog on 2006-03-20
Hi all, I'm fairly new at Linux so apologies if this is something that's obvious...

I've been a Linux user for about three months now, thanks to Ubuntu.  From the start, I've used the base server install with XFCE because I liked how light weight it seemed.  I've enjoyed it quite a bit, but after reading up on the new improvements to Gnome and trying Drake on a live CD, I think I'm ready to move up and start working with Gnome.

My problem is that I've spent a lot of time tweaking things and getting it the way I want, and I'd rather not start over from scratch with a fresh install of Ubuntu.  Is there a fairly uninvolved way of installing Gnome and keeping everything "the way I had it", as it were?  If I were to install Gnome, would Gnome know where my programs are?  As a neophyte, would it be simpler to just back everything up and start fresh?

Thanks for any help you can provide me.

---

### Post by Sutekh on 2006-03-20
Just ```
sudo apt-get install ubuntu-desktop
```and you will get the default Ubuntu desktop installation, all your XFCE stuff will remain, GNOME will find your apps. 

[QUOTE=kryptondog]keeping everything "the way I had it"[/quote]I don't know exactly what you mean by this though, could you elaborate on the things that are customised and you want to keep?

Do not re-install.

---

### Post by dragomirov on 2006-03-20
I assume you're using Breezy. For moving from breezy to dapper just change you sources.list file (you can edit by "sudo gedit /etc/apt/sources.list)

Here is an example [http://www.macewan.org/2006/02/23/upgrading-breezy-to-dapper/]("http://www.macewan.org/2006/02/23/upgrading-breezy-to-dapper/")

Have a try to the new xfce 4.4: it's fantastic

Sit down and relax there are a lot of upgrades. If synaptic brokes up: don't panic just reboot with your old kernel and go on

h&k

---

### Post by dragomirov on 2006-03-20
....just let me add

Your settings won't get lost. If you ever plan for a fresh installation just make a backup copy of your home directory ;)

Have a look to the hidden files and dirs, there are lots of config file underneath

---

### Post by kryptondog on 2006-03-20
[QUOTE=Sutekh]I don't know exactly what you mean by this though, could you elaborate on the things that are customised and you want to keep?[/QUOTE]

More than anything just stuff like my ATI driver and the little tweaks that easyubuntu did.  I also used a work-around on this board to fix an issue I had with my system clock going way too fast that I wanted intact.

Thanks for the replies, guys.  This doesn't sound hard at all.  Much appreciated.

---

### Post by Sutekh on 2006-03-20
[QUOTE=kryptondog]More than anything just stuff like my ATI driver and the little tweaks that easyubuntu did.  I also used a work-around on this board to fix an issue I had with my system clock going way too fast that I wanted intact.
[/QUOTE]
Cool, that kind of thing won't care what desktop environment you have running and shouldn't cause any problems if you start to use GNOME.

---

### Post by kryptondog on 2006-03-20
Aw, pooh.  :(

> Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: evince but it is not going to be installed
E: Broken packages

I tried downloading evince, but it asks for libpoppler0c2-glib, which in turn:

> libpoppler0c2-glib: Depends: libpoppler0c2 (= 0.4.2-0ubuntu6) but 0.4.2-0ubuntu6.5 is to be installed

Any ideas?

---

