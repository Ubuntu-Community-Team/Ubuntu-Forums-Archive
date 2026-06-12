---
title: "Youtube videos will no longer play after system update"
date: 2012-01-09
forum: General Help
---

### Post by koolkatkiwi on 2012-01-09
Yesterday there was a system update, which I just accepted as I always do. After that, no video will play on any of the video sites. I restarted the computer several times, which didn't fix anything.

Sometimes there is a big red circle with a line across it, and sometimes it is a striped "clapperboard" such as is used in movies - "lights, camera, action". When you click on the "play" button, either nothing happens (the clapperboard) or the screen just turns white (the red circle).

I'm using the Chromium browser, but I tried on Firefox, and the same thing happens. The reason I'm using Chromium now is that after I upgraded to Ubuntu 11.10 a couple of months ago, Firefox will no longer work. The right click button does nothing anymore in Firefox, and as you can imagine, this makes the browser useless. So, I went to Chromium.

I had to install codecs, etc. when I did the upgrade, and have been viewing videos fine up until yesterday. If I download the videos, they will then play perfectly in any of my video players, so it is something to do with the streaming, I would guess.

I have already removed and re-installed the Adobe Flash Plugin, with no joy.

Dual core Pentium D processors (3.00 GHz each), 3.4 GiB memory (I think DDR2), 250 GB hard drive. 

Can anyone help me?

---

### Post by imachavel on 2012-01-09
reinstalled the flash plug in? wow it is a streaming problem. 

sudo apt-get install flashplugin-installer
[http://www.linuxquestions.org/questions/linux-software-2/which-version-of-adobe-flash-player-do-i-install-for-ubuntu-10-10-a-864157/](http://www.linuxquestions.org/questions/linux-software-2/which-version-of-adobe-flash-player-do-i-install-for-ubuntu-10-10-a-864157/)

dude I'm at a loss myself. I haven't used youtube in a bit though. I'm guessing you will need some type of codec/driver/plug in/java diagnostic read out from your terminal to fix this problem. What a bummer

---

### Post by koolkatkiwi on 2012-01-09
Mate, you are tops! This fixed the problem instantly. THANK YOU!!! Sorry I can't give you any kudos on here, as there doesn't seem to be any provision for that. Maybe I shouldn't blindly accept updates in the future. :/

Cheers, Kath:KS

:popcorn:

---

