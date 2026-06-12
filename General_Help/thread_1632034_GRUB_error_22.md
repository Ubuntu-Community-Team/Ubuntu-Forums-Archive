---
title: "GRUB error 22"
date: 2010-11-27
forum: General Help
---

### Post by Patrunjel007 on 2010-11-27
Hi...I wanted to install ubuntu via wubi, but i had to format my partitions (can't do it on wubi :) ) so i used a crappy program(i don't remember the name) to get rid of Backtrack4 , because i wanted windows kept for my mom.So, that was the sorry, i've ended up with a GRUB error 22, and a Backtrack4 CD stuck in my DVD-rom.
So my question is: Can somewone tell me how to fix error 22? (i've seen some methods online, but i obviously can't put a Windows CD in my DVD rom because the Backtrack4 DVD is stuck in there...)Can somewone please help me? :)

PS: I can use the Bakctrack4 live CD to acces the console and stuff

---

### Post by dino99 on 2010-11-27
for serious installation:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by Patrunjel007 on 2010-11-27
Ok, but i can't get the Backtrack4 DVD from the DVDrom.I press the button, it does not respond.I have tried to press it while BIOS was loading, same thing...it doesn't want to get out...

PS: I've tried sticking a needle in that little hole of the DVD-rom, but i didn't solve anything...being noob sucks...

---

### Post by Patrunjel007 on 2010-11-28
Can anywone help me? 
At least tell me how to get that DVD out...please...

---

### Post by bcbc on 2010-11-28
I use a paperclip, unwind it and jam it in the hole. Had to do that a bunch of times. That drive no longer works now :)

You can install wubi by putting the downloaded .iso in the same folder as wubi.exe and running it from there. Just make sure the wubi version matches the .iso (when you run wubi it tells you the version right on the top)

Once you get it running, don't update packages grub-pc and grub-common, especially if you install 10.04.1 (grub is breaking wubi installs at the moment).

---

