---
title: "Firefox Text Rendering - Invisible Text"
date: 2010-11-10
forum: General Help
---

### Post by cyqotiq on 2010-11-10
After a routine system update using the Update Manager, Firefox froze.  I killed it using the 'kill' command, but when I restarted Firefox, the text no longer rendered... at all.  I've attached a screenshot.

I've looked through the forums, and the closest thing I can find is a problem that seemed to deal with improper LCD rendering or compatibility issues related to the Ubuntu Add-On.  I didn't install any new add-ons into Firefox, so I'm guessing an update to some library is causing problems.

I verified my Pango installation by typing
```
sudo apt-get install libpango1.0-common
```

This results in the following response:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libpango1.0-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

I'm currently using Chromium as my browser, and am quite pleased with it.  But after installing Eclipse this afternoon, I've discovered the exact same behavior from the Eclipse Welcome screen.  I'm curious if Eclipse is using Firefox's rendering engine to display their welcome screen.

---

### Post by cipherboy_loc on 2010-11-10
What version of Firefox? I am using the 4.0b, and that sometimes happens (but only in the reply to thread text box). It does not happen with anything else though.


Cipherboy

---

### Post by cyqotiq on 2010-11-10
I'm running Firefox 3.6.12 and it's branded as "Firefox for Ubuntu Canonical - 1.0" (Default installation with Ubuntu 10.10

This problem happens every time I launch Firefox and happens with ALL text-rendering inside the browser panel.  The UI elements render with no problem.

---

### Post by cyqotiq on 2010-11-26
Update:

I am still experiencing the problem with invisible text rendering in the Firefox web document.  As I mentioned in my first message, Eclipse has also begun to show signs of a similar problem.  I've posted screenshots to demonstrate how both Firefox and Eclipse look.  There is also a windows screenshot showing that the Windows version of Firefox runs over Wine and using the same add-ons as I have installed on Ubuntu.  The Windows version runs with no problem.

I still haven't found any information on why this happening.  I have uninstall all Firefox Add-ons and then uninstalled Firefox.  I will soon be re-installing Firefox once I have cleared out any old cache and config files.

---

### Post by daveduncan on 2010-12-08
Experiencing exactly the same problem after my first update (just went over to Ubuntu this week). Thought it was a firefox problem, uninstalled firefox and loaded several other browsers - all did the same thing. Installed Chromium, which is working perfectly.

---

### Post by daveduncan on 2010-12-09
The problem has now extended to emails in Thunderbird with remote content.Pic attached. I'm beginning to tear my hair out :(.

---

### Post by daveduncan on 2010-12-10
After running firefox using the terminal, I was able to figure out that this was caused by .ttf fonts that I had attempted to install. Disabling the offending fonts fixed the problem.:p

---

