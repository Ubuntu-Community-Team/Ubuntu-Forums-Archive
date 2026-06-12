---
title: "New to Ubuntu, multiple problems"
date: 2010-06-20
forum: General Help
---

### Post by j4ss on 2010-06-20
Hi there,

I decided to switch to Linux a while ago. I have tried this several times in the past, but always found myself in the safe arms of MS again. This time, to my surprise, was really fast and easy, all the hardware was detected and installed and I had no problems. I'm using Ubuntu 10.04 on Acer Aspire 5520.

But I have a few now, which I have not been able to solve. I have found similar problems, but no solutions that work.

1) My gnome keeps crashing
When I dim my screen brightness, it usually crashes and sometimes it dims the screen just for no reason itself, usually from bright to darker. I have 'dim display when idle' on in power management, but I am not idle, when it does that. When it crashes the only thing I can do is a hard shutdown by holding down the power button. But if i'm listening to music, for example, then it continues so I guess its a matter of the GUI.

Anyway, I found a kinda half solution to that. It was said somewhere in this forum that its a problem of Compiz, so I disabled it. Have not encountered the problem again. But boy, do I miss compiz. I'm also using AWN dock and it looks just awful without the visual effects. Does anyone know how I could still use compiz? It worked well for almost a week, no problems encountered.

Well, then I thought, why not give KDE a go, but it got me into another kinds of problems, which I'm not going to describe since I think that it should be solvable in theory.

2) Unable to enumerate USB device on port 1 & 2
My console keeps looping me this error, which renders the console almost useless, I can still type, but it keeps flushing me with this error after every character in every tty. All the USB devices actually work. I also see this when I shutdown or boot. I wonder if it writes a log with these errors... about 2 lines in a second.

3) Cannot restart or shutdown from gnome.
If I select any of the two options it just logs out and gives me the welcome screen. To reboot or shutdown I have to go to terminal and 'sudo reboot' or 'sudo shutdown -a now'

4) Sometimes when I boot I dont have sound.
The sound icon in the upper panel shows that the sound is muted, although it is not and I can move the slider but the icon does not change and I cant hear anything.

I'm new to this forum so I'm sorry if the common practice is one problem at a time. I'd be really glad if I could get some help with this, cause i'd really like to use ubuntu instead of windows.

I'd be grateful for any advice!

---

### Post by bobcollard on 2010-06-20
Leave Compiz alone, use Cairo Dock instead of AWN with Gnome Compositor running.
Dimming the screen is part of the Power Manager, the adjustments are in there and the other problem is, if the music keeps on playing either your screensaver or the power manager is allowing your screen to sleep while the application continues.  It's not a crash.
Sorry, cannot help with the rest, but, it is the custom of most forums to list each problem in a separate post.  Hope this helps, if so then put the other problems in a separate post.

---

### Post by Zip247 on 2010-06-20
Use Metacity compositing.  Make sure that compiz is off then,

Open the GNOME Configuration Editor; press Alt-F2 to open the Run Application dialog and type gconf-editor. Click Run. Navigate to Apps->metacity->general. Check the compositing_manager  box, and Metacity will immediately restart with compositing!

---

### Post by j4ss on 2010-06-20
thanks guys, it at least seems not to freeze anymore, and now i have transparency again and i'm able to restart and shutdown from gnome.

yay!

---

### Post by j4ss on 2010-06-20
okay, sorry to bother again, but now i screwed something up I guess.

I removed compiz from ubuntu software manager and set metacity composition from gconf-editor.

The system still froze and after the reboot all window decoration was gone, even the close-minimize buttons on top, plus my cursor was a big X.

When i set the visual effects from the appearance settings to normal I got the buttons and the old familiar cursor back.

Did I do something wrong? It seems okay now again, but i don't know for how long..

---

