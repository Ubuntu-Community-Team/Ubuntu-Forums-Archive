---
title: "newbie need help!"
date: 2006-04-16
forum: General Help
---

### Post by hanamachi on 2006-04-16
Hello everyone, just switched to Linux Ubuntu Gnome and I want to update my firefox, but how? i downloaded the tar file but where do I go from there to upgrade it and how do i install prog in general downloaded from the web?
Also what is difference btwn gnome and kde? thanks

---

### Post by Zdravko on 2006-04-16
>  Also what is difference btwn gnome and kde?
Both GNOME and KDE are desktop environments just like EXPLORER for Windows.
GNOME is based on pure C(++) via the GTK(mm) API. As a result the graphical system is quite fast, stable and simple :)
KDE is based on a macro-API that wraps C++ - Qt. As a result this desktop has a lot more possibilities, it is more flexible, it looks nicer, but also takes much more resources and is error-prone.

---

### Post by hanamachi on 2006-04-16
i see

---

### Post by xXx 0wn3d xXx on 2006-04-16
[QUOTE=hanamachi]Hello everyone, just switched to Linux Ubuntu Gnome and I want to update my firefox, but how? i downloaded the tar file but where do I go from there to upgrade it and how do i install prog in general downloaded from the web?
Also what is difference btwn gnome and kde? thanks[/QUOTE]
You can use automatix to update firefox with ALL the plugins and many other things you may find interesting.

Put this in terminal. Copy + Paste.

> wget [http://beerorkid.com/automatix/automatix_5.7-3_i386.deb](http://beerorkid.com/automatix/automatix_5.7-3_i386.deb)
sudo dpkg -i automatix_5.7-3_i386.deb

Start it by going under Applications > System Tools > Automatix. Then check the things you want and then click ok then your done and it will install everything.

---

### Post by hanamachi on 2006-04-16
yeah i did automatix, but for example the firefox is version 1.5.0.1 not 1.5.0.2, how for i get the latest installed?

---

### Post by xXx 0wn3d xXx on 2006-04-16
[QUOTE=hanamachi]yeah i did automatix, but for example the firefox is version 1.5.0.1 not 1.5.0.2, how for i get the latest installed?[/QUOTE]
Help > Check for Updates. If it is greyed out then close firefox and in terminal type:

> sudo su  Then it will ask for your password. Put it in, but you won't see it then press enter.

Then:

> firefox

Firefox will then start and you should have the option.

---

### Post by rtfmviolator on 2006-04-16
Automatix completely Rocks!!!!

---

### Post by ncappel1 on 2006-04-16
The difference between the two versions is more support with mac osx and a couple of security fixes. those are always nice to have, don't want to get malicious code to ruin your days!
here's the release notes:
[http://www.mozilla.org/projects/security/known-vulnerabilities.html#firefox1.5.0.2](http://www.mozilla.org/projects/security/known-vulnerabilities.html#firefox1.5.0.2)

---

### Post by YuHoo on 2006-04-16
[QUOTE=Zdravko]Both GNOME and KDE are desktop environments just like EXPLORER for Windows.
GNOME is based on pure C(++) via the GTK(mm) API. As a result the graphical system is quite fast, stable and simple :)
KDE is based on a macro-API that wraps C++ - Qt. As a result this desktop has a lot more possibilities, it is more flexible, it looks nicer, but also takes much more resources and is error-prone.[/QUOTE]

In english...
Gnome is usually faster and more windows like than KDE (not like windows, but closer to).
KDE is more mac-ish. You'll find the menu access through clicking the desktop very nice. It is horrifically slow though if you do not know what you're doing and it keeps building up widgets/stuff. 
It's all a matter of taste though. All k(insert name of program here) is usable in gnome and vice versa. They're only superficial differences in the real meaning of the word. I haven't heard of this with KDE, but with Gnome you can have different windows managers. As you explore you'll start to perhaps customize how you interact with your computer.

KDE - Simple, kind, pretty, good beginning stage
Gnome - Step down in prettiness, but you can alter more powerful things like the window manager
XFCE - Another desktop environment, not as friendly as KDE or Gnome. Don't start with it. But after a while you might look for a change, I'd suggest looking here.
Fluxbox - The least pretty of them all, least kind, and also the ultimate for customized interface. Look to this perhaps instead of XFCE if you're comfortable with minimalism.

---

