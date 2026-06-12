---
title: "Inactive display goes to sleep too soon"
date: 2010-10-04
forum: General Help
---

### Post by rbaleksandar on 2010-10-04
Hi, guys.

  Ever since I installed 10.4 my display turns off (goes to sleep) after a couple of minutes. At first this didn't bother me for I was always doing something with either the mouse or the keyboard, or both, so my display didn't stay inactive for more than a few minutes. But now that I use it for reading from time to time, this drives me crazy so I finally made up my mind to solve this (or someone else to solve it for me :D). Here's the problem in detail:

The power manager is configured as follows:
**AC Power:**
_ACTIONS:_
1)Put computer to sleep when inactive for *1 hour*.
2)When laptop lid is closed *hibernate*.
3)Spin down hard disks when possible
=======================================================
_DISPLAY:_
1)Put display to sleep when inactive for *30 minute*.
2)Set display brightness to *60%*.
3)Dim display when inactive is *deactivated*.


The display in battery mode goes to sleep when inactive for *10 minutes*. Display dimming is *activated*.


I leave my laptop unattended that is - I don't touch neither keyboard nor mouse. After about 5-6 minutes the display goes to sleep. As you can see from the configuration above, even in battery mode it supposed to do so after 10 minutes.

Additional info:
# Nvidia GF 7300 Go with the latest drivers for this card
# No overheating or display problems (hardware problems I mean) encountered.


Any ideas what's the source of all evil in this case and perhaps some suggestion(s) how to fix it?


Thanks in advance!
rba




EDIT: Problem solved.
[http://ubuntuforums.org/showthread.php?t=1483345](http://ubuntuforums.org/showthread.php?t=1483345)
I checked it and indeed the screensaver "Black screen" is being activated after 5 minutes. :D

---

