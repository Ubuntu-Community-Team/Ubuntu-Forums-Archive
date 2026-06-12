---
title: "How to Remove a Menu Item from Terminal"
date: 2011-07-12
forum: General Help
---

### Post by Azdour on 2011-07-12
Hi,

I'm looking for a way from the terminal to remove certain menu items from the System | Administration for certain users. I'm working with a CyberCafe style application so user accounts come and go and I wanted to see if I can set it up that after an account is created that it will do some customisations.

I've found examples of adding menu items but nothing specific to removing via the terminal.

I think I may already know the answer to this. The Alacarte application simply manages the XML in the settings.menu to hide menu items and that if I want to do any customisations from the terminal I will need to play with this XML file to hide things.

I just wondered if anyone else has any suggestions? I'd like the customisation per user rather than a blanket removal for all users, thanks.

---

### Post by CatKiller on 2011-07-12
If the user isn't a member of the admin group then the Administration menu is pretty pared-down anyway.

Removing an entry is exactly the same as creating an entry, except that you put Hidden=True in the .desktop file (IIRC. I'm not at my own computer atm).

---

### Post by Azdour on 2011-07-12
Hi,

Sorry, in my rush to post my original request I included the wrong menu.

I would like to remove Preferences | Network Proxy from the accounts we create on the fly. The panels are locked down so the user cannot add it back. It just makes it slightly more difficult for them to play with the proxy :) Someone with more knowledge would be able to get around this so I am not looking at making it impossible to get to Network Proxy just looking for a way to make it more difficult for your 'average' user to access.

I have also been toying with the idea of making gnome-network-properties executable only by a superuser but I do not know what impact/effect that will have on the server.

---

### Post by CatKiller on 2011-07-12
(Back at my own computer now. Checking the Ubuntu Forums at work is bad form.)

All menu entries are .desktop files in /usr/share/applications (and potentially some other places for legacy reasons). When you edit the menu entries, a copy of that .desktop file is stored in that user's Home folder (~/.local/share/applications) with the changes applied. This can include the Hidden attribute. Because the per-user entries are queried first, the per-user menu entry gets used instead of the system-wide menu entry. There's a [specification]("http://standards.freedesktop.org/desktop-entry-spec/latest/") for .desktop files, if you're interested.

You could create the appropriate .desktop files and then put them in the appropriate place in /etc/skel (the directory that's used to propagate a new user's Home folder). This would hide the menu entry for the user, but wouldn't stop them launching the program if they already knew what it was called, and wouldn't by itself stop them from editing the menu to put it back. You could probably make the ~/.local/share/applications directory read-only, though. That would probably help.

An alternative would be to make the particular /usr/share/applications .desktop file readable only by a particular group. I don't know for sure that the bit that indexes those files into a menu runs as the user, so you'd need to check that. Again, wouldn't stop a user from running the application if they already knew what it was called.

A think that, to some extent, control over how locked-down a particular user should be is largely a solved problem. I believe it's generally referred to as "kiosk mode," but it's not something that I've looked into particularly.

---

### Post by Azdour on 2011-07-13
Hi,

Thanks for info, it seems this is a better way than for me to try and manipulate the XML .

---

