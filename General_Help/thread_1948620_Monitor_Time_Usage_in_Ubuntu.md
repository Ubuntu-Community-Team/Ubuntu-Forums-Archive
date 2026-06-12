---
title: "Monitor Time Usage in Ubuntu"
date: 2012-03-28
forum: General Help
---

### Post by Aqil on 2012-03-28
My computer serves as my main working tool, but also as an entertainment machine, telephone and more. If I'm home, I'm probably at the computer.

Therefore, I'd like very much to keep track of how I use my time at the computer. Is there any software that can help me do this? I'm not sure what the most practical solution would be, but I could imagine logging something of the following.

- Keystroke logger.
- Which programs are open at a given point? Save metadata periodically.
- Which website is open at a given time? Log periodically.
- Print Screen periodically and save as image.
- Is the computer on?
- Is the computer in energy saving mode?

Periodically could perhaps mean every five minutes.

I managed to extract some sqlite3 data from Chromium history but what I've seen so far it's not as detailed as I hoped for. It only has date/time for the last visit to a website that you visited several times, correct me if I'm wrong. I might also try the same on Skype.

Ideally, I'd like the data in .csv format or something similar, so that I easily can make statistical analysis and pretty graphs of how my time is spend.

Let the creativity flow. Do you have any good ideas?

---

### Post by Aqil on 2012-03-28
I should have searched more before asking. Found a little program called arbtt (for Automatic Rule Based Time Tracker) which seems awesome. I installed it through Ubuntu Software Center, but I think I'm gonna need some help to get through the setting up process, which ironically seems to take a lot of time.

Reading this guide but I'm not getting the hang of it: [http://darcs.nomeata.de/arbtt/doc/users_guide/](http://darcs.nomeata.de/arbtt/doc/users_guide/)

I opened the terminal and wrote as follows:
> aqil@Computer:~$ arbtt-capture
Why no respons?



^[
^[
^[
^[
what?
help
wtf?
arbtt-capture.desktop
arbtt-stats
^C
aqil@Computer:~$

I don't know what happened, if anything? I searched for arbtt in the dash, and got nothing. How do I get this thing starting? And if the arbtt-capture.desktop file isn't there, how can I copy it to ~/.config/autostart/ like the guide advises?

Sorry for being so amateurish, but I gotta learn this stuff sometime, and sometime is hopefully now. I'm sure this is trivial to you.

---

### Post by majordread on 2012-03-28
If you set up a Conky file, which there are many posts for in these forums, you can have it show your system uptime. I have it set on mine as you can see about half way down in the screen shot :

---

### Post by squilookle on 2012-03-28
Also KTimeTracker if you want/don't mind something that is integrated with KDE.

---

### Post by jim_deadlock on 2012-03-28
How about the Hamster Time Tracker hamster-applet

---

### Post by Aqil on 2012-03-29
**Conky** seems like a cool thing to have, but I'm not so sure it's what I'm looking for. Does it log system uptime into a .csv file for me to watch it retroactively? I have little use for seeing it in real time.

**KTimeTracker** seems good because it apparently has a function that automatically changes the activity when you change the active application. So I tried downloading it from the Software center. But when I open it from the Dash it just gives me *Error: Could not create the KTimeTracker part*, probably because I use gnome and not KDE. I don't mind changing if that doesn't come with any negative side effects. I'll look into it.

**Hamster Time Tracker** seems to be popular, but requires you to type in your activity whenever you change it, and that takes to much time and effort.

I really need something that **logs** time usage **automatically**. I have enough to think about without having to keep in mind all the time that I need to log whatever I'm doing. Also, what people say and what they do is not always the same, and I would be naive to think that doesn't apply to myself.

I'd especially appreciate any further help on arbtt or KTimeTracker.

Thank You!

---

### Post by Habitual on 2012-03-29
> **Aqil said:**
> **Conky** seems like a cool thing to have, but I'm not so sure it's what I'm looking for. Does it log system uptime into a .csv file for me to watch it retroactively? I have little use for seeing it in real time....

You'd have to code an external script to parse the uptime data into a .csv file. This can be done without Conky and you wouldn't even need to install it (unless there's some other useful functions in it that are applicable to your over-all solution). [http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html) for those metrics.

sar from the sysstat package could probably do this as well, (still have to code something for .csv file)
But the beauty of sar is that it retains 7 days (by default) of LOTS of metric data about the system (NOT user-specific data however). See [http://sebastien.godard.pagesperso-orange.fr/features.html](http://sebastien.godard.pagesperso-orange.fr/features.html) for 

HTH.

---

### Post by Aqil on 2012-03-29
I'm getting closer to making sense of arbtt now.

Here's how it works (if anyone happens to have the same problems):

Typing **arbtt-capture** in the terminal does start the data collecting. It just doesn't give you any feedback. I still didn't figure out how to autostart it.

It saves the data in a hidden folder, namely ~/home/.arbtt/capture.log which I found difficult to read. Opening it in gedit text editor, it's a lot of gibberish and no log viewer seems to be able to read it. The developer promotes his function arbtt-stats for reporting, but I find the **arbtt-dump** command more useful. It prints all the data in the terminal and then you can copy and paste to a text file and then import to Libre Calc or whatever.

Here's a sample for you:

> TimeLogEntry {tlTime = 2012-03-29 13:44:15.01513 UTC, tlRate = 60000, tlData = CaptureData {cWindows = [(False,"Desktop","desktop_window"),(False,"DNDCollectionWindow",""),(False,"launcher",""),(False,"panel",""),(True,"[ubuntu] Monitor Time Usage in Ubuntu - Ubuntu Forums - Chromium","chromium-browser"),(False,"Dash",""),(False,".arbtt","nautilus"),(False,"aqil@Computer: ~","gnome-terminal"),(False,"aqil@Computer: ~","gnome-terminal")], cLastActivity = 10272}}
TimeLogEntry {tlTime = 2012-03-29 13:45:15.098806 UTC, tlRate = 60000, tlData = CaptureData {cWindows = [(False,"Desktop","desktop_window"),(False,"DNDCollectionWindow",""),(False,"launcher",""),(False,"panel",""),(True,"SYSSTAT - Chromium","chromium-browser"),(False,"Dash",""),(False,".arbtt","nautilus"),(False,"aqil@Computer: ~","gnome-terminal"),(False,"aqil@Computer: ~","gnome-terminal")], cLastActivity = 2459}}


Now I just have to interpret, transform and eventually analyze. Perhaps I'll even learn to change the settings eventually. I think arbtt will work well for me, but I might use some of your ideas as a complement. So thank you all for your time and effort! And keep shooting good ideas if you have them. Logging system performance seems like a good idea, not only for the sake of time management.

---

