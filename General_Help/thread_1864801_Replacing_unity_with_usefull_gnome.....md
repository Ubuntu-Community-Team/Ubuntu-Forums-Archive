---
title: "Replacing unity with usefull gnome....?"
date: 2011-10-19
forum: General Help
---

### Post by Spyderkid on 2011-10-19
I want to replace Unity with the latest version of gnome,[COLOR="Silver"] (used in ubuntu 10.10)[/COLOR](GNOME 3)[B][U][COLOR="Red"] and would like to be able to switch between the two.
[/COLOR][/U][/B]
the classic gnome option is fairly pants, and not at all customisable. So don't suggest me to use this

---

### Post by RaganN on 2011-10-19
You can install Gnome 3 by typing in the terminal

sudo apt-get install gnome-shell

but this is not the version used in 10.10.  Gnome 2 is not available in 11.10.  There is a fallback mode that simulates the old shell, however.  I can't remember the command offhand to install it though.

---

### Post by haqking on 2011-10-19
> **Spyderkid said:**
> I want to replace Unity with the latest version of gnome, (used in ubuntu 10.10) and would like to be able to switch between the two.

the classic gnome option is fairly pants, and not at all customisable. So don't suggest me to use this

Gnome in 10.10 is not the latest version of Gnome.

Also Unity is a shell which sits on top of Gnome.

If you want the classic option which i think you are referring to then

```
sudo apt-get install gnome-session-fallback
```

---

### Post by Larkspur on 2011-10-19
> **Spyderkid said:**
> I want to replace Unity with the latest version of gnome, (used in ubuntu 10.10) and would like to be able to switch between the two.

the classic gnome option is fairly pants, and not at all customisable. So don't suggest me to use this

You cannot install Gnome 2, since Ubuntu 11.10 runs Gnome 3.  Since you don't like the fallback session, your best bet is to install an alternative DE like Xubuntu or Lubuntu (both available in the repositories), which are closer to what you are used to.

---

### Post by collisionystm on 2011-10-19
> I want to replace Unity with the latest version of gnome, (used in ubuntu 10.10) and would like to be able to switch between the two.

NOT the latest.

[http://www.gnome.org/gnome-3/](http://www.gnome.org/gnome-3/)

Its really not that bad.

---

### Post by haqking on 2011-10-19
> **RaganN said:**
> **You can install Gnome 3 by typing in the terminal**

sudo apt-get install gnome-shell

but this is not the version used in 10.10.  Gnome 2 is not available in 11.10.  There is a fallback mode that simulates the old shell, however.  I can't remember the command offhand to install it though.

Gnome 3.2 is already being used in 11.10.

gnome-shell is exactly that a shell for it, Unity sits on top of Gnome 3.2

---

### Post by mcduck on 2011-10-19
Ubuntu 11.10 *uses* the latest version of Gnome (even when you are running Unity), and yes, the fallback session of Gnome Shell (which is what I assume you mean with the "classic gnome option") *is* customizeable, although some methods for doing that are different than in old Gnome 2. For example editing the panels requires you to Alt+right-click instead of just a right-click, and changing themes and fonts etc. requires you to install [gnome-tweak-tool]("apt:gnome-tweak-tool"))

There is no easy, or supported, way of installing the old Gnome 2 on 11.10. And if you do it by hand, you won't be able to use any Gnome 3-based programs, or the Gnome Shell & Unity desktops, any more. So if you really want the old Gnome 2 and no othe roption, or desktop environment, is an option, you'd better just make a new install of some older Ubuntu version instead. But remember that it would only be a temporary solution, the old Gnome 2 is unsupported by it's developers and you *will* eventually have to move to something else...

---

### Post by Spyderkid on 2011-10-19
ok thanks guys, btw mcduck thanks for the info about the alt+right click.

---

### Post by haqking on 2011-10-19
> **Spyderkid said:**
> ok thanks guys, btw mcduck thanks for the info about the alt+right click.

remember to mark the thread as solved using thread tools.

Cheers

---

### Post by Spyderkid on 2011-10-20
ok, I generally do. Thanks for reminding me

---

### Post by Spyderkid on 2011-10-22
Re-Opening thread...

I installed the Gnome-3 shell, but all the text is really screwed up, any help...?

---

