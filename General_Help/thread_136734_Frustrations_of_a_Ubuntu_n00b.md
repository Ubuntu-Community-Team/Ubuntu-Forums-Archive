---
title: "Frustrations of a Ubuntu n00b"
date: 2006-02-26
forum: General Help
---

### Post by jimhaddon on 2006-02-26
Ok, I have done absolutely everything humanly possible to get this ubuntu working, and now i have finally given up.
Ubuntu really does look like it could be useful software, and one that is worthy of competition, but it just does not work.

I have tried the Ubuntu, and Kubuntu Live discs, and neither one will work.
Then, I tried insalling ubuntu breezy, again nothing.
The final time what Kubuntu dapper, and yet again, all i got was a shell, no desktop system, so i'm afraid until this software has been worked on a little more, so we get a desktop system, im back to good old windows.

Both of the Live cds stopped at hotplug system, to which removing my sound card made it work. 
SO after removal of my soundcard, it then hangs at the end, where it says checking battery state. Looks like it's because my video card isnt supported (ATI X800GT).

The Kubuntu installer, gives me a shell prompt only, and i cant do anything with that. I've tried Sudo Startkde, to which i get cant open ''
cant open ''
cant open''
X-server not found etc...

Maybe in a few years time, the software will work.

---

### Post by simon_is_learning on 2006-02-26
To me it seems as if you have installed a base sysyem.

Just ashore me that you didn't wrote "server" when you installed it.

Becouse typing that will give you only a terminal window with no x-server.

Otherwise I don't know.

---

### Post by az on 2006-02-26
[QUOTE=jimhaddon]Ok, I have done absolutely everything humanly possible to get this ubuntu working, and now i have finally given up.
...

Maybe in a few years time, the software will work.[/QUOTE]


Please file a bug report.

Go here:

[https://launchpad.net/malone](https://launchpad.net/malone)

The package involved is xserver-xorg.

Your sound issue is also another bug.  But let's deal with one thing at a time.


Most people do not see *any* bugs.  I guess you are lucky.

---

### Post by Chemicalvamp on 2006-02-26
i had something simular happen to me when trying to install gentoo & kubuntu onto a hp box.. gentoo didnt even get a grapgical gui up... my solution: switched that hp for my moms gateway.. works great now

---

### Post by jimhaddon on 2006-02-26
Yes, it does look like a base system....

I didnt type anythin!

I just pressed 'install to hard disk'. thats correct right?

I have an ABIT AA8XE Fata1ity Mobo,

---

### Post by davebradford on 2006-02-26
take to it another system and try it out on aleast 4 other computers before you give up!

---

### Post by pestilence on 2006-02-26
After installing (install with a vga=0x317 flag or something) install the **ATI drivers** that should fix your problems.
I had problems booting after the installation (since ati drivers where not installed) after installing everything is ok.

---

### Post by az on 2006-02-26
The x server (the graphical system) should default to perfectly fine 2d graphics.  This is fine for the desktop.  If you need hardware accelerated graphics for games of mass blodshed, install the proprietary ati drivers.  But you should not need this to get to the desktop.  You should boot the installer, reboot and when it is finished setting up, have a graphical desktop.

This is a bug in the x server.

---

### Post by az on 2006-02-26
[QUOTE=jimhaddon]Yes, it does look like a base system....

I didnt type anythin!

I just pressed 'install to hard disk'. thats correct right?

[/QUOTE]

Yes, that is correct.

Since you did not drop a bomb and leave, you seem to be interested in getting this fixed.  W00t!  For now, log in with the username and password you created during the install and run

sudo dpkg-reconfigure xserver-xorg

and enter your password again.  This will try to reconfigure your graphical system.  It will ask you questions.  When it asks what driver, try picking the "vesa" driver.  If it is the one already picked, try the ATI one. continue to the end, picking the default (hit enter)  and then type

sudo /etc/init.d/gdm restart

and see if that works.

---

