---
title: "Ubuntu just... um... idk?"
date: 2010-01-20
forum: General Help
---

### Post by DarthScape on 2010-01-20
OK, so, Ubuntu just took a dump on me. Just sittin' there, watching a movie, and BAM: both my screens go completely black... So, no big deal, my screens come back, the movie is gone but firefox is still up. Alright so I just decide to start the movie back up, one problem, there is no sound. So I close out of the movie, and firefox. Start the movie in vlc this time, alright, the sound is working and everything seems good. Then I relaunch firefox, and it gives me some error saying that some setting might be wrong and some features might not work. I close out of the error, and the browser seems fine. I continue along, but notice the the time on my computer has suddenly change to like 6:40 and its only 12:40... WTF?!?!?

And no, I haven't restarted my computer since, just putting that out there.

Any ideas what went wrong?:confused:

---

### Post by SchizmWolf on 2010-01-20
Noticed you're running Karmic. I don't know if that's a bug in the system or not, but I have a few suggestions:
1) RESTART THE COMPUTER!!!!! Sometimes my sound will just go kaput as well, and restarting has always fixed it.
2) Have you tried running apt-get -f install? If there's a broken package in java or adobe it might cause your sound to die.
3) Do you have any recorded code dump from before, during, and/or just after the crash? That information might be useful.
4)File a bug report, and maybe someone will be able to figure out what's happened.

I know they're all pretty basic, but those are two common fixes, and I can't be arsed to think hard right now x.x

---

### Post by DarthScape on 2010-01-20
soz, not lookin for solution, just wondering why all of that happened at once. i know i could just restart and everything would be all fine and dandy.

---

### Post by ImperialXT on 2010-01-20
sudo apt-get install libalsa 
sudo apt-get install alsa-oss

---

