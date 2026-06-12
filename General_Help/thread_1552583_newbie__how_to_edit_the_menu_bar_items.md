---
title: "newbie : how to edit the menu bar items?"
date: 2010-08-13
forum: General Help
---

### Post by Bey-Dyn on 2010-08-13
hello everyone, 

I am new to Ubuntu, I installed a dual boot Windows 7 / Ubuntu netbook remix 10.04 yesterday. 
So far so good, everything works fine. 

However, i would like to get rid of the little enveloppe in the menu bar, more precisely in what i think is called the notification area. i have found some stuff online about how I'm supposed to delete a package and restart, quite unsuccessful method really, since the envelope is still there.

Plus whenI right click on the menu bar to pin / unpin items, it doesnt work, all the submenus are greyed out. 

Could you guys help me out a little ? 

Thanks in advance, 
Bey

-----------------------------------------
**EDIT** : I'm talking about this ...
[IMG]http://img405.imageshack.us/img405/817/screenshotmh.png[/IMG]

---

### Post by volamoot on 2010-08-13
Hello Bey-Dyn,
i too experienced this issue, but it was fixed via and update.
Have you tried to update your computer to the most current updates then rebooting it?
If not i would suggest that you do so.
-Best of Luck
-Volamoot

---

### Post by Bey-Dyn on 2010-08-13
Hi volamoot, 

Yes I did download and install all the latest updates... which hasnt fixed the problem unfortunately!

Any other ideas?

---

### Post by earthpigg on 2010-08-13
the volume and envelope thing are tied together in ubuntu 10.04.

this is silly, but that's the decision that's been made.

you can right click -> remove it, but it will take the volume indicator with it.

you will still be able to adjust the volume in system -> preferences -> sound.

---

### Post by Bey-Dyn on 2010-08-13
so Earthpigg you're saying there is NO WAY of removing that envelope icon? That just sucks !

Anyway, i still cant see any submenus when i right-click that menu bar... so i cant even take it out :(

---

### Post by earthpigg on 2010-08-13
> so Earthpigg you're saying there is NO WAY of removing that envelope icon? That just sucks !

Of course there is a way, this is Open Source software. We can either code the change ourselves, or file a bug report / feature request and ask people more knowledgeable than ourselves to make the change.

Alternatively, there may be a pointy-clicky way that i am not aware of. this is a very real possibility -- I do not have UNR installed anywhere.

> **Bey-Dyn said:**
> Anyway, i still cant see any submenus when i right-click that menu bar... so i cant even take it out :(

This might be something specific they have changed in the netbook remix, then. Sounds silly to me.

If this feature is really a huge deal for you, you could do some distro surfing. I'd suggest Linux Mint LXDE edition, and installing the lxlauncher package.

Linux Mint LXDE looks like [this]("http://www.youtube.com/watch?v=2Y7SVLKqobU"). 

lxlauncher is intended for netbooks, and looks like [this]("http://wiki.lxde.org/en/File:LXlauncher.png").

---

### Post by earthpigg on 2010-08-13
oh hey, look at these two links i just found:

[http://ubuntugenius.wordpress.com/2010/05/04/restore-missing-volume-button-to-system-tray-after-upgrade-to-ubuntu-10-04/](http://ubuntugenius.wordpress.com/2010/05/04/restore-missing-volume-button-to-system-tray-after-upgrade-to-ubuntu-10-04/)

[http://ubuntugenius.wordpress.com/2010/05/04/remove-evolution-mail-notifier-from-indicator-applet-in-ubuntus-system-tray/](http://ubuntugenius.wordpress.com/2010/05/04/remove-evolution-mail-notifier-from-indicator-applet-in-ubuntus-system-tray/)

try this:

uninstall the evolution-indicator package, and add gnome-volume-control-applet to system -> preferences -> startup applications.

the envelope ought to be gone, and you will have a normal volume control thingie.

---

### Post by 0004tom on 2010-08-13
sudo apt-get remove indicator-messages

log out and log back in

---

### Post by Bey-Dyn on 2010-08-13
Thanks for all the advice. 

I did find a way to get rid of that envelope icon though so I'll post it here. 

I visited the developer's website at [http://launchpad.net/indicator-applet](http://launchpad.net/indicator-applet) and it turns out that all I had to do was remove indicator-applet from synaptic package manager.

Hope that helps someone in the future.

regarding the right click on the menu bar, yeah it does seem like it's a function that was just stripped from the netbook version. i dont see another explanation, and i cant find anything about that online.

---

### Post by earthpigg on 2010-08-13
good. 

if you want a normal volume changer thingie:

> add gnome-volume-control-applet to system -> preferences -> startup applications.

---

### Post by kerry_s on 2010-08-13
the panel is locked on 10.04. there are several ways around it.

1. you can log out & select gnome session & add the netbook stuff.

2. you can just uninstall those indicators.

3. you can replace the panel with another panel or dock.

i'm using tint2 on mine, xfce4-panel & awn are also good replacements.

---

### Post by Bey-Dyn on 2010-08-13
Here are some very useful links to use as a complement to this question : 

[http://maketecheasier.com/unlock-gnome-panel-in-ubuntu-netbook-edition-une/2010/04/25](http://maketecheasier.com/unlock-gnome-panel-in-ubuntu-netbook-edition-une/2010/04/25)

[http://doc.ubuntu-fr.org/ubuntu_netbook_edition](http://doc.ubuntu-fr.org/ubuntu_netbook_edition)


--> it is indeed possible to unlock the limitations of UNE but only under a GNOME session while keeping the look and feel of netbook remix... more details in those links.

What I wonder about is battery life and power management -- basically how does a gnome session affect the use of the netbook... more resources needed ?

---

### Post by kerry_s on 2010-08-13
> **Bey-Dyn said:**
> Here are some very useful links to use as a complement to this question : 

[http://maketecheasier.com/unlock-gnome-panel-in-ubuntu-netbook-edition-une/2010/04/25](http://maketecheasier.com/unlock-gnome-panel-in-ubuntu-netbook-edition-une/2010/04/25)

[http://doc.ubuntu-fr.org/ubuntu_netbook_edition](http://doc.ubuntu-fr.org/ubuntu_netbook_edition)


--> it is indeed possible to unlock the limitations of UNE but only under a GNOME session while keeping the look and feel of netbook remix... more details in those links.

What I wonder about is battery life and power management -- basically how does a gnome session affect the use of the netbook... more resources needed ?

it should be the same battery life. your not running any more or less, it's the exact same.

---

