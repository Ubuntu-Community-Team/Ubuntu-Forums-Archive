---
title: "VLC try icon has a white background, how to fix it?"
date: 2010-05-05
forum: General Help
---

### Post by QueenZ on 2010-05-05
So VLC try icon stands out on the default Ubuntu 10.04 Lucid theme with an odd white background.. Is there a way to make it look like the rest so it suites the theme? Do you guys have the same problem?

See my attachment to see what i mean..

---

### Post by palimmo on 2010-05-05
> **QueenZ said:**
> So VLC try icon stands out on the default Ubuntu 10.04 Lucid theme with an odd white background.. Is there a way to make it look like the rest so it suites the theme? Do you guys have the same problem?

See my attachment to see what i mean..

I'm interesting, too!

---

### Post by WorMzy on 2010-05-05
Isn't that just how all windows look with that theme?

Anyway, you can use gnome-color-chooser to gain complete control over the colours GNOME uses.```
sudo apt-get install gnome-color-chooser
``` It will have a menu item under System -> Preferences. Play around with the settings until you get everything to look the way you want.

---

### Post by peculiar penguin on 2010-05-05
He's talking about the panel icon.

Guess the developers were lazy and didn't use an icon with a transparent background?

Desktop Drapes has the same issue.

---

### Post by lotharmat on 2010-05-05
Looking forward to see how this pans out!

---

### Post by QueenZ on 2010-05-05
> **peculiar penguin said:**
> He's talking about the panel icon.

Guess the developers were lazy and didn't use an icon with a transparent background?

Desktop Drapes has the same issue.

you might be right but i don't think we had this problem in previous versions even when a black theme was used, did we?

---

### Post by palimmo on 2010-05-05
> **QueenZ said:**
> you might be right but i don't think we had this problem in previous versions even when a black theme was used, did we?

same problem with ubuntu 9.10...

---

### Post by peculiar penguin on 2010-05-05
Hmmm, so is this user fixable or do we need to annoy the devs by filing bugs for this :mrgreen:
[Here's another thread]("http://ubuntuforums.org/showthread.php?t=1471629"), looks like Banshee does it too?

---

### Post by WorMzy on 2010-05-05
> **peculiar penguin said:**
> He's talking about the panel icon.

Guess the developers were lazy and didn't use an icon with a transparent background?

Desktop Drapes has the same issue.

Oh, I see!

I have that icon too.

---

### Post by QueenZ on 2010-05-05
well temporarily i have got rid of that icon from my tray as i don't really need it and it look ugly..maybe they'll fix it later. If you go to "Preferences" there is an option to hide the system tray icon if you don't want it.

---

### Post by palimmo on 2010-05-11
Same "problem" with Banshee

---

### Post by hanzj on 2010-05-14
A big version of the cone is at [http://upload.wikimedia.org/wikipedia/commons/archive/3/38/20090624181539!VLC_icon.png]("http://upload.wikimedia.org/wikipedia/commons/archive/3/38/20090624181539%21VLC_icon.png")

The background is transparent. But I do not know how to use a different icon for the program

---

### Post by hanzj on 2010-05-14
According to [http://trac.videolan.org/vlc/ticket/3581](http://trac.videolan.org/vlc/ticket/3581),
this is not a bug and therefore cannot be fixed.


courmisch says:

> 

A transparent icon  needs an X11 visual with alpha channel. Unfortunately, VLC needs to disable those otherwise  libQt4-gui will use ARGB visuals also for the video widget. This will  make VLC essentially unable to play videos.

Please retry with 1.1.0-pre1-267-g9f9f6d1 or later.  


---

### Post by Ginsu543 on 2010-05-15
Assuming you're running 10.04 Lucid, give this a try. Download the VLC icon with transparent background as posted by hanzj above. In your menu, go to System --> Preferences --> Main Menu. Click on the Sound & Video tab. Click on VLC and click the "Properties" button. Change the old icon with the new downloaded one. Now, launch VLC and see if the new icon appears in the panel.

If you're running 9.10 Karmic, you will need to copy the new icon to your /usr/share/pixmaps directory where you will find the old icon.

---

### Post by lotharmat on 2010-05-15
It not worky!

---

### Post by VCoolio on 2010-05-15
I think you'll find the tray icon in /usr/share/vlc, probably the 16x16 one. Didn't try myself (I have a white tray anyway), but sounds reasonable, right?

---

### Post by HyperFlexed on 2010-06-28
I'd like to nominate this as the most ridiculous thing ever. It's not a bug? Like hell it's not a bug. I'm chilling with my nice dark desktop, scanning along, when all of a sudden a giant white monstrosity pops out and demands my attention for an inordinate amount of time. Maddening.

If we can't fix the icon, is there a way to prevent it from showing in the tray? This would be just as good for me, as I hardly ever use tray icons and as I understand it, they shouldn't even be a part of ubuntu (from the most recent design documents I've read).

---

### Post by deckoff on 2010-07-02
Same problem here, anyone did anything?
Cant we just change the default icon file?

---

### Post by WorMzy on 2010-07-02
Last I heard, they'd fixed it, or were going to. It's got a transparent background on 9.10, which I'm currently having to use, but I'm not sure if it did before or not..

---

### Post by gerben1 on 2010-07-20
> **HyperFlexed said:**
> 
If we can't fix the icon, is there a way to prevent it from showing in the tray? This would be just as good for me, as I hardly ever use tray icons and as I understand it, they shouldn't even be a part of ubuntu (from the most recent design documents I've read).

Yes, if you do not use the tray icon, as I would assume most people, you can just as well turn it off. 

Start vlc and go to: Tools -> Preferences
and then in the interface section uncheck "systray icon". 
When you restart vlc the tray icon will not show up.

---

### Post by joshdale on 2010-08-20
yeah this is really annoying...but not a huge deal

---

### Post by WorMzy on 2010-08-20
It's been fixed. has been for a little while now. What version of Ubuntu are you using?

---

### Post by sinbin on 2010-08-25
> **WorMzy said:**
> It's been fixed. has been for a little while now. What version of Ubuntu are you using?

I'm using 10.04 and it's still a little annoying problem!

---

### Post by lotharmat on 2010-08-25
> **WorMzy said:**
> It's been fixed. has been for a little while now. What version of Ubuntu are you using?

Still knackered on 10.04 for me too!

---

### Post by sinbin on 2010-08-25
I can report that it's fixed in 10.10. Just upgraded to Maverick

---

### Post by WorMzy on 2010-08-25
It's weird that it's fixed in 9.10 and 10.10 but not 10.04. Unless it is. Do you guys have the most up-to-date version of VLC installed from the repos? If you do then have a look on Launchpad to see if there's a bug report about it. It could be that 10.04 is dependant on the "broken" VLC release, so the update has been held back from it.

---

### Post by Shaggy138 on 2010-10-09
The Drapes icon is still "broken", but VLC and Banshee 1.8.0 are fixed in Ubuntu 10.10. Everything looks really nice besides that :^)
PS. The "Close" button in the about box for Drapes doesn't work.

---

### Post by Midnightsun on 2011-01-31
I can confirm this bug persists in 10.4.  Fresh OS installed yesterday.  I just turned the icon off but it'd be much nicer if I didn't have to.

---

### Post by elliotn on 2011-01-31
Its not fixed am running 10.10 and there latest vlc

---

