---
title: "What Desktop environment?"
date: 2011-06-27
forum: General Help
---

### Post by nickos on 2011-06-27
What desktop environment should i install to develop Gnome apps?

As i cna see ,the required tools are


[LIST]
[*]Anjuta - 3.0
[*]Devhelp - 3.0
[*]Glade - 3.10
[/LIST]
and most of these versions are not available for ubuntu.
Tell me what DE to have in order to do that! 

thanks (:

---

### Post by yotam on 2011-06-27
Consider **emacs**.
In addition to its editing strengths, it has interfaces to:
gdb, compile/make, cscope and various source-control tools.

---

### Post by nickos on 2011-06-27
i am talking about Fedora,Kubuntu,XUbuntu dunno which is suitable for gnome development.

---

### Post by pqwoerituytrueiwoq on 2011-06-27
Desktop environment=unity/gnome/kde/xfce/lxde
you are referring to distributions

---

### Post by dFlyer on 2011-06-27
If your referring to Distro's any of them will do for development. They all offer various Desktop Environments IE gnome, kde etc.

---

### Post by FormatSeize on 2011-06-27
> **nickos said:**
> i am talking about Fedora,Kubuntu,XUbuntu dunno which is suitable for gnome development.
Fedora seems to be the obvious answer. Fedora Core 14, that is. I haven't done enough with 15 to know whether it would be suitable for real work, and there's no Kate. Real work can't be done without Kate, and BlueFish didn't install for whatever reason when I tried to compile it. In F14, though, everything is fantastic. It has all the best tools from both the GNOME and KDE environs, and you can get more if you need them.
 
I'm not sure if Glade is there, but it's not something that I typically use. I'm sure it, or something like it, is there.

---

### Post by nickos on 2011-06-27
sorry guys,looks like i was referring to distros.

i dont seem to be able to do anything , only the basic compiling at the terminal using g++.
I tried to get further with anjuta 3.0 and it cant be installed,no needs are met is all the configuration says.
I also cant install GTK 3.0.
 so if someone can tell me what is the best distro which will be able to do GNOME development, post a reply :) 

looks like im going with fedora?

---

### Post by Simian Man on 2011-06-27
It really doesn't matter, any distro can do all of the things you mentioned, though I prefer Fedora.

> **FormatSeize said:**
> I haven't done enough with 15 to know whether it would be suitable for real work, and there's no Kate. Real work can't be done without Kate, and BlueFish didn't install 

Fedora 15 does have kate.  It's in the "kdesdk" package, just like it has been for several releases at least.

---

### Post by nickos on 2011-06-27
yeah but my problem is that i cant install anjuta 3.0 and GTK 3.0 on ubuntu because i cant even install the requirements!
So will any other distro support this?

---

### Post by el_koraco on 2011-06-27
> **nickos said:**
> yeah but my problem is that i cant install anjuta 3.0 and GTK 3.0 on ubuntu because i cant even install the requirements!
So will any other distro support this?

You need distros that come with Gnome 3. Fedora, Arch Linux, Gentoo, Foresight Linux. Fedora is probably the easiest to install and maintain of all of them.

---

### Post by mcduck on 2011-06-27
> **nickos said:**
> yeah but my problem is that i cant install anjuta 3.0 and GTK 3.0 on ubuntu because i cant even install the requirements!
So will any other distro support this?

There is an official PPA repository for Ubuntu 11.04 with GTK3 and Gnome 3 packages. The only thing here is that Unity, and the version of Gnome used in Ubuntu 11.04, uses GTK2 and the two GTK versions won't work on the same machine.

So if you want to get GTK3 you'll need to move to using Gnome 3 and the Gnome Shell instead. Which works just fine: [http://news.softpedia.com/news/How-to-Install-GNOME-3-on-Ubuntu-11-04-194085.shtml]("http://news.softpedia.com/news/How-to-Install-GNOME-3-on-Ubuntu-11-04-194085.shtml")

Anyway, any distribution that has GTK3 available should work for what you want to do.

---

### Post by nickos on 2011-06-28
right now im having a problem installing fedora.i donwloaded the .iso live image file to my usb.I cant Boot my computer cause i am running a Three Boot(when i start the computer i choose from windows xp,7 and ubuntu).

what to do to instlal fedora???

---

