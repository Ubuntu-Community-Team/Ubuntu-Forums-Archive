---
title: "Is it Kubuntu or Ubuntu using KDE?"
date: 2009-10-05
forum: General Help
---

### Post by tuahaa on 2009-10-05
Well, I was wondering that is my system officially considered "Kubuntu" if I install the Ubuntu 9.10 Beta and then install the Kubuntu Desktop on it?

---

### Post by CatKiller on 2009-10-05
As soon as you install anything at all, it differs from the released version.

In terms of features, installing kubuntu-desktop is pretty much equivalent to having installed Kubuntu from a cd. If that's your definition, then yes.

---

### Post by tuahaa on 2009-10-05
mkay cool. Thanks

---

### Post by issih on 2009-10-05
I think it should be called ubunku at that point....:)

---

### Post by tuahaa on 2009-10-05
lol ubunku indeed.

But anyhow I'm downloading the Kubuntu 9.10 Beta CD for myself as I stuffed up when trying to get them both to run (long story). I converted a friend over to linux (we had a common problem- windows) and I've decided to give him the Ubuntu 9.04 and tell him to upgrade to Kubuntu 9.10 when he feels comfortable. I think that would be the safest bet. We don't want to scare a newbie by giving him a test version, do we?

---

### Post by slakkie on 2009-10-05
It is Ubuntu using KDE. It not like they call Ubuntu with FVWM FVubuntu or whatever.

---

### Post by corncob on 2009-10-05
> **CatKiller said:**
> 
In terms of features, installing kubuntu-desktop is pretty much equivalent to having installed Kubuntu from a cd. 

I'm totally unfamiliar with Kubuntu.  Is its only difference from Ubuntu the desktop?

---

### Post by slakkie on 2009-10-05
> **corncob said:**
> I'm totally unfamiliar with Kubuntu.  Is its only difference from Ubuntu the desktop?

Yes, pretty much. You have some different apps as well, where Gnome uses Gnome apps, KDE uses KDE apps. But you can use KDE apps in Gnome and vice versa.

---

### Post by SeanHodges on 2009-10-05
> **corncob said:**
> I'm totally unfamiliar with Kubuntu.  Is its only difference from Ubuntu the desktop?

The desktop environment is different (KDE), as is the software that comes pre-installed. The default applications tend to be more integrated with the KDE environment.

[http://www.kubuntu.org/faq#whatis](http://www.kubuntu.org/faq#whatis)

If you install [kubuntu-desktop]("apt://kubuntu-desktop"), it installs all this alongside of your existing Ubuntu desktop. You can then switch between them using the "Options -> Select Session" menu option at the Login screen.

---

### Post by Lars Noodén on 2009-10-05
> **SeanHodges said:**
> 
If you install [kubuntu-desktop]("apt://kubuntu-desktop"), it installs all this alongside of your existing Ubuntu desktop. You can then switch between them using the "Options -> Select Session" menu option at the Login screen.


+1 for Sean's suggestion.

I'd add further that if you have the space and the interest, you can add more.  Xfce ([xubuntu-desktop]("apt://xubuntu-desktop")) is also popular.  Fluxbox is even smaller, [FVWM-Crystal]("apt://fvwm-crystal") is smaller still and something to consider for netbooks.

Even the big desktop environments like Xfce and KDE can be customized to your desire.  What you get in the default package is just a suggestion.  If you want to see an example of how much even a low-power GUI can be customized, install FVWM and run it to see how bare bones it is.  Then install FVWM-crystal and see the difference.  The same desktop (actually a window manager) but with customizations.

---

### Post by t0p on 2009-10-05
I installed Ubuntu on one of my computers.  Then I installed kubuntu-desktop, and I could switch desktop managers at the login screen via "Sessions".  But that didn't make the OS turn into "Kubuntu", as Gnome was still there.

I also installed xubuntu-desktop, and I could use XFCE via the login page and "Sessions".  But that didn't make the OS "Xubuntu" either.

I guess some of you would call the OS "K/X/Ubuntu", or "Kxubuntu", or something along those lines. Or maybe you'd call it "Ubuntu" when I'm using Gnome, "Kubuntu" when I'm using KDE, and "Xubuntu" when I'm using XFCE. But I think of it as Ubuntu.  So I've got more options - so what?  My Ubuntu is a little more featureful than the average install, that's all.  Nothing to get stressed about.

**Note:** Incidentally, I uninstalled kubuntu-desktop and most of the K-apps not long after installation.  KDE is a real bloat-hog, it ran noticeably slower than Gnome, and most of the K-apps brought nothing useful to the table.  I don't think I'll bother with "Kubuntu" again in a hurry.

Oh yeah, I almost forgot: installing kubuntu-desktop and/or xubuntu-desktop adds what seems like *hundreds* of apps to the menus.  You can edit the menus, of course.  But it's a pain nevertheless.  I wanted to set up the menu so it would show Gnome apps when I'm using Gnome, XFCE apps when using XFCE, and so on.  But I never figured out how to do that.  Can anyone enlighten me?  I use Gnome on that machine pretty much all the time now, since I upgraded the RAM; but it'd be useful to know anyway.

---

### Post by CatKiller on 2009-10-05
> **t0p said:**
>  Oh yeah, I almost forgot: installing kubuntu-desktop and/or xubuntu-desktop adds what seems like *hundreds* of apps to the menus.  You can edit the menus, of course.  But it's a pain nevertheless.  I wanted to set up the menu so it would show Gnome apps when I'm using Gnome, XFCE apps when using XFCE, and so on.  But I never figured out how to do that.  Can anyone enlighten me?

You'd do it by setting the [OnlyShowIn]("http://standards.freedesktop.org/menu-spec/latest/apb.html")/NotShowIn property for the .desktop entries. KDE has the ability to do this easily, but the other DEs don't. Since you didn't like KDE enough to explore, you probably didn't see it.

---

### Post by tuahaa on 2009-10-05
I have both gnome and KDE installed and I can switch between them any time. Man, KDE has a lot of bugs but it is fun to use. They need to fix those bugs

---

