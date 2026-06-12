---
title: "after update wont start checking battery state"
date: 2011-04-29
forum: General Help
---

### Post by luvgirl12345 on 2011-04-29
I just updated to 11.04... well I wanted to  :( I got the message checking battery state. I used google and found out it has to do something with fglrx (or whatever) so I thought I was really smart and did sudo apt-get remove fglrx after using alt + f1 to get into the terminal... but now I cant do anything anymore!! when I boot the pc a purple screen appears (without ubuntu logo or anything, cant get into terminal mode) then it shows the no signal window from my monitor and I get a black screen... It didn't shut off though!! the fans are spinning and everything but nothing happens when i press alt + f1... When turning off the computer (quick press on power button) the ubuntu screen shows with the dots...


HELP!!!

---

### Post by VipArt on 2011-05-01
same problem here. After upgrading from maverick to 11.04 got the message when starting ubuntu and the system hangs.

Tried reinstalling gdm and xorg - no help.

/etc/X11/default-display-manager show only one line as expected: /usr/sbin/gdm

Please help since new shiny 11.04 doens't boot... :(

---

### Post by luvgirl12345 on 2011-05-01
Well I fixed my computer!  If you can get into grub with shift then try recovery mode and use fallback graphics. Then completely uninstall fglrx and get the new drivers from ati. If that doesn't work try ctrl alt f1 and screw around in there lol

Classic gnome  still doesn't work for me: massive flicker... ctrl alt f1 then type unity --replace

Hope that helps

---

### Post by eeverson on 2011-07-13
I have just had a similar issue... I am guessing my issue relates to Gnome 3 and auto login.

The fix I found was... Start up in recovery mode then select failsafe x. Login as your normal user..

Once in Gnome (3) I edited my user account and turned off auto login.

Restarted and everything works.

Cheers
Euge

---

