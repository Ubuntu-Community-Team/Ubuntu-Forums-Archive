---
title: "Docky Docklets"
date: 2010-02-12
forum: General Help
---

### Post by kolo-01 on 2010-02-12
hi,
i am using the Docky panel, and would just like to know how to go about adding more applets to the panel as i intend to eventually get rid of my other default panel, so im trying to find an applet for processes like shutting down, killing applications and showing the desktop. not sure if there would be one for the main menu.. does anyone know of good places to find these applets and how to insert them into docky? any help would be appreciated, thanks

---

### Post by M93 on 2010-08-31
am searching for the same
but seems like theres no answer for that question :)
have u figured something yet?

---

### Post by inso_741 on 2010-08-31
try AWN!!!

---

### Post by M93 on 2010-08-31
i tried to force myself to like but i couldnt :D

---

### Post by kolo-01 on 2010-08-31
docky has got better and better in the last few months now its super stable and much better than any other dock now in my opinion

---

### Post by M93 on 2010-08-31
yup thats y am not planning to give it up
but it needs some stuff!! :)

---

### Post by fabounet on 2010-09-01
give a try to GLX-Dock, it's has a bunch of nice applets.

---

### Post by M93 on 2010-09-01
oh yes cairo dock i like it, not as much as docky but i do
i downloaded this glx...and its really g00d
thank u for the link ;)

---

### Post by weberc2 on 2010-11-16
> **fabounet said:**
> give a try to GLX-Dock, it's has a bunch of nice applets.

Yeah, I have that installed and I love it's customization features; however, I couldn't figure out how to make it a simple panel that spans the width of my screen. I'm also looking to replace the default panel.

---

### Post by kerry_s on 2010-11-16
awn is the best gnome-panel replacement.

see pic, all are awn.

---

### Post by fabounet on 2010-11-16
easy, amongst the different view available in Cairo-Dock, select the "panel" one, and you get a pretty gnome-panel replacement ;-)

---

### Post by inso_741 on 2010-11-16
> **kerry_s said:**
> awn is the best gnome-panel replacement.

see pic, all are awn.

How did you get the separate panel for network/sound applet?

---

### Post by kerry_s on 2010-11-16
> **inso_741 said:**
> How did you get the separate panel for network/sound applet?

you just click add dock & put the stuff on it.

you need to running the latest awn, so use the ppa.
[https://launchpad.net/~awn-testing/+archive/ppa](https://launchpad.net/~awn-testing/+archive/ppa)

---

### Post by Habitual on 2010-11-17
> **kolo-01 said:**
> hi,
i am using the Docky panel, and would just like to know how to go about adding more applets to the panel as i intend to eventually get rid of my other default panel, so im trying to find an applet for processes like shutting down, killing applications and showing the desktop. not sure if there would be one for the main menu.. does anyone know of good places to find these applets and how to insert them into docky? any help would be appreciated, thanks

You need to not use the docky from the repos, but the this version for those applets --> Docky **2.1.0** bzr docky r1688 **ppa**
It comes with those applets.

Add 
deb [http://ppa.launchpad.net/docky-core/ppa/ubuntu](http://ppa.launchpad.net/docky-core/ppa/ubuntu) maverick main
deb [http://ppa.launchpad.net/docky-core/stable/ubuntu](http://ppa.launchpad.net/docky-core/stable/ubuntu) maverick main
deb-src [http://ppa.launchpad.net/docky-core/ppa/ubuntu](http://ppa.launchpad.net/docky-core/ppa/ubuntu) maverick main
deb-src [http://ppa.launchpad.net/docky-core/stable/ubuntu](http://ppa.launchpad.net/docky-core/stable/ubuntu) maverick main

---

### Post by inso_741 on 2010-11-18
> **kerry_s said:**
> you just click add dock & put the stuff on it.

you need to running the latest awn, so use the ppa.
[https://launchpad.net/~awn-testing/+archive/ppa](https://launchpad.net/~awn-testing/+archive/ppa)

thanx!!!

---

### Post by kolo-01 on 2010-12-03
> **Habitual said:**
> You need to not use the docky from the repos, but the this version for those applets --> Docky **2.1.0** bzr docky r1688 **ppa**
It comes with those applets.

Add 
deb [http://ppa.launchpad.net/docky-core/ppa/ubuntu](http://ppa.launchpad.net/docky-core/ppa/ubuntu) maverick main
deb [http://ppa.launchpad.net/docky-core/stable/ubuntu](http://ppa.launchpad.net/docky-core/stable/ubuntu) maverick main
deb-src [http://ppa.launchpad.net/docky-core/ppa/ubuntu](http://ppa.launchpad.net/docky-core/ppa/ubuntu) maverick maincore/stable/ubuntu[/url] maverick main




i made that post when docky didnt have the docklets it has now, they obviously found my post and put them in for me..

---

### Post by kolo-01 on 2011-01-05
just thought id say that i now use awn as a replacement for the main gnome-panel, i got the idea off the guy on the previous page, it is a good idea for how i like things- sort of minimal, it can be shrunk and hidden, but docky is still the real king, although still doesnt have the docklets to make it a panel that can work without anything else, so i use them together. they both hide for windows so everything is in full screen, takes a bit of getting used to  but its not that hard living without windows selecter bar, still cant find a force quit replacement though. may aswell give you a picture of my desktop too..

[IMG]http://i167.photobucket.com/albums/u152/kolo-01/desktop.png[/IMG]

---

### Post by Habitual on 2011-01-05
add this to your repo:
ppa:docky-core/ppa

and then use Package Manager to install 2.1.0x

It has the Session Manager functions you are looking for.

---

### Post by kolo-01 on 2011-01-05
> **Habitual said:**
> add this to your repo:
ppa:docky-core/ppa

and then use Package Manager to install 2.1.0x

It has the Session Manager functions you are looking for.


i have that ppa, but its not the session manager that i need awn for, its the main menu, that is another key one that as far as i know docky cant do yet. i just put the session manager on awn cos i prefer it there, also docky's network manager isnt that good, the one on awn is identical to the gnome-panel which is a bit better.. cheers though

---

