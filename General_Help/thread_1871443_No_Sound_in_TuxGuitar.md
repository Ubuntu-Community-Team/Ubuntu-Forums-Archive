---
title: "No Sound in TuxGuitar"
date: 2011-10-28
forum: General Help
---

### Post by Jaybyrrd on 2011-10-28
Ok so Ubuntu Oneiric Ocelot there is no sound on Tuxguitar, this is what I receive by running from terminal:


(java:8454): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(java:8454): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(java:8454): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(java:8454): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
/dev/sequencer: No such file or directory


My guess is that there is a new or different file for Ubuntu 11.10 as I have done modprobe snd-seq. Any ideas? I really want sound! Thanks a ton!

---

### Post by satanselbow on 2011-10-29
Your post title mentions Tuxguitar but your query reads like you have no sound in the OS at all...

For tuxguitar you will want to install timidity midi server

```
sudo apt-get install timidity
```

and ensure it is running before firing up TuxG

```
sudo /etc/init.d/timidity restart
```

---

### Post by Jaybyrrd on 2011-10-29
Ok and you are right, that is a typo I will edit, I did add Timidity before,but I didn't do the second command, so I will see if that makes it work.


Edit: Still no sound yet but the terminal now reads:

(java:8454): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(java:8454): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(java:8454): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(java:8454): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


The dev/sequenceer part no longer shows up. :/

---

### Post by gigabz666 on 2011-10-29
Sorry to the OP but I'm also having the same issue and haven't come up with a resolution yet. I've restarted timidity and I still get the issue with /dev/sequencer. I have also tried using fluidsynth since other people have claimed it works but not having any luck.

EDIT: And as always I manage to solve it within minutes after posting. Try to install tuxguitar-jsa, then make sure you restart tuxguitar if its already running. Now go to settings and then click on sound. Change the MIDI Sequencer to the Real Time Seqeuncer (I believe Tux Sequencer was the only option available before hand) and change the MIDI Port to Gervill. In my case this is working and I'm now getting sound.

---

### Post by Jaybyrrd on 2011-10-29
> **gigabz666 said:**
> Sorry to the OP but I'm also having the same issue and haven't come up with a resolution yet. I've restarted timidity and I still get the issue with /dev/sequencer. I have also tried using fluidsynth since other people have claimed it works but not having any luck.

EDIT: And as always I manage to solve it within minutes after posting. Try to install tuxguitar-jsa, then make sure you restart tuxguitar if its already running. Now go to settings and then click on sound. Change the MIDI Sequencer to the Real Time Seqeuncer (I believe Tux Sequencer was the only option available before hand) and change the MIDI Port to Gervill. In my case this is working and I'm now getting sound.

Dude you are the best! Thank you so much worked perfectly, marking as solved!

---

