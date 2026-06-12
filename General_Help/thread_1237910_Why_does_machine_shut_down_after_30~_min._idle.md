---
title: "Why does machine shut down after 30~ min. idle?"
date: 2009-08-11
forum: General Help
---

### Post by duhfactor on 2009-08-11
I've been using ubuntu 8.04 as a convert from XP, and recently, after I leave the computer for a while, it will shut itself down. It didn't do it initially, but recently I added AWN bottom toolbar and compiz to the start up process. I have been using both programs before, without any trouble. The machine before would go to the screen saver, and run on that for hours, then I could start back up where I left off. As near as I can tell, it started happening recently, perhaps when I added the above programs to the start up/boot up sequence. I checked preferences-power management, and the settings are to never shut down on idle. I have to push the "on" button on the computer to fire it up, it will boot up normally, requiring logon, then it will have the file dialogue box open for some reason ( even though it wasn't open when it shut down). When I click on firefox, I will be asked if I want to "restore from a previous session" or something like that. I'm not sure where to look to figure this out. Any ideas?

Thanks in advance,

Duhfactor

---

### Post by llamabr on 2009-08-11
I had a machine that would overheat, and shut itself down.  Is yours getting hot while sitting there running compiz?

---

### Post by duhfactor on 2009-08-13
It doesn't seem to, as it only does it when it's been idle for a while. If I'm using it with heavy programs, and the CPU is runnin' hard, it doesn't have any problems. I probably need to wait and see how long it takes to shut down. Sometimes I'm running amarok streaming music in the background while idle, which restores once I boot up again. hmmmm......

D

---

### Post by steveneddy on 2009-08-13
Look in Power Management

System --> Preferences --> Power Management

and see if the settings for shut down after x minutes idle are set.

Sliding all the way to the right will select Never.

---

### Post by duhfactor on 2009-08-15
I tried those settings, and they are already set to "never". I did find a box in the settings manager for compiz for "session manager" and unchecked it, in the event that had something to do with it.....I'm going to let it run for a bit and see what happens...

D

---

### Post by amac777 on 2009-08-15
Maybe there is a problem with your screensaver? Try to run your screensaver manually to see if the computer shuts off. If it is the screensaver, maybe switch to a different one to see if the problem goes away.

---

### Post by duhfactor on 2009-08-15
> **amac777 said:**
> Maybe there is a problem with your screensaver? Try to run your screensaver manually to see if the computer shuts off. If it is the screensaver, maybe switch to a different one to see if the problem goes away.

Is operating it manually accomplished by simply selecting "preview" by slecting system-->screensaver-->preview?

D

---

### Post by duhfactor on 2009-08-15
BTW, which part of Taiwan are you in? I lived there for a while, hopefully far enough away from the mudslides??

D

---

### Post by duhfactor on 2009-08-15
I just waited idle for the screen saver to come on, and it did without incident. I then started using the computer again, and when the screen saver went off, there was no problem.... I'm guessing this problem may be something other than the screen saver, but I was hoping it was that. I'll let it run a little longer and see what happens since I unchecked the sessions box in compiz... Thanks for the help.

D

---

### Post by amac777 on 2009-08-15
Hmm... doesn't sound like a screen saver problem then. Maybe check the system log to see what happened right before it shut down for clues:

```
less /var/log/syslog
```

I'm in Taipei so luckily we weren't affected by this recent typhoon other than a day off work. I've been living in Taiwan for the last seven years and this place sure does see more than it's fair share of natural disasters. Mostly earthquakes and typhoons but there's a lot of 'em. Which city did you live in?

---

### Post by duhfactor on 2009-08-15
I lived in taipei, lwo dong, I lan, ban chau, and hua lien. I liked taipei quite well,....always action going on...the country towns of hua lien were nice though. Thanks for the help, I need to run for a few hours, I'll check the log and see what I can figure out when I get back...Good to hear things are ok back there....I was in one storm, broke a ship in half...couldn't believe it. Have a good one,

D

---

### Post by duhfactor on 2009-08-16
o.k., interesting, I turned the screen saver off, and the computer doesn't shut down anymore. So it doesssss have something to do with the screen saver after all. It's funny how it would start doing it out of the blue, perhaps Those changes I made to compiz somehow caused it. Should I re-install the screen saver, or just reactivate it??

Thanks,

D

---

