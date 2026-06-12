---
title: "power management issue?"
date: 2006-06-03
forum: General Help
---

### Post by andrewcox on 2006-06-03
hey everyone

i'm a 30 hour convert from windows so bear with me if i don't associate
things properly

i initially installed 5.10 and upgraded immediately to dapper because i
knew there was an available upgrade.  i have pretty much everything
running (minus tv tuner which i can't even begin to talk about how
frustrated that made me) but i'm having an issue with power management.
 i've already changed the power management preferences to 'never' put my monitor on standby, but when i'm idle for 20 minute it goes to standby without
fail. i changed the preference to place on standby after 1 minute and
it did not.. it waited for the 20 minute mark.. is this a problem many
people are having or am i the only one with this bug.  i changed the preference through the system > preferences > power management.

if you need me to post anything here just let me know and i'll do it
promptly

-andrew

ps if you can fix the tv tuner issue (hauppauge pvr-250) let me know
too ;]

---

### Post by Sirkent on 2006-06-03
Are you sure there isn't a power management setting in your BIOS which is causing this?

---

### Post by andrewcox on 2006-06-03
quite sure. it's never happened before.  also because the monitor didn't go to standby while i upgraded and i wasn't even at my pc

---

### Post by andrewcox on 2006-06-04
well i figured that it was a conflic with the xorg.conf.  i'm still looking for ideas about that hauppauge on an amd 64bit  ](*,)

---

### Post by HotShot on 2006-06-05
i have the same problem with my ibm t20 notebook. the monitor goes off after some minutes. i changed the power management settings, checked the bios and disabled the gnome-power-manager.

can you give me some details about the conflict with the xorg.conf?

---

### Post by _simon_ on 2006-06-05
1. take a look in /etc/X11/xorg.conf at your monitor section, if it has DPMS, try commenting it out.

i.e.

# DPMS

2. check screensaver slider is set to "never"

3. Open the configuration editor, if it's not in System Tools then from terminal: gconf-editor

apps -> gnome-power-manager and take a look at what's ticked.

Mine does not blank, see the attachment for my settings.

---

### Post by andrewcox on 2006-06-05
i did exactly what simon said about commenting out that one line and it worked like a charm.

---

### Post by _simon_ on 2006-06-05
glad that worked for you :)

---

### Post by varunus on 2006-06-05
Did you try the IVTV drivers for your card?  It should be supported...though they're a little tricky to set up on Dapper.  I've gotten it working, though, with my PVR-150 (though i'm on 32 bit Ubuntu).

---

