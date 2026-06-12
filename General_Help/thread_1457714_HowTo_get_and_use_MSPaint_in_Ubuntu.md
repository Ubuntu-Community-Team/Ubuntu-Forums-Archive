---
title: "HowTo get and use MSPaint in Ubuntu"
date: 2010-04-19
forum: General Help
---

### Post by robot_chicken_parm on 2010-04-19
This is my first thread ever in Ubuntu Forums.  I am a newb myself so if i am doing anything worng or anything please dont hesitate to let me know.  I have been using linux for a few months now and i LOVE Ubuntu 9.10 and i love this forum, in which i have found countless solutions to issues i have faced in my transition and use of Karmic.  So here goes...

So I am halfway there with this problem:

I found a link to mspaint.exe and it works fine in wine.  It can be found here:
 ["_http://download.microsoft.com/download/winntwks40/paint/1/nt4/en-us/paintnt.exe_]("http://download.microsoft.com/download/winntwks40/paint/1/nt4/en-us/paintnt.exe")" 

I downloaded it, and then extracted the file to "/home/christopher/.wine/drive_c/Program Files/Paint/".

Then in that folder, i right click the file "MSPAINT.exe" and selected "Open with Wine Windows Program Loader" and it opens just fine and works perfectly.

Now comes the part where i am confused.  I want to put it in the menu panel under "Applications-Wine-Programs-Accessories".....   Can someone please help me out with this?

Like i said, i'm a newb and i tried doing it by right clicking the menu panel and editing menus, but i dont know how to make the file "MSPAINT.exe" automatically open with Wine.  For some reason, when i got Project64 and a few other apps i didnt run into this problem because they were automatically put into the menu and openned with Wine by default.  please help.   thanks.

---

### Post by asmoore82 on 2010-04-19
Have you tried out GNU Paint?
It's in the repos.

To get mspaint in the menu, though, you could just right click and "Edit Menus"
But an easier slightly more advanced way would be to go to the hidden folder
".local/share/applications" under your HOME folder
and make a copy of an existing wine shortcut and edit it to your needs.

---

### Post by elliotn on 2010-04-19
and i think gimp is the best

---

### Post by dineshs on 2010-04-19
Follow this link to add an item to menu
[http://ubuntuforums.org/showpost.php?p=8986279&postcount=9](http://ubuntuforums.org/showpost.php?p=8986279&postcount=9)
I suggest you to try Kolourpaint first
[http://www.tips5.com/kolourpainta-simple-paint-tool-in-ubuntu](http://www.tips5.com/kolourpainta-simple-paint-tool-in-ubuntu)

---

### Post by Dell Inspiron 1501 on 2010-04-19
Though it looks a tad dated, I've used Xpaint as a suitable replacement for MSPaint.  You can easily find it in the repos.

---

### Post by robot_chicken_parm on 2010-04-20
i tried gimp, mtpaint, gnu paint, and xpaint but they just werent the same, i was raised on mspaint lol :(  ...but i just now got kolourpaint and its just what i was looking for.. @asmoore82:  thank you i made a copy of an existing wine shortcut and changed it to open paint and its workin great right from the menu. so thanks to all you guys i really appreciate all the help.

---

### Post by robot_chicken_parm on 2010-05-07
KOLOURpaint is 100,000,000,000,000,000X better than MSPaint!!!   Thank you so much!!

---

