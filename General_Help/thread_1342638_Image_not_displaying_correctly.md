---
title: "Image not displaying correctly"
date: 2009-12-01
forum: General Help
---

### Post by absentspace on 2009-12-01
Hi,
This is my first trip down Linux Rd, and I'm having a slightly rough time of it. 

Video Problem: The image on the monitor is shifted about an inch to the right, meaning there is about an inch of dead space on the left side, while about an inch of the desktop is off screen to the right.


Firefox Flash Plugin Problem: I can't get it. I tried loading up pandora and it keeps telling me that plugin is needed, then the package can't be found, then it is installed, but it never works.


Audio Problem: Is is possible to get 5.1 audio working with a Creative SB Audigy SE card? 
I have a modified driver package that I use for Windows Vista / 7 on the same computer.


Thanks for any suggestions.

Chris

---

### Post by fluffman86 on 2009-12-01
1.  Press the OSD button on your monitor to shift or stretch the picture where ever you want it.  Occam's Razor: the simplest solution is probably right.  :)  

2.  Close firefox, go to System > Administration > Software Sources, and check the top 4 boxes.  Close, and press "Reload."  Then go to applications > Ubuntu Software Center and search for Flash.  Download ubuntu-restricted-extras (at the top) to get Flash, MP3 Support, Java, Microsoft Fonts, etc.

3.  dunno, sorry. :P

edit: check this? [http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html](http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html)

---

### Post by Spectre5 on 2009-12-01
1.  What video drivers are you using?  Did you enable to nvidia restricted drivers (if your card is nvidia)?  Is your card ATI, nvidia, intel, or other?  Double check if your monitor has an "auto" button on it as well - mine was once off by about a half inch and pressing this button on the monitor fixed it.

2.  For flash, you'll need (some) flash player...perhaps the easiest is to use the command:
```
sudo aptitude install ubuntu-restricted-extras
```
If this doesn't work still, then search the forums for one of the other methods of installing flash...it is a common topic.

3.  You should be able to get 5.1 audio without much trouble.  Type in:
```
aplay -L
```
And you should see the support for 5.1 there.

Extra - For videos in general (such as playing encrypted DVD's), you'll want to use the medibuntu repos, see this link:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by akakingess on 2009-12-01
I believe you could just use the old```
sudo apt-get install flashplugin-nofree
```
and that should get flash installed for you...

---

### Post by absentspace on 2009-12-20
UPDATE: Problem is solved.

I had to shelve the project for a few weeks, as I just started a new job, All I had to do was install a bunch of updates and activate the Nvidia Proprietary Driver. I now have full resolution for the card and Firefox flash is installed properly. I am still not getting full functionality from a 5.1 SB Audigy SE card. I will be posting questions in another forum.

Thanks for the responses!

---

