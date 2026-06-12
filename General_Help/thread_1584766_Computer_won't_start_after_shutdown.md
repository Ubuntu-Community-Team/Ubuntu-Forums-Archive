---
title: "Computer won't start after shutdown"
date: 2010-09-29
forum: General Help
---

### Post by jpietari on 2010-09-29
Sometimes when I shutdown Ubuntu 10.10 and try to turn on the desktop PC it fails.  I then have to disconnect tower from the power source and plug it in after waiting a few minutes.  This problem first started in Ubuntu 9.10.  I have a hunch that it happens because I am shutting down with applications open.

I was told that this is a batter issue on my motherboard, but I've replaced it and still have issues.

---

### Post by hesder on 2010-09-29
When you shutdown and wait a few minutes the system does not work like when you shutdown and disconnect the power source?

Have you tried putting your bios back to default settings?

Most bios also have a safe-setting, have you tried this?

---

### Post by hrickh on 2010-09-29
I doubt it has anything to do with shutting down your machine with an application still running. 

Have you looked at your log files? Go through them and look for anything out of the ordinary at the times you shut down. You can view them by going to System > Administration > Log File Viewer.

R.
==

---

### Post by jpietari on 2010-09-30
I will take a look at the BIOS settings and the log files.

It could be a BIOS setting as I was messing around in it just before the problem started.

---

### Post by jpietari on 2010-09-30
hesder, it is weird.  Shutting down my PC and waiting a few minutes doesn't seem to have the same effect as turning off the power source from the back of the PC.

This is exactly what I have to do to get it to start.
1. I shutdown Ubuntu and everything seems to work fine
2. A few hours later I hit the power button on my desktop.  It tries to start (I hear the fan kick in), but almost immediately it turns off.
3. I hit the power button again on my desktop, but nothing happens.
4. I turn off the power button on the back of the pc, wait to hear a faint sound (< 10 seconds) then hit the power on the back of the pc.
5. I now wait a couple minutes then turn on the PC.

---

### Post by hesder on 2010-10-02
Have you tested your pc with default and save settings already as suggested in my previous post? 

Because you have been messing around with the bios settings, changes are its something related. Just try default and after that save settings to be sure... settings can alway be put back after this test.

---

### Post by sheffrem on 2010-10-02
Very often this type problems are caused by a dying Power Supply. Even after changing your motherboard if the power that come in is not enough it will be the same. i advice that you get another power suply to try on your pc. after connecting a different power supply just boot up your pc when linux come up,just restart do the same and then shutdown and try putting it on again and see.

---

