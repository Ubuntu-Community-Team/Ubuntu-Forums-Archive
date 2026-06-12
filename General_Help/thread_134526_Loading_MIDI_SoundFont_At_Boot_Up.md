---
title: "Loading MIDI SoundFont At Boot Up"
date: 2006-02-22
forum: General Help
---

### Post by johnnymo87 on 2006-02-22
Hi,

I need my MIDI soundfont to load at boot up. Right now I need to open a terminal and type *sudo sfxload /home/jcm05003/"Sound Font Ultimate"/Ultimate.SF2* before any MIDI files work. Any suggestions?

---

### Post by valadil on 2006-02-22
Scripts in /etc/rc2.d will be run at bootup, so you just have to dump that command in there.  Make a text file, call it S99midi, put your command in there (it doesn't need sudo thought since its being run as root) and chmod +x it.

---

### Post by nanotube on 2006-02-22
sorry valadil, that is not quite the correct way to do it.
you should place your script into /etc/init.d/
and then make a link to that script in /etc/rc2.d
there is even a program called "update-rc.d" that you can use to automatically create/remove symlinks to your startup scripts at various runlevels. 

so, what you would do is create a shell script with that command, and place it into a file /etc/init.d/loadmymidi
and chmod it to executable. then you can run command 
```
sudo update-rc.d loadmymidi defaults 99
```
and that would place proper symlinks to your script into various rc dirs, with reasonable defaults. and with a late start order (99).

---

