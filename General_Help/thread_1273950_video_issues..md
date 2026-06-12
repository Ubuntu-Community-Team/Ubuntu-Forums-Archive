---
title: "video issues."
date: 2009-09-24
forum: General Help
---

### Post by rodh on 2009-09-24
I have been waiting for an answer in Multimidea/Video for a couple days.  I have a DIY Desktop,  Asus K8S-MX motherboard, with onboard SIS Video chip set.  Have 2 gigs memory with 512 shared for video (i think).  Ubuntu 9.04 on sda1, home on sdb1.  I have 398 gig free space.  And a HP w2007 widescreen monitor recommended resolution is 1680-1050 60 HZ.  That is also the Max resolution. HorzSync range is 24-82KHz, VertRefresh range is 50-76Hz,  Signal input is VGA,  Dot Pitch is 0.282mm. [COLOR=Red]The problem:[COLOR=Blue]I can only get 800x600 and still see most of the page without scrolling.  I have tried to set up things in xorg.conf but they did not work.  I have been searching for an answer for about 4 days now and have posts with no answers.   I can paste my Xorg.O.log if someone thinks they can help figure where things are going wrong.[/COLOR][/COLOR]  **[COLOR=Black]Thanks in Advance![/COLOR]**

---

### Post by rodh on 2009-09-28
BUMP!  No responses?  Any help would be appreciated a pointer something.  I would like to get the Monitor back out of safe mode.  I know it will work it did before 9.04 but nothing seems to work. I have searched Ubuntu, and Kubuntu forums and I have searched google.  I don't know how else to search for Xorg.config ,  I look in Xorg.0.log file and it looks like all the Sis drivers are loading properly.  Then it drops back to vesa and safe mode.  My monitor is more than capable,  I have tried with DDC/CI Support ON and Off.

---

### Post by no2498 on 2009-09-29
go to 
system 
preferences
look for the 
main menu
set it to load up all you like 
screen resolution
now go to
applications other
monitor and display
you will need to play with things if you know the monitor name  look for it

---

### Post by rodh on 2009-10-03
Well here is what I did to get my monitor up to capacity.  After searching and posting and waiting. I decided to re-install.  I did this 4 times, and then I decided to re-install 7.10 which was the only version that I did not have Video issues with.  I then copied and saved the Xorg,config file to the desktop and the re-installed 9.04 as a clean install.  I am not sure how this worked but my video is now working.  The xorg,config file that is in the new install of 9.04 matches the one I saved from 7.10.  I did not have to copy it over to the new 9.04 install though.

---

