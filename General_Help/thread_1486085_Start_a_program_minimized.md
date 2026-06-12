---
title: "Start a program minimized"
date: 2010-05-17
forum: General Help
---

### Post by DrKenobi on 2010-05-17
Hi! I know how to start a program automatically with 'Startup Applications', but how do I start it minimized? In particular, I would like to start Tomboy, but I want it to be minimized and only showing the icon on the system tray. Thank you!

---

### Post by SlidingHorn on 2010-05-17
As far as I'm aware, this is not possible.  Anyone here can feel free to prove me wrong though...

Reference: [probably an easy question, startup program minimized?]("http://ubuntuforums.org/showthread.php?t=70138")

---

### Post by DrKenobi on 2010-05-17
> **SlidingHorn said:**
> As far as I'm aware, this is not possible.  Anyone here can feel free to prove me wrong though...

Reference: [probably an easy question, startup program minimized?]("http://ubuntuforums.org/showthread.php?t=70138")

I also read that post, but it's from 2005/06. I think it should be possible five years later. If it's still not possible, I think I'll post it at Brainstorm.

---

### Post by DrKenobi on 2010-05-18
Yep, it's not possible. I found I bug in Launchpad and I'm following it. I can believe the guys from Tomboy haven't solve this issue yet.

---

### Post by Yarui on 2010-05-18
If there is nothing built into the program or operating system to do that, you could always try to figure out how to write a script that will do it for you and then have that script run at startup.  Something that just closes the window after it opens, maybe.  I have never tried to write something that would do anything like that, so I can't give any tips on how to do it.

---

### Post by nilsja on 2011-05-04
why is this topic marked as solved? is there a solution to start a program like tomboy minimized? the panel applet workarround is gone since ubuntu 11.04...

---

### Post by kenjiru on 2011-05-29
I'm using Ubuntu 11.04 and I have the same problem. Tomboy start by showing the search notes window, and the tomboy-applet is gone.

---

### Post by JoePublic9 on 2011-05-30
I am not sure if this is what you are looking for but I wanted tomboy to 
start in the background at boot so I did a search and found this solution.

 Make this script.

#!/bin/sh
/bin/sleep 5
/usr/bin/tomboy

add it to /usr/local/bin

Now when I boot or log in tomboy is running with icon on the top panel.
 Not my solution and I wish I could credit the person I got it from but it
was this forum.

If this wasn´t what you were looking for I am sorry to waste the time and space.

Good luck.
  Joe

---

### Post by Larkspur on 2011-05-30
In Startup Applications, do you have the command "tomboy --search" (Which I think is the default command)?  I've got 11.04, and running the command "tomboy" starts the panel indicator and no search box.

---

