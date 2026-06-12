---
title: "my external hard drive is read as a picture cd?"
date: 2009-07-09
forum: General Help
---

### Post by Dawei87 on 2009-07-09
not a huge problem, but whenever i connect one of my external hard drives and sometimes my flash drive, a box appears in nautilus that says "These files are on a picture cd" and there is a button to launch f-spot. i will attach a screenshot because i am bad at explaining this, but my question is, is there a way to A) tell my computer that my hard drive is not a picture cd? and/or B) is there a way to disable that box and button all together? if anyone knows please clue me in!

---

### Post by coffeecat on 2009-07-09
I can understand if Nautilus offers to open F-Spot if it detects jpegs in your external drive (I see you've got a 'Pictures' folder there) but it's odd that it thinks that the HD is a Picture CD. So what I'm about to suggest may or may not help.

Open a Nautilus windows and go to Edit > Preferences > Media Tab and see what is showing under 'Photos'. Change that to 'Open Folder' or whatever you want. If that doesn't help have a look under 'Other Media'. If you drop down the 'Type' box, you'll see that 'Picture CD' is one of the choices. You could try changing that to whatever helps (if anything).

By the way, that is what I see in Jaunty. I see you're using Intrepid. I seem to remember the File Management Preferences window was a little different with that version of Gnome.

---

### Post by Dawei87 on 2009-07-09
yea, i have those options, but i actually set it to never prompt or open programs on any media insertion. i guess it isnt actually doing that, but it would be nice to fix this behavior. let me know if you have any other ideas!

---

### Post by Dawei87 on 2009-07-10
bump

---

### Post by coffeecat on 2009-07-11
A google search shows that this is a bug in the version of gnome that comes with Intrepid.

[http://ubuntuforums.org/showthread.php?t=969897](http://ubuntuforums.org/showthread.php?t=969897)

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/258936](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/258936)

The launchpad thread starts off with this issue occurring in a cifs share but others report they get it with an ordinary external drive. It would appear that the problem is triggered by the system seeing your 'Pictures' folder, so you could try renaming the folder. Alternatively, how about running Jaunty? I've just tried an experiment in Jaunty and I can't reproduce this behaviour, so it seems that the problem is fixed in the 2.26 version of gnome.

---

### Post by Dawei87 on 2009-07-11
oh wow, thanks for the info. its funny you should mention jaunty, i just installed and am testing now. im still trying to find a fix for the low low volume though. if i cant fix that im gonna go back to intrepid.

---

