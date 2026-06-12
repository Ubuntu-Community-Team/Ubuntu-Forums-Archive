---
title: "Can I completely disable the Assistive Technologies?"
date: 2010-07-31
forum: General Help
---

### Post by Heathicus on 2010-07-31
We have two very young children and we often let them play games (such as those at the Nick Jr. website) on my computer.  I have a user account just for them when I log them on to play their games.  Except for when they are playing, or when I'm using the computer, the screen is locked and typically at the user login screen.  But, they will sometimes sit down and "mess" with the computer anyway (typically begging to play their games).  It hasn't been a problem since they couldn't do anything unless I logged them on.  But somehow, they have found the "Universal Access Preferences" button and have started causing chaos!  Several times now, they have turned on the screen magnifier.  And for some reason on my computer, that thing doesn't work.  When it is on, half of the screen is a garbled mess and I can't even log on.  I can see part of the logon box on the left half of the screen, but it does not accept my password.  The first time it happened, the only way I could log in to the computer was to start in recovery mode, then choose continue normal startup, enter my username and password, then run the startx command.  It took me about an hour to figure out what the problem was the first time it happened.    I can go to System -> Preferences -> Assistive Technologies and uncheck all of the boxes there, but on the user login screen, that icon is still there at the bottom and the kids are still opening it and clicking and messing things up.  I don't need any assistive technologies so I want that icon to go away!  Can that be done??  I'm running Ubuntu 10.04.

---

### Post by stinkeye on 2010-07-31
In **gconf-editor > /desktop/gnome/lockdown/disable_user_switching** you can disable user switching.
This disables the *switch user* tab when you lock the screen so they can't get to the login screen which shows the "Universal Access Preferences" button.
You can still switch users when your logged in using the menu bar or main menu applet.
System > logout.

---

### Post by Heathicus on 2010-07-31
Is that the only way?  I'd rather not go that route if there's another option.  Often, I will lock the screen when I leave the computer (such as when I go to work), then from there my wife (or my older kid) will use the switch user to switch to another login.

---

### Post by marshmallow1304 on 2010-07-31
Removing gnome-mag and libgnome-mag2 makes the screen magnification option go away, but it doesn't get rid of the whole Assistive Technologies button/dialog.

---

### Post by Heathicus on 2010-08-01
That would certainly help.  I'm still a Linux newb and have only been running it a couple months now trying to stay in the gui.  So pardon my ignorance, but how do I remove gnome-mag and libgnome-mag2?

---

### Post by marshmallow1304 on 2010-08-03
System->Administration->Synaptic Package Manager
Put gnome-mag in the search bar, right click the package, and remove.
Put libgnome-mag2 in the search bar, right click the package, and remove.

---

### Post by Maverick_Meerkat on 2010-08-03
Greetings, 

1. You can remove the shortcut/launcher from the desktop drop-down menu using the menu editor.

2. Download and install Ubuntu Tweak. Get it here: [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

There is a menu entry for Auto Start Programs. You can clear the checkbox for Visual Assistance. That will prevent the service from loading at boot time.

BTW you may have to run Ubuntu Tweak with root privileges "gksu ubuntu-tweak" or add the "gksu " to the shortcut/launcher properties in the menu editor.

There is a Terminal/CLI app to turn off braille, tty, & speech services as well, but that is probably over-kill for your situation.

---

### Post by Lavahead on 2010-08-03
I removed the entire "Assistive Technologies" in Synaptics Pkg Manager. Search for "at-spi" (not including quotations). Mark all applicable files for removal, and apply. Should be completely gone after that.

---

### Post by RodaKoRn on 2011-04-01
Hi!

I tried everything said here to get rid of the universal access icon on the login screen and nothing worked.

Finally I found the solution.

 * As root edit the file /var/lib/gdm/.gconf.mandatory/%gconf-tree.xml
 * Modify the value of the entry name "enable" to false:

<dir name="accessibility">
  <dir name="keyboard">
    <entry name="enable" ... type="bool" value="[COLOR="Blue"]false[/COLOR]"/>
  </dir>
</dir>

Save and reboot.

---

### Post by stinkeye on 2011-04-01
Thanks. Tried it and it works.
=D>

---

