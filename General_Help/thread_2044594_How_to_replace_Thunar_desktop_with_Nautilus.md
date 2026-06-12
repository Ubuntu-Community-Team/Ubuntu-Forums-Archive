---
title: "How to replace Thunar desktop with Nautilus ? ? ? ?"
date: 2012-08-19
forum: General Help
---

### Post by BlackoutWorm on 2012-08-19
Hello. I've just recently replace the file manager with nautilus, because I don't really care much for Thunar.
But how do I change the desktop and all the other stuff as well?
Thanks in advance

---

### Post by arsenic23 on 2012-08-19
If you look in the xfce setttings there should be startup items and session config tools. 

Remove xfdesktop from the startup items and and nautilus to the session.  That's all you have to do.  When you load nautilus without xfdesktop running it should take over.

---

### Post by BlackoutWorm on 2012-08-19
> **arsenic23 said:**
> If you look in the xfce setttings there should be startup items and session config tools. 

Remove xfdesktop from the startup items and and nautilus to the session.  That's all you have to do.  When you load nautilus without xfdesktop running it should take over.

Ah of course. And loading nautilus without the file manager is nautilus -f? Or is it nautilus -n. Cant remember.

---

### Post by BlackoutWorm on 2012-08-23
Bump!
How do I do this?
I really can't stand having thunar as a desktop manager.
And btw there weren't any entries in the session settings called xfdesktop.
So how do I fix this?

---

### Post by LewisTM on 2012-08-23
I don't get it. You dislike Xfce's file manager and desktop manager. Why stick with Xfce then? Just go with a [GNOME Classic]("http://ubuntuforums.org/showpost.php?p=11923589&postcount=4") desktop where Nautilus is king and regent.

Cheers!

---

### Post by BlackoutWorm on 2012-08-23
> **LewisTM said:**
> I don't get it. You dislike Xfce's file manager and desktop manager. Why stick with Xfce then? Just go with a [GNOME Classic]("http://ubuntuforums.org/showpost.php?p=11923589&postcount=4") desktop where Nautilus is king and regent.

Cheers!

I Love xfce but just not thunar.
There's a lot more to xfce than just the file and desktop manager, you know.

---

### Post by Bucky Ball on 2012-08-23
Tried PCmanFM? It is the one used by Lubuntu and very light. Don't love Nautilus myself and not fond of Thunar. You'll find it in the repos.

Out of curiousity; Is there any feature of Nautilus you're desperately after or just don't like Thunar? ;)

---

### Post by BlackoutWorm on 2012-08-23
> **Bucky Ball said:**
> Tried PCmanFM? It is the one used by Lubuntu and very light. Don't love Nautilus myself and not fond of Thunar. You'll find it in the repos.

Out of curiousity; Is there any feature of Nautilus you're desperately after or just don't like Thunar? ;)
PCmanFM is the file manager. I already have the nautilus file manager, but I want the desktop as well.
Nautilus is faster, faster right-click, less messy right click menu, can copy/paste directly into folders and other things like that.
The reason why I prefer xfce over gnome or anything else is because of the panels and the applets.
I really wanna try to make the unity lenses and hud work in xfce, but that's for another time.
XFCE is very customizble. Even more than gnome 2.

---

### Post by Bucky Ball on 2012-08-23
Don't follow. Want the desktop as well? You mean Unity? Which bits of the desktop, exactly?

---

### Post by BlackoutWorm on 2012-08-23
> **Bucky Ball said:**
> Don't follow. Want the desktop as well? You mean Unity? Which bits of the desktop, exactly?
Unity is not a desktop.
But I want nautilus desktop instead of thunar desktop.
That has nothing to do with unity.
What I am trying to do though is, I want the unity lens feature, hud and probably the sidebar. But first things first.

---

### Post by CrusaderAD on 2012-08-23
Whatever you're attempting to do, you might have an easier time installing ubuntu-desktop and altering things from there.

---

### Post by BlackoutWorm on 2012-08-23
> **CrusaderAD said:**
> Whatever you're attempting to do, you might have an easier time installing ubuntu-desktop and altering things from there.
Nope:)

Btw, solved!

I learned that xfdesktop4 was the package.
So I deleted it and added nautilus -n to the startup session.
This is great:)
Thanks a lot for your help:)

Before I mark this as solved, do you know what command that is to run HUD, and the command to open the lenses?
And also what packages they live in, so I don't have to install the whole gnome thing just to find these 2 things.?

---

### Post by Bucky Ball on 2012-08-23
> **BlackoutWorm said:**
> Unity is not a desktop.
But I want nautilus desktop instead of thunar desktop.
That has nothing to do with unity.
What I am trying to do though is, I want the unity lens feature, hud and probably the sidebar. But first things first.

Unity is a desktop environment, or DE. Nautilus is a file manager. ;)

Glad it's solved, almost.

---

### Post by CrusaderAD on 2012-08-23
> **bucky ball said:**
> unity is a desktop environment, or de. Nautilus is a file manager. ;)

glad it's solved, almost.

+1

---

### Post by BlackoutWorm on 2012-08-23
> **Bucky Ball said:**
> Unity is a desktop environment, or DE. Nautilus is a file manager. ;)

Glad it's solved, almost.
It's actually the shell (extension if you will). The desktop is steal nautilus

Anyway, that's not important at all. Do you guys know what the packages for hud and lenses are?

---

### Post by LewisTM on 2012-08-23
I've never seen someone want to build such a hybrid environment. It might be technically feasible but at what cost? To get the lenses and HUD you need Unity. If you want to keep Xfwm4 you might be able to run Unity-2D concurently with Xfce but I doubt it, it needs Metacity. For Unity 3D, you need to install and run Compiz in Xfce. Both flavors pull in a LOT of GNOME stuff. I just tried the second option in a VM. It works (you have to enable the Unity plugin in ccsm) but it puts a panel over your Xfce top panel.

It will be heavy; it will be messy. If you want a Unity-like dock, I suggest you try Cairo-Dock which runs perfectly alongside Xfce. If you want a dash-like app, try Synapse. The HUD has not counterpart AFAIK.

---

