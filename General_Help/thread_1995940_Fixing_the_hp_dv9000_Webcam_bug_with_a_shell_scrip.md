---
title: "Fixing the hp dv9000 Webcam bug with a shell script patch."
date: 2012-06-03
forum: General Help
---

### Post by ntzrmtthihu777 on 2012-06-03
Hello all,

Super-noob here again! I have an idea that will hopefully fix the problem posted here

[http://ubuntuforums.org/showthread.php?t=1253907](http://ubuntuforums.org/showthread.php?t=1253907)

The problem seems to be that guvcview (and presumably cheese and other webcam programs) renames /dev/video0 to /dev/video1 after being run a few times. A temporary work-around I found was to run

[FONT=Courier New][COLOR=Silver]gksudo nautilus[/COLOR][/FONT]

and rename video1 to video0. This fixes the problem until the rename happens again. 

My idea is to insert a couple lines of script into guvcview (or whatever you use) so that each time you run it it first checks for the existance of /dev/video0, and if it is not found to check for /dev/video1 and if found rename it to /dev/video0. This should fix the problem (assuming you don't actually have a video1 input, this probably would work best/only in laptops with built-in webcams) as it does what I do manually automatically.

However, being a total noob, I have little knowledge of shell scripting, mainly I just copy and paste stuff I find online and tweak little things. One day I hope to be knowledgeable enough to be the one giving help, but now I need the community's help.

Could someone with the knowledge please write a script that:

1. checks for video0
2. if video0 is not found checks for video1
3. if video1 is found rename it to video0
4. does these actions before guvcview (or whatever) actually runs

Also, what file to add it to is needed knowledge.
I know I'll appreciate it, and I know others with the same problem will too.

---

### Post by ntzrmtthihu777 on 2012-06-03
Anyone? I'm researching this right now, but help would be appreciated.

---

### Post by ntzrmtthihu777 on 2012-06-04
Hello?

---

