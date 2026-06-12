---
title: "No keyboard Layouts in System Settings"
date: 2006-03-09
forum: General Help
---

### Post by Paradoxdruid on 2006-03-09
I recently purchased a new Koala mini mac mini clone from [System76]("http://www.system76.com"), and now my new Koala system is up and running hooked to my TV, playing movies, music, and wirelessly surfing the web. Yay!

However, there are a few little things about the experience that could be improved on, and that I'm still grappling with.

Take, for instance, the fact that I have no keyboard layouts available by default. In Kubuntu, I go to System Settings -> Regions and Localization --> Keyboard Layouts. The area is blank, without even a current keyboard layout listed.

Searching online, they suggest making sure there are proper symbolic links in the /etc/X11/xkb/rules/ folder... but those are already there. In fact, if I open the xorg.lst file, I can see the keyboard layouts, including the one I want, logicdp (Logitech Desktop Wireless Pro, which a quick google search informs me would run my Logitech Wireless EX 110 combo just fine). All these layouts should be in the Kubuntu system settings menu.

So I tried the command line option:
Code:
setxkbmap -layout logicdp
No luck, it says "Error loading keymap description".

And keymaps are such a basic part of the xorg installation, I'm having trouble diagnosing how to reinstall or fix them-- everybody else just has them.

Might anyone have any advice?  Thanks!

---

### Post by Heliix on 2006-03-09
i don't like those graphical applications on system or environment settings. i argued with the gnome applets for some time, if they work it's just fine but if not-they aren't transparent enough (well, my oppinion)

 i'd advice to edit the /etc/X11/xorg.conf file directly, section  Keyboard layout.. you may choose more than one layout
if you brouse ubuntu forums, there are *plenty* of howtos on keyboard settings. i'm pretty sure there is the right keymap already installed but maybe you don't know its right name (such as cz_qwerty versus cz-qwerty or even qwerty-cz for czech keyboards)

remember our good Google ;-)

---

### Post by crichell on 2006-03-09
I posted in the System76 forums as well but this thread will solve the issue.

[http://ubuntuforums.org/showpost.php?p=563129&postcount=18]("http://ubuntuforums.org/showpost.php?p=563129&postcount=18")

Strangely Ubuntu can read in the keycodes and assign them where as Kubuntu can not.  Doesn't make a lot of sense but we're hoping it's solved in Kubuntu Dapper.

---

### Post by StratosL on 2006-03-09
Hi there. This may have to do with a known bug, which has been reported many times here at the forums and also the support list. It is kubuntu specific, not a general kde problem. 

Try to see if this fixes your problem:

cd /usr/share/X11/
sudo ln -s /etc/X11/xkb/ xkb

This particular bug came up with the first 3.5.1 packages and it is not corrected yet.

regards,
stratos

---

### Post by Paradoxdruid on 2006-03-10
[QUOTE=StratosL]Try to see if this fixes your problem:

cd /usr/share/X11/
sudo ln -s /etc/X11/xkb/ xkb
[/QUOTE]

Thanks, Stratos.  Those two little commands made everything work perfectly.

---

### Post by lodp on 2006-03-11
worked great for me too, many thanks - i had the same problem after updating to kde 3.5.1, plus the kde keyboard tool switch disappeared and couldn't be recovered. i ended up with my keyboard being switched to hebrew and not being able to switch it back.. luckily restarting kde switched back to regular (i would have been totally boned otherwise).

has this bug been reported in the right places? i don't even know what the right places are...

---

### Post by zupermanz on 2006-05-27
[QUOTE=StratosL]
Try to see if this fixes your problem:

cd /usr/share/X11/
sudo ln -s /etc/X11/xkb/ xkb

This particular bug came up with the first 3.5.1 packages and it is not corrected yet.

[/QUOTE]
Thanx  Stratos!

---

### Post by bmralex on 2007-02-07
Hi,
I am running KDE and have the same problem: no keyboard layouts available in Settings->Regional&Accessibility->Keyboard Layout.
The method recommended by StratosL did not fix the problem.
Please, help
Thanks

---

