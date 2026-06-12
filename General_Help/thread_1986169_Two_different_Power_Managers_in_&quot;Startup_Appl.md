---
title: "Two different Power Managers in &quot;Startup Applications&quot;"
date: 2012-05-24
forum: General Help
---

### Post by james_mcl on 2012-05-24
I've got both XFCE and Gnome 2.32 (yep, I'm a Luddite!) installed on my Ubuntu Natty laptop. (Actually, I'm pretty sure I started with Gnome and installed xubuntu-desktop instead of just XFCE, but I digress)

Whenever I boot into Gnome and go to System -> Preferences -> Startup Applications, I find that both

Power Manager (Power management daemon)
and
Power Manager (Power management for the Xfce desktop)

are ticked.

I'd like to untick the second, because I don't see why xfce4-power-manager should be running when I'm in Gnome and already have gnome-power-manager. However, if I do this, will it prevent the Xfce power manager from being one of XFCE's startup applications? Or will changes made in Gnome to the Startup Applications list only affect Gnome?

There are a few similar issues I have with the list - for instance, "XFCE Volume Daemon" being ticked when I log into Gnome, and the fact that

PulseAudio Sound System (Start the PulseAudio Sound System)
and
PulseAudio Sound System KDE Routing Policy (Start the PulseAudio Sound System with KDE Routing Policy)

are both ticked. But this one is the one which is bothering me the most.

Googling for more information, I found someone with the same problem ([http://mail.xfce.org/pipermail/xfce/2011-December/029648.html);](http://mail.xfce.org/pipermail/xfce/2011-December/029648.html);) however the replies to his posting worked on the assumption that he didn't plan on booting into Gnome again; whereas I want to be able to boot into both.

Thanks,

James McLaughlin.

---

### Post by 2F4U on 2012-05-24
>  However, if I do this, will it prevent the Xfce power manager from  being one of XFCE's startup applications? Or will changes made in Gnome  to the Startup Applications list only affect Gnome?

No offense from my side, but why don't you try it on your machine? There is not much that could go wrong since you can easily re-enable it.

---

### Post by james_mcl on 2012-05-24
Okay - unticked it in Gnome, rebooted into an XFCE session, rebooted into a Gnome session.

All seems fine except that a

No name
No description

entry has been added to the Startup applications list (with nothing but a blank string for "Command".) I delete it and reboot. It's there again. Don't know what's going on there, it's as if something keeps trying to add a new, but nonexistent, startup application before login.

Anyway, other than that, things seem fine, and I've unticked the XFCE Volume Daemon as well.

Thanks for the suggestion,

James.

---

