---
title: "Openarena 0.8.5 on Karmic 9.10 32bit"
date: 2010-05-20
forum: General Help
---

### Post by carn1x on 2010-05-20
Ok so everytime I exit OA, the game will hang as soon as I tell it to quit (includes typing quit in console)

I ran from terminal to see what the last entry was before killing the process and it's always: 

Closing SDL audio device...

I get this problem on Urban Terror most of the time, and I get it on Nexuiz rarely.

Also, sometimes when I boot the game up I get about 5-10 seconds of very poor quality audio and then the audio just cuts out. Can't see anything in the terminal however that looks like an error regarding this.

From googling I take it there are a number of other people who've hit this problem on Linux.

Thanks for any help :)

---

### Post by carn1x on 2010-05-20
Ok, solved via: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/224399](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/224399)

although for me the package was called libsdl1.2debian-pulseaudio

it seems to have solved both issues, although only the exit bug was 100% reproducable.

---

