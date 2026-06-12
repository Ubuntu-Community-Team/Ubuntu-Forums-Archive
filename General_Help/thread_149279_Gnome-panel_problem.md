---
title: "Gnome-panel problem"
date: 2006-03-23
forum: General Help
---

### Post by ko16736 on 2006-03-23
So, today I decided to play around with the panels on my desktop. Stupid idea. So I remove everything from the "stock" top panel. Then I make a new panel on the right of the screen and add the "applications, places, system" things. Then I make all of my panels transparent. I had to reset because I needed to go into windows for a sec. I come back to ubuntu and now I can't click on anything in the panel or right click on the panel. I ended gnome-panel and for a split second I could right click but then everything froze. I tried searching for this problem but couldn't find anything relevant. So somone please help me out.

---

### Post by ko16736 on 2006-03-23
no one knows?

---

### Post by barthel on 2006-03-23
[QUOTE=ko16736]So, today I decided to play around with the panels on my desktop. Stupid idea. So I remove everything from the "stock" top panel. Then I make a new panel on the right of the screen and add the "applications, places, system" things. Then I make all of my panels transparent. I had to reset because I needed to go into windows for a sec. I come back to ubuntu and now I can't click on anything in the panel or right click on the panel. I ended gnome-panel and for a split second I could right click but then everything froze. I tried searching for this problem but couldn't find anything relevant. So somone please help me out.[/QUOTE]

This is the best I can offer for you remotely. What I'm going to suggest doing is forcing GNOME to give you back the default panel. However, we will save your existing configurations first so we can put things back later. Things are a bit trickier now because some settings are stored by gconf, so we really want to have some safety backups.

[LIST=1]
[*]Log out if you can. If not, [Ctrl][Alt][Backspace] should work.
[*]Hit [Ctrl][Alt][F1]. (This should bring you to a console login screen.)
[*]Enter you username and password to log in.
[*]If you weren't able to log out, do "killall -HUP gdm". (This may require you to hit [Ctrl][Alt][F1] again to get back to the console)
[*]tar cvzf paranoia.tar.gz .gconf .gnome*  (This is our failsafe backup of everything)
[*]mv .gnome2 gnome2-old
[*]mv .gconf/apps/panel gconf-apps-panel-old
[*]mv .gconf/apps/gnome-settings/gnome-panel gconf-apps-gnome-settings-gnome-panel-old
[*]Hit [Ctrl][Alt][F7] to go back to the gdm login screen and log in. You should now have the default panel back. If so, log out again.
[*]Next, you'll want to restore your old .gnome2 settings--except for the panel2.d subdirectories. Hit [Ctrl][Alt][F1] to go back to the console.
[*]cd .gnome2
[*]rm -ri accels evince gnome-pilot.d keyrings nautilus-scripts share sound totem-addons (and any other directories **except panel2.d**)
[*]rm -i * (to remove all other files)
[*]cd ~/gnome2-old
[*]cp -a [a-oq-z]* ~/.gnome2 (This will copy everything except files/directories starting with "p")
[*]If you have any files starting with p **except panel2.d**, copy them using the "cp -a filename ~/.gnome2" command
[*]Hit [Ctrl][Alt][F7] to go back to the gdm login screen and log in. You should now have your original settings with the default panel back. Hit [Ctrl][Alt][F1] to go back to the console and log out, then return via [Ctrl][Alt][F7].
[/LIST]

Note: for the "rm" commands, I used "-i" for interactive mode for safety. You can use "rm -rf" for the .gnome2 subdirectories if you're confident that you won't delete anything else accidentally.

If you encounter a problem, "tar zxvpf paranoia.tar.gz" will restore your original settings.

Good luck.

---

### Post by go_beep_yourself on 2008-01-14
Has anyone tried this?

---

