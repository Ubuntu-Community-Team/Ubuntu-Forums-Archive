---
title: "Cant turn off sound effects!"
date: 2010-02-14
forum: General Help
---

### Post by stealth17 on 2010-02-14
I'm on Karmic 9.10 and Fluxbox. For some reason the window manager has sound effects for events such as alerts, window closing, etc. which are extremely annoying to me.

I've disabled all sound effects in the gnome control panel. Am I missing something?

It's definitely ubuntu or gnome sound effects too....

---

### Post by switch10 on 2010-02-14
maybe try it as root.........

```
 gksu gnome-volume-control 
```

---

### Post by lidex on 2010-02-14
> **stealth17 said:**
> I'm on Karmic 9.10 and Fluxbox. For some reason the window manager has sound effects for events such as alerts, window closing, etc. which are extremely annoying to me.

I've disabled all sound effects in the gnome control panel. Am I missing something?

It's definitely ubuntu or gnome sound effects too....

Did you make changes in "Sound Preferences"? "Applications>System>Preferences>Sound"

---

### Post by stealth17 on 2010-02-16
> **switch10 said:**
> maybe try it as root.........

```
 gksu gnome-volume-control 
```

Doesn't do anything, just opens a alert saying "Waiting for sound system to respond" and it never does anything.

> **lidex said:**
> Did you make changes in "Sound Preferences"? "Applications>System>Preferences>Sound"

Yup, I have it set to No Sounds and the volume muted.

[attach]147296[/attach]

The weird thing is it doesn't do it in Gnome, only Fluxbox. When you close a window in fluxbox, it sounds like the Ubuntu startup sound. Every time I open a tab in Chrome it makes a click.

What else can I try, I really love fluxbox but the sounds are killing me!

---

### Post by lukjad on 2010-02-16
I know this may sound stupid, but have you tried rebooting?

---

### Post by stealth17 on 2010-02-16
> **lukjad007 said:**
> I know this may sound stupid, but have you tried rebooting?

A few times, yeah. I've even tried resetting the sound theme while in gnome, restart, then boot to gnome again and disable then head to fluxbox. Same out come.

Such a strange issue, fluxbox doesn't have anything in the startup file that would be causing this either. I've been running fluxbox since 6.04 and 9.10 is the first time I've had this happen.

---

### Post by lukjad on 2010-02-18
Well, try locating the hidden files (the ones beginning with a period (fake example: .sound) in you home folder) that pertain to sound and renaming them to something else like .[bak]sound. Then reboot and see if you can work with the sounds. If anything gets messed by renaming them you can just rename them to the original file name.

---

### Post by danboid on 2010-08-08
I'm having this same problem with being unable to disable sfx under lucid fluxbox. I don't get any sfx under GNOME as I've disabled them everywhere, tweaked gstreamer, tried removing pulseaudio etc etc. but still I have these annoying sfx playing which prevent me from starting JACK on the affected card (whatever I set as the ALSA default gets stolen).

On a related note I've got problems using gdmsetup to choose my default window manager. I got it to work once but after having had to change it back to GNOME trying to resolve the sfx prob it doesn't seem to work anymore and no matter what wm I choose to auto-load it just boots into GNOME now. I can still get into other wm's from the gdm login screen tho, just not automatically on boot as chosen by gdmsetup.

---

