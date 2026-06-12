---
title: "problems with amarok in 9.10"
date: 2009-11-06
forum: General Help
---

### Post by scandido on 2009-11-06
I recently installed 9.10 and installed Amarok. However, when I try to play music files it will not play anything and immediately skips forward in the playlist. The confusing thing is that when I got to sound system configuration and click test on the "output device preferences", I can hear the test sound on every device. 

To debug, I opened Amarok in a terminal and I noticed that when I doubleclick on a song in the playlist to play it, I get the message

xine_open for gapless playback failed!

in the terminal. 

Does anyone have a suggestion as to what might be wrong, or how I can diagnose the problem? Thanks for your time and help.

---

### Post by dkerlee on 2009-11-06
I'm having the same problem!

I get this in the terminal window:
findServiceByDesktopPath: kded/networkstatus.desktop not found

---

### Post by ibs on 2009-11-09
same problem here

---

### Post by GooglieS on 2009-11-16
The same problem... I don't like 9.10 at all! Everything is buggy :(

---

### Post by r-mo on 2009-11-16
Do you have the xine plugins installed?  Amarok will just skip through the tracks if it can't find the codec to play them.

```

sudo apt-get install libxine1-plugins libxine1-all-plugins

```

or just install from synaptic.

---

### Post by tyler.olpin on 2009-11-20
Thanks, that fixed the problem for me.

---

### Post by sieve on 2009-12-09
Worked for me also. Thanks!

---

### Post by morgoth85 on 2009-12-20
Works.
This note should be on amarok site.

---

### Post by Glasairmell on 2010-01-25
This fixed my problem "Amrok could not find any:

**[SIZE=1]"Amarok could't find collection plugins" = keeps	updating forever [/SIZE]**


Thank very much for the solution!  It took a long time searching to find this.  It really needs to be on Amaroks site!

---

### Post by go_beep_yourself on 2010-02-13
+1

:popcorn:

---

### Post by Johannlynx on 2010-06-15
thanks worked for me too.
i had been trying to use amarok and always uninstalled it , feeling frustrated 

thanks again =D>

---

