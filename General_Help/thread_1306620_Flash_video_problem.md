---
title: "Flash video problem"
date: 2009-10-30
forum: General Help
---

### Post by akand074 on 2009-10-30
Hello, 
Ever since I installed Ubuntu Karmic I haven't been able to play videos online. Youtube works fine but when I try all other hosts like zshare and megavideo they won't play. I click play and nothing happens doesn't even start buffering or show any sign of response, kind of like clicking on a picture. I have installed some new add ons like "Ad block plus" that I have tried disabling first but that hasn't worked. I only did a few steps from the "**Firefox optimization and troubleshooting thread**" just before I updated to ubuntu Karmic, though I don't think anything I have done there could have caused the problem. I am running 64 bit btw, but I don't know how relevent that is because its worked fine before. Anyone have any idea what the problem could be?
Thank you very much.

---

### Post by Giblet5 on 2009-10-30
[Read this]("http://ubuntuforums.org/showpost.php?p=7904240&postcount=1") and you'll be happy. :)

Don't forget to mark this thread SOLVED with the "Thread Tools" drop down above...

---

### Post by akand074 on 2009-10-30
Hey, thanks for the reply!
I installed the 64 bit flash, and I managed to click 100 times and get it to start playing and buffering, but after that I couldn't click any of the buttons (play, pause, maximize, full screen, etc) and when I reloaded it went back to doing the same thing where it wouldn't even start playing. Very odd. Also I'm using firefox x86_64, is there a full 64 bit version or is what I'm using correct? Thanks again

Also, I just realized that with the youtube videos, its the same, it plays but I can't use any functions of the player like play or pause or move the time, this is a bit frustrating, there must be some explanation.

FIXED IT! Removing "flashplugin-installer" did the trick, it looks like that was causing firefox to use an alternate flash plugin rather than the one from Adobe. Thanks again for the help, hopefully anyone having similar problems can fix it the same way.

---

