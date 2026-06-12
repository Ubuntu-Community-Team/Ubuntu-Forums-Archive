---
title: "XP-Ubuntu dual boot questions"
date: 2009-10-24
forum: General Help
---

### Post by lordshika on 2009-10-24
Alright, there was some super virus goin' 'round my school and, like an idiot, I caught it and it wouldn't come off, manually or through a virus scanner. So I decided now would be the best time to switch to ubuntu and reinstall windows. I did just that. I kept XP for games, so this is where the question comes in: 
1. Say someone gives me a game, and I wanna scan it for viruses on ubuntu before saving it on windows, how do I do that? 
2. Also, say I download something for windows and scanned it (if possible) with the answer given to question 1 (above), is there some way for me to transfer it to the windows partition?

I've looked around and found no answer to this, so forgive me if it's a stupid question. I know a lot about PCs... just not linux or dual-boots XD

---

### Post by phillw on 2009-10-24
> **lordshika said:**
> Alright, there was some super virus goin' 'round my school and, like an idiot, I caught it and it wouldn't come off, manually or through a virus scanner. So I decided now would be the best time to switch to ubuntu and reinstall windows. I did just that. I kept XP for games, so this is where the question comes in: 
1. Say someone gives me a game, and I wanna scan it for viruses on ubuntu before saving it on windows, how do I do that? 
2. Also, say I download something for windows and scanned it (if possible) with the answer given to question 1 (above), is there some way for me to transfer it to the windows partition?

I've looked around and found no answer to this, so forgive me if it's a stupid question. I know a lot about PCs... just not linux or dual-boots XD


Hi, 
welcome to the forum

Yes, you can scan for viruses via ubuntu before you let a file near your windows area.

It's only when you are dual booting / running wine that u need an anti virus for linux.

A quick How to can be found here..

[http://www.vpolink.com/showthread.php?t=198](http://www.vpolink.com/showthread.php?t=198)

There are other anti-virus systems - BitDefender just happens to be the one I use.

Hope that helps clarify things.

Phill.

---

### Post by MelDJ on 2009-10-24
for 1:
 [https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

for 2:
depends how you install ubuntu. if through wubi, windows will be in filesystem-host. just put the files there and you can access it next time you boot windows. if you installed it on another partition, the windows partition can be mounted in ubuntu

---

### Post by howefield on 2009-10-24
Wouldn't it be better installing anti virus to the windows installation and have the resident scanner do it's work.

If you want anti virus in Ubuntu clamav can be installed with Synaptic Package Manager.

---

### Post by lordshika on 2009-10-24
oh to clarify, it was through wubi, but if I want to send files from ubuntu to windows, what then?

---

### Post by MelDJ on 2009-10-24
> **lordshika said:**
> oh to clarify, it was through wubi, but if I want to send files from ubuntu to windows, what then?
[I]
if through wubi, windows will be in filesystem-host folder. just put the files there and you can access it next time you boot windows.[/I]

---

### Post by phillw on 2009-10-24
If you'd prefer to keep your windows and ubuntu areas seperate from eachother, I'd suggest going for a seperate install of ubuntu - what it known as "dual-booting".


Info on this can be found here ....

[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

Regards,

Phill.

---

### Post by lordshika on 2009-10-24
alrighty then. thanks for the help mates :3 much appreciated :D

---

