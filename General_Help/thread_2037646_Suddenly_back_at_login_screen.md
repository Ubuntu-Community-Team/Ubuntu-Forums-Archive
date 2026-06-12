---
title: "Suddenly back at login screen"
date: 2012-08-05
forum: General Help
---

### Post by jmore9 on 2012-08-05
I was watching a youtubr vid and suddenly the screen went blank and i was at the login in prompt.  I did a hard reboot right then and logged on normally.  First time this has ever happened with ubuntu.

Anyone know where to look for what happened ?  Check the sysop log  but only saw a bunch of eth(0) stuff and wimax trying to start then failing , then the wired starts.

---

### Post by mahachi911 on 2012-08-11
I have the same problem.  I was not able to login and restart my computer

---

### Post by raja.genupula on 2012-08-11
I think this issue have some relation with Video Drivers . what kind of video drivers you have with you  ?

---

### Post by Supaikoo on 2012-08-11
We need you to validate with us whether or not you can or cannot log in. If you type your password in, does it take you right back to the login screen? Or does it load X successfully?

---

### Post by Bill Roberts on 2012-08-11
This has happened to me on numerous occasions since I upgraded to 12.04.  It's always when I'm in Firefox but not necessarily watching a video.  It returns to the normal login screen.  I have always been able to login after it happens.

---

### Post by gifford on 2012-08-11
For me the problem was with a Nvidia card and drivers. I tried to find an adequate solution, spent much time and effort but nothing seemed to provide a permanent fix.

I ended up replacing the Nvidia card with an ATI/AMD card and have not had any trouble since. I do understand the frustration that Linus Torvalds expressed about Nvidia and my solution is not to purchase products that have poor to little support for Linux.

---

### Post by The_Autonomist on 2012-08-12
> **Bill Roberts said:**
> This has happened to me on numerous occasions since I upgraded to 12.04.  It's always when I'm in Firefox but not necessarily watching a video.  It returns to the normal login screen.  I have always been able to login after it happens.

Chrome user here, and it just randomly started happening a few weeks ago. My screen will all of a sudden go black, then it takes me to my log in screen. 

I log in, get a box that pops up saying an error has occurred (something about xforg) and then i just resume my normal activities. 

It's really annoying though, and could be potentially problematic once school starts again. Ie, being in the middle of hw or writing a paper and then BAM! it logs you out at random. 

anyone has any idea what causes this>

---

### Post by The_Autonomist on 2012-08-20
any ideas???

---

### Post by Bill Roberts on 2012-08-21
See this post: [http://ubuntuforums.org/showpost.php?p=10775851&postcount=16]("http://ubuntuforums.org/showpost.php?p=10775851&postcount=16")
Finding the Multimedia Systems Selector was a real struggle (and I still don't know how I did it) but applying the value X Window System (No Xv) to the Video Default Output Pluin seems to have done the trick.

---

