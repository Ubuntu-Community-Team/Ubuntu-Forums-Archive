---
title: "A few minor, but annoying, bugs"
date: 2006-04-02
forum: General Help
---

### Post by Aielyn on 2006-04-02
Hi all,

First of all, I should mention that I am very much a newbie to Linux, though I am an adept user of both DOS and Windows. I am using Ubuntu Breezy (GNOME version). Before I get into the problems, I would like to note that I am quite impressed with Ubuntu - I've only had it for a week, and I'm using it quite easily already. So far, I've only needed to use Windows for those programs that aren't available for linux (for instance "Maple") - the rest of the time, I have used ubuntu without major problems.

I hope this is the right place for such a thread.

Now onto the bugs that I haven't been able to iron out.

1. A strange problem, that I have seen mentioned a few times on the forum, without solution - Occasionally, the mouse will start behaving strangely, with the focus being locked on a particular panel/window, so mouse-clicks only register for that window. This will happen, seemingly for no reason, and will fix itself after about 10 minutes or so. I have found a temporary workaround - if I right-click, and the panel it is locked to has a right-click menu, then the focus frees itself until my next left-click. If it doesn't have a right-click menu, I have to close whatever has the focus, using the keyboard, to regain control.

2. I used Automatix to install a number of things, including the Debian Menu. Problem is, it appears that the Debian Menu is incompatible with smeg (Clicking "Applications menu editor" causes a startup bar at the bottom, but closes without actually opening, and when I put smeg or sudo smeg into the terminal, I get an error). I can get smeg to work again by reinstalling menu-xdg, but that causes the Debian menu to disappear again. Is there any way to get the two to cooperate? Or perhaps an alternative menu editor?

3. XMMS seems slightly buggy - sometimes it will freeze at the end of a song (so that it needs to be killed and restarted), and other times it will just close without warning at the end of a song. Note: I have got the plugin that allows XMMS to play m4a files, and those are the files I have been listening to, so it might be related to the plugin.

4. Hibernation refuses to work on the system - when I go "Log out" and choose Hibernate, it successfully drops into hibernation, but then on bootup it freezes.

5. When I install aegis-virus-scanner, it refuses to appear on the menu, even though it is marked as visible in the menu editor.

6. When I choose Networking from the System > Administration menu, I don't get an "Add" button on the connections tab, although one is mentioned in Help.

7. Despite gnome-system-tools being installed, the bootloader editor component does not appear to have been installed.

I think that is enough for now - those are the worst of the bugs. I don't suppose any of them have known solutions, do they?

Thanks in advance

-Aielyn

P.S. Sorry, but this is a pet peeve - The program "Mahjongg" that installs with Ubuntu is not Mahjongg - it is "Mahjongg Tiles", AKA Taipei AKA Shanghai. Mahjongg is a four player tile game similar to Gin Rummy.

---

### Post by Aielyn on 2006-04-08
Have I posted this in the wrong forum, or something?

---

### Post by Aielyn on 2006-04-10
That's one down - I managed to solve number 2:
> I used Automatix to install a number of things, including the Debian Menu. Problem is, it appears that the Debian Menu is incompatible with smeg (Clicking "Applications menu editor" causes a startup bar at the bottom, but closes without actually opening, and when I put smeg or sudo smeg into the terminal, I get an error). I can get smeg to work again by reinstalling menu-xdg, but that causes the Debian menu to disappear again. Is there any way to get the two to cooperate? Or perhaps an alternative menu editor?

While trying to get it working, I updated smeg to alacarte.

It turned out that the link in /etc/xdg/menus called "debian-menu.menu" was broken, pointing to a directory in /var/ (I don't recall the exact target). To fix it, I replaced it with a link to ~/.config/menus/debian-menu.menu, and now alacarte works with the debian menu.

One down, six to go.


Also, regarding bug 3, I have identified the nature of the fault with XMMS (same problem occurs with Beep Media Player, too) - it is a segmentation fault. Any hints as to why a segmentation fault might occur?

---

### Post by anandakatze on 2006-05-14
[QUOTE=Aielyn]
P.S. Sorry, but this is a pet peeve - The program "Mahjongg" that installs with Ubuntu is not Mahjongg - it is "Mahjongg Tiles", AKA Taipei AKA Shanghai. Mahjongg is a four player tile game similar to Gin Rummy.[/QUOTE]

You might want to look into this:
[http://www.stevens-bradfield.com/MahJong/](http://www.stevens-bradfield.com/MahJong/)

Also, with regard to hibernation, this tends to be pretty flaky in general. Normally one tries to unload modules such as those for the network card, etc. prior to hibernation. Others have tried using software suspend with success:
[http://www.suspend2.net/](http://www.suspend2.net/)

---

### Post by Aielyn on 2006-06-03
[QUOTE=anandakatze]You might want to look into this:
[http://www.stevens-bradfield.com/MahJong/](http://www.stevens-bradfield.com/MahJong/)

Also, with regard to hibernation, this tends to be pretty flaky in general. Normally one tries to unload modules such as those for the network card, etc. prior to hibernation. Others have tried using software suspend with success:
[http://www.suspend2.net/](http://www.suspend2.net/)[/QUOTE]

Thanks for the MahJong info, but I already have that particular game installed. I mentioned it at the end in a "P.S." because it's really just a pet peeve of mine, people leaving off the word "tiles".

As to hibernation: would you be able to direct me to somewhere where there is a step-by-step to unloading modules and hibernating?

Thanks.

---

