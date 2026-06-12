---
title: "About to do a reinstal because my Rhythmbox is broken"
date: 2011-02-07
forum: General Help
---

### Post by Mad dog on 2011-02-07
Please help me if you can. I wanted to rip songs from my CDs using Rhythmbox but I wanted to do it at a higher bitrate. I followed the directions from post #10 here: [http://ubuntuforums.org/showthread.php?t=1195545](http://ubuntuforums.org/showthread.php?t=1195545) This worked for a while, then I tried to change the 320 to a 256. This made my MP3 selection disappear. I remade a profile called MP3 but now it will not rip the whole track. It only rips a few seconds of each track.

I've tried completely removing and reinstalling Rhythmbox via Synaptic. It doesn't help. I can't get the defauly mp3 profile back under EDIT>PREFERENCES>MUSIC>PREFERRED FORMAT :confused:

I'm considering doing an entire OS reinstall just for this, tell me there's an easier way to fix it.

---

### Post by coffeecat on 2011-02-07
Doing a reinstall of an application doesn't remove your personal settings which are held in your home folder and it sounds as though there is a  problem in the personal settings. The following will set rhythmbox back to its defaults but you will lose your playlists.

Close rhythmbox and open your home folder. Now ctrl-H for hidden files. Open the .local folder, now the share folder. You can either delete the rhythmbox folder plus contents or rename it. Now open rhythmbox again and see if that helps.

---

### Post by Mad dog on 2011-02-07
Maybe there are some repositories or packages I need? I'm just confused because it was fine one second, then broken the next.

Gnome audio Profiles is what it is. How can I reset that?

---

### Post by Mad dog on 2011-02-07
I deleted that, and that resets my music list and deletes playlists, but it doesn't reset audio profiles listed under preferences>music.

---

