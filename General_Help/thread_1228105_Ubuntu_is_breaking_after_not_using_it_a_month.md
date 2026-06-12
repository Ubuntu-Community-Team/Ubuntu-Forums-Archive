---
title: "Ubuntu is breaking after not using it a month"
date: 2009-07-31
forum: General Help
---

### Post by Vostrocity on 2009-07-31
Forget this, close it. I'll fix the problems myself. :)


---


I haven't booted into Ubuntu for about a month :( since I was using a lot of Windows apps and it was more convenient to just use Windows. Well I just now went back to Ubuntu, and the first thing I noticed was that my 20GB Ubuntu partition was at 100% full. So I went into Synaptics and cleared out some apps that I didn't really need. But that didn't help at all (still 100%). So I gave up and booted into GParted and extended my partition to 38GB. Now the disk usage is at a good 52% except everything has gone wonky.
-WiFi no longer auto-connects [fixed]
-The icon font has changed.
-The Applications menu doesn't open (the Places and System do).
-The Update Manager says "Welcome to Ubuntu" as if it was my first time booting it. [fixed]
-Galeon's toolbar configuration went back to default. [fixed]
-I lost my custom folder bookmarks (in the Places folder). [fixed]
-The Temperature panel object also went back to default (graphical instead of text display). [fixed]
Well that's what I've noticed for now. I could try to fix them one by one but I think there's a bigger problem. :o

EDIT 1: The weather display next to the clock also lost my location pref. [fixed]
EDIT 2: Alt+Tab is also broken..
EDIT 3: And so is my column configuration in Process Manager. [fixed]
EDIT 4: Well I'm impatient so I started fixing the problems manually. I guess I could fix all this separately but I'm curious about what caused this in the first place.



EDIT!: Damnit 2 months later this exact same thing happens again! I fill up my partition to 100%, and the exact same things get screwed up! Good thing I remembered this thread and did what I did last time to fix it.

---

### Post by cb951303 on 2009-07-31
To me it looks like, something messed with your config files in your home directory.

---

### Post by egalvan on 2009-07-31
Further, posting the actual fixes would help others in similar situations.

---

### Post by steveneddy on 2009-07-31
So - you were using W7 when this happened?

---

### Post by Vostrocity on 2009-08-01
> **egalvan said:**
> Further, posting the actual fixes would help others in similar situations.
Actually they're simple problems. Most of them are just my settings getting reset to default. The two things that actually broke were the Applications menu and Alt+Tab. For the Apps menu I found [a thread]("http://ubuntuforums.org/showthread.php?t=1166006") where another person was having the same problem. And for Alt+Tab it was just going into Compiz settings and playing around with the Effects settings. So although I fixed all this stuff manually I still don't know what caused them in the first place. :confused:


> **steveneddy said:**
> So - you were using W7 when this happened?
Yep I guess you read my signature. :D

---

