---
title: "shutdown or reboot only logs out"
date: 2011-06-26
forum: General Help
---

### Post by Bazon on 2011-06-26
Hello. From a 11.04 Ubuntu, I installed the meta-package xfce4 (*). 
Now, in the xfce4 session, "suspend" and "logout" (from the xfce4-panel button) works, but "shutdowmn" and "reboot" not, they only lead to GDM. (the shutdowm option there works.)

I tried to solve that by installing the meta-package "xubuntu-desktop" (maybe there are some necessary settings included?), and in fact, the login-screen changed (it's still GDM, I suppose) and there is now a "xubuntu" session, but in that, the probem is just the same: shutdown only leads to the login screen. 

In Gnome Classic or Unity, shutdowmn works as it shoulds, so it's not a general problem with my computer.

So how can I fix that?




(*)
In Detail, in forst tried to install xfce4 with ubuntu-software-center, but although it seemed to succeed, there was no xfce session. In Synaptic, installing the xfce3 metapackage worked. In fact, software-center seemed to have overlooked some dependencies...

---

### Post by doas777 on 2011-06-26
I don;t know for sure, as I have never run multiple DEs on one box, but I think it has to do with how the DE is started.

in the old days, you invoke a vtty with Ctrl + Alt + F1-6, and use it to stop X. this was before GDM was a respawning service. once stopped you could do whatever you needed to, and then just run 'startx' to reload your desktop. when you wanted to shut down from this manually started session, you could not do it from within gnome. 

I think you are experiencing the same thing with xfce, because gdm is the default and xfce is invoked as a standalone session.

the command line tools should work fine though. you could create launchers for 'shutdown'/'halt'/'reboot' and shutdown that way.

---

### Post by Bazon on 2011-06-26
Indeed, from a terminal, reboot works without problems.
The thing I don't like about custom launchers is, that I would have to enter the password. (Or who else should do that...)

Also, I don't think it's a general problem with DE switches: On my netbook, I switched from Ubuntu to Lubuntu by installing lubuntu-desktop, and there shutdown and reboot from the panel works.


**So is there another way apart from custom launchers, a way to make the normal way work?**
*(Maybe I should mention I use compiz in Xubuntu by autostarting compiz --replace?)*


Anyway, thanks for your answer, doas777! :-)

---

### Post by Toz on 2011-06-26
See: [http://ubuntuforums.org/showpost.php?p=10941852&postcount=4]("http://ubuntuforums.org/showpost.php?p=10941852&postcount=4")

---

### Post by Bazon on 2011-06-29
> **Toz said:**
> I don't have a solution, but I can provide some background on the issue. Whats really happening behind the scenes is that X is crashing before the shutdown/reboot command is executed, and the automatic response is to respawn the x session - leading to a redisplay of the login screen.

This is a known bug ([https://bugzilla.xfce.org/show_bug.cgi?id=7442]("https://bugzilla.xfce.org/show_bug.cgi?id=7442")) that has been fixed upstream in version 4.8.2 (I believe). Unfortunately, the fix introduces transparency issues ([https://bugzilla.xfce.org/show_bug.cgi?id=7534]("https://bugzilla.xfce.org/show_bug.cgi?id=7534"))

Looks like some sort of bad interaction between X and xfdesktop. I'm not exactly sure of how they're moving forward with this, but it may require some fixes both with xcfe and X.

The interesting thing is that this bug is intermittent (on my machines at least). Sometimes it crashes and sometimes it doesn't (meaning I can successfully shutdown/reboot). There doesn't appear to be any clear correlation between action and result. I find that I am more successful if I shutdown/reboot from the menu Logout option than I am from the Session Menu Logout option.

Thanks, that's it.
I actually saw the crash when using sudo shutdown now recently.

---

