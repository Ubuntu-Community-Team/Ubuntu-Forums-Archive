---
title: "cannot load 10.04"
date: 2010-10-06
forum: General Help
---

### Post by workshop1702 on 2010-10-06
i cannot get ubuntu 10.04 to load on my pc , version 9.04 works fine appart from it cocks up the screen resolution. ubuntu 10.04 just wont load i put the cd in the cd rom and restart it tries to load you get ubuntu purple screen with ubuntu writen in the middle several red dots underneath which it scans back and forth untill the end of time itself. no lights flashing on the cd rom or the pc , it totally refuses to load . i have tried a downloaded disc and a genuine one through the post exactly the sam problem .
on my other pc it cannot even detect the cd rom , it does however work on my computer tablet .
Anyone any ideas as to what the problem is please.

---

### Post by Quackers on 2010-10-06
Did you check the MD5 checksum of the downloaded .iso file? Is it possible that it is a bad burn? What have you checked, if anything?

---

### Post by workshop1702 on 2010-10-06
this would be unlightly to be the problem as the discs work on my tablet pc also one is fron conical through the post so not a bad burn . as to what have i checked . i am at a total loss as how or what to do to check anything or what to check as i have no idea at all as to what the problem is . i need help please as this is my main pc and its down i ned it working again asap :confused:

---

### Post by Favux on 2010-10-07
Hi workshop1702,

Quackers is not describing a general check:
> as to what have i checked . i am at a total loss as how or what to do to check anything or what to check as i have no idea at all as to what the problem is 
but a specific procedure to validate you have burned a good disk.  This is called a "MD5 checksum" of the downloaded .iso file and is described on the download page and there are links to more details.  Or you could google it.

Many things could cause Ubuntu not to load.  Often it can be the video chipset/video driver.  The fact that you have video trouble with 9.04 may be a clue.  What video card/chipset do you have?  Enter in a terminal:
```
lspci | grep VGA
```

Frankly I expect no response to my request for further information.  That's been my experience with you.  I've noticed your recent complaints.  Unfortunately those threads were shutdown so I couldn't respond.

I tried to help you with your tablet in 3/09 and you stopped responding as soon as I asked for information:  [http://ubuntuforums.org/showthread.php?t=1084121](http://ubuntuforums.org/showthread.php?t=1084121)  Tatung is not a brand I'm familiar with, and I know a little bit about tablets in linux.  It may be that it is a relatively uncommon tablet with little likelihood of support, but we never explored that.  However there are plenty of tablets that are supported by linux.

A sort of similar pattern with your second mouse request:  [http://ubuntuforums.org/showthread.php?t=1223845](http://ubuntuforums.org/showthread.php?t=1223845)  It's not clear you ever looked at the links or read anything.  And you responded at 3 week or 9 month intervals??  How exactly am I suppose to respond/deal with that?

Frankly I decided you were some kind of Troll and started to ignore you.  And with your latest posts I still think you are.  I'm not buying a flat learning curve for 18 months.

---

