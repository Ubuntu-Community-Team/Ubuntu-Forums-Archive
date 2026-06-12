---
title: "Disable automount for USB drive"
date: 2010-02-18
forum: General Help
---

### Post by New2Ubunt on 2010-02-18
[FONT=Times New Roman][SIZE=3]Ubuntu v9.10 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I have a damaged HDD which I want to clone using ddrescue.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I want to attach it via USB connection, otherwise Linux hangs on startup. [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I don't want the O/S to attempt to mount the drive.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I would be happy to disable mounting of all external USB drives.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]How can I achieve this?[/SIZE][/FONT]

---

### Post by byStanderone on 2010-02-18
...open a browser window (places), clik edit>preference>media...check never prompt or start program on media insertion.

---

### Post by New2Ubunt on 2010-02-19
[SIZE=2]Thanks for your response.[/SIZE]
[SIZE=2][/SIZE] 
[FONT=Times New Roman][FONT=Verdana][SIZE=2]I tried this, and I also unchecked Browse media when inserted[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]The partition still seems to have been mounted - icon on Desktop, folder in **/**media[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]This is not while using the damaged drive, I'm using a different USB ext HDD to see what happens.[/SIZE][/FONT]
[/FONT]

---

### Post by rbc on 2010-02-19
Alt + F2, then type in *gconf-editor*, and hit Enter. When that window comes up, navigate to apps-->nautilus-->preferences, then uncheck *media automount*

---

### Post by New2Ubunt on 2010-02-19
Thanks very much, rbc.
 
That worked fine.

---

### Post by byStanderone on 2010-02-20
...thanks as well, rbc

---

### Post by tugsy on 2010-08-02
Is there a way to turn this off when the Desktop is not installed, running command line only. Ubuntu as server 10.4
me scenario.
I have a Smart Card reader that uses a USB device that is set as a Serial reader (virtual via USB) works great normally, but if I reboot at startup with a card in the reader it fails and it won't work unless i reboot without the card in the reader. once its rebooted, insert the card and it starts working again. Hence the need to stop the automount as it is trying to mount a smart card.

---

### Post by Chemtox on 2010-11-11
> **tugsy said:**
> Is there a way to turn this off when the Desktop is not installed, running command line only. Ubuntu as server 10.4


A bit late to the party, but I just had to do this myself.  You can apply the above solution from the CLI with *gconftool-2 --set /apps/nautilus/preferences/media_automount --type bool false*.  This will only work if it's indeed Nautilus (or Gnome Volume Manager/whatever they use this year) what is mounting your card.  If you don't have gconf2 installed, then something else is doing it (also through dbus or directly in fstab?), and this solution won't help you.

---

### Post by cdaringe on 2013-04-15
> **byStanderone said:**
> ...open a browser window (places), clik edit>preference>media...check never prompt or start program on media insertion.

Yahtzee!  Thx.

---

