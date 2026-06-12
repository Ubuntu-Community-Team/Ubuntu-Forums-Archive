---
title: "Gnome 3 ATI graphics driver issues."
date: 2011-12-30
forum: General Help
---

### Post by cokabear on 2011-12-30
Whenever I install a newer linux distro with the new gnome 3 desktop, the windows move perfectly smooth. But when i install the graphics driver from the 'additional drivers' my windows become all choppy when i move them. I try to remove the drivers again but it doesn't say that they are activated, even though i already activated them. Then I am not able to uninstall them and when i try getting proprietary drivers off the ati website, my computer wont even boot up once i install them and im forced to reinstall ubuntu or any other gnome 3 OS.

This problem does not occur in a gnome2 desktop such as ubuntu10.10

Any ideas? Does this occur to anyone else too, or should i just stick with the older gnome2 desktop operating systems?


I also use an ati hd 5770 graphics card.

---

### Post by 2F4U on 2011-12-30
To find out what driver is used look into /var/log/Xorg.0.log. Here it says what drivers have been tried and whether there have been errors during driver activation or not.
May I ask why you want to install the proprietary drivers when the open source drivers seem to work?

---

### Post by thaelim on 2011-12-30
Why do you need to install the proprietary drivers? The open drivers work (well enough) with Gnome Shell - just start with a clean install and don't install any new drivers...

---

### Post by QIII on 2011-12-30
Well, cokabear...

I just logged out and logged into a GNOME session to find that it looked like doo doo like it did when I first tried the ATI proprietary drivers and decided to just go with KDE.

I know this was an issue some time back.

I'm only up this late because of an irritating cough, so I might not get to it.  But I'll see if I can dig something up for you.

---

