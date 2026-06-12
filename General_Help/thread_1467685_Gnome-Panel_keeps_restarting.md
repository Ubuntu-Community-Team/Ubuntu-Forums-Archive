---
title: "Gnome-Panel keeps restarting"
date: 2010-05-01
forum: General Help
---

### Post by sheehanje on 2010-05-01
I'm having a weird problem on Ubuntu 10.04 64bit.  Right now gnome-panel is in a constant crash, start loop.  The PIDs for gnome-panel and a few of the other applets keep going up, and I can't access the panel at all.

This is a fresh install.  I installed the restricted drivers for ATI, I added a few programs (VLC, Flash, etc).

The last two things I did was created a launcher to eject the cd-rom, and then I put in a DVD to test playback.  All of a sudden the panel disappeared and went into an endless start/stop loop.

I restarted Ubuntu, and upon logging in, I noticed the panel wasn't displaying and the screen kept flickering.  I went to terminal and kept running 'ps -A'  to confirm my suspicion that the panel was crashing.  And it was as the PID keeps rising.

Anyone experiencing anything similar right now?

---

### Post by WorMzy on 2010-05-01
Try running 'pkill gnome-panel && gnome-panel' in a terminal, and see if you get an error message.

I'm using x64 Lucid, and I've had no problems with gnome-panel.

---

### Post by sheehanje on 2010-05-01
I ran it a few times.  It finally killed the cycle, but I can't start it from a terminal as I'm getting a Gtk-WARNING **: cannot open display

---

### Post by sheehanje on 2010-05-01
Ok, I created a luancher to start gnome-terminal after I came to my senses a bit.

After running pkill then restarting gnome-panel from gnome-terminal, I get the following:

Gtk:ERROR:/build/gtk+2.0-2.20.0/gtk/gtkrecentmanager.c:1395:get_icon_fallback: assertion failed:  (retval != NULL)

---

### Post by WorMzy on 2010-05-01
This topic might help: [http://ubuntuforums.org/showthread.php?t=392387](http://ubuntuforums.org/showthread.php?t=392387)

In particular, the solution suggested by acesabe, which apparently reverts your gnome-panel config to the default settings by simply removing the gconf folder containing the configuration. You'll lose your changes, but it should fix the problem.

I haven't tried it myself, but I think it'll work. Probably best to back up the directory first.

---

### Post by sheehanje on 2010-05-01
That didn't work either.  I even tried:

sudo apt-get purge gnome-panel

then 

sudo apt-get install gnome-panel


One thing I was able to do was to bring up gnome-panel using sudo.. So it was obviously using configs in /root

I then loaded midnight commander to do a comparison between the two directories, and tried deleting all the .whatever files related to launching the gnome panel.. nothing...

Very confused on this one, I will give it another go in the morning.  If I can't figure it out, I will probably just reinstall...  Maybe if I get daring, I will try to recreate the problem with the last two steps I did before it crashed and if I get it to repeat, I'll file a bug report.

---

### Post by WorMzy on 2010-05-01
Did you do 'gconftool-2 --shutdown'? Because that bit's important. Do it after you've removed ~/.gconf/apps/panel and it'll force gconf to load the default settings. I tried it myself, and it worked fine.

---

