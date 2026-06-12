---
title: "Total Beginner, problem with microphone!"
date: 2010-01-29
forum: General Help
---

### Post by abarnett on 2010-01-29
I recently installed ubuntu and have really been loving it. I tried calling my bf on skype the other day though and while I could hear him just fine, he could not hear me at all. I tired making a recording and my mic didn't pick that up either. I have tried all the obvious solutions and explored every option under sound preferences. I am really frustrated because everytime I want to talk to someone on skype, I have to switch back to windows. Someone please tell me you know how to fix this, and PLEASE PLEASE remember I am an absolute beginner, no high tech talk here please :-) Thanks in advance!

---

### Post by gradinaruvasile on 2010-01-29
Well then low tech... :)

Skype-specific stuff:

open the options, and make sure, "allow skype to adjust my mic levels" IS OFF. This sometimes mutes the mic.

The generic stuff (applies to Ubuntu 9.10):

Right-click on the volume icon in the tray, select sound preferences. Go to the input tab and check the volume, make sure the mic is not muted. Then see if you have more than one mic device (connector section). Try switching if you have more than 1 mics, tap the mic to see if thete is any input.

If that didnt change, open a terminal (applications -> accessories -> terminal) and type in:

alsamixer

press enter. Then press tab to get to the capture view. Here is a bit complicated because each card has specific input/output options. 

Basically you should have a capture device selected and have high volume set (the capturable devices are those that have dotted lines - ) - navigation is with left/right, toggle capture is space, up/down sets volume.

Best is to take a screenshot of this (alt+printscreen) and post it here.
Make sure you are in the capture view (tab cycles the views).

---

### Post by abarnett on 2010-01-29
Ok, I have already tried all the skype and sound preference stuff and none of that worked. Here is a screen shot that you suggested. I tried fooling around with some of that stuff but nothing worked :-( Hopefully this will help someone to help me :-)

/home/ashley/Desktop/Screen Shot.png

---

### Post by gradinaruvasile on 2010-01-29
You have to attach the screenshot to a forum message. That link is on your computer.Here is how to do it:

Click the go advanced button (if not already in advanced message mode) and click on the attachments button, select your file then click upload.


Edit:

Also it may help if you specify what computer model are you using.

---

