---
title: "Screen issue after login, new to Ubuntu, but really excited..."
date: 2011-07-15
forum: General Help
---

### Post by ToddJ on 2011-07-15
Hey guys,
 
I've got an HP ThinClient that my computer dumped in the recycling pile. I swapped out the ATA 1-gig flash drive, and replaced it with a 60 gig ATA hard drive. I installed Ubuntu on it through a flash-drive, and everything comes up just fine. 
 
When I boot up the computer, I get the ubuntu screen, it comes to the login, I select my username and enter my password. I hear the little jingle music, and then the computers graphics get messed up. I still see the mouse, and it appears as though I'm opening windows, but they come up really as just screwed up boxes that are black or other colors and the graphics get all distorted. 
 
I just figured out how to get into the GRUB menu, and I was able to boot in reduced graphics mode. Everything seems to be in 16 colors, but I can actually log in now and see everything! (really cool). 
 
I'm guessing I have a problem with my graphics setting, what do you guys suggest I do?
 
Thanks!!!
 
Todd
 
 
 
EDIT: Just to give an update, I can log into the computer using rescue mode, and I can do everything on the computer that I want to in 16-color mode or whatever that mode is. As soon as I reboot in the normal mode, the graphics mess up as SOON as I log in.

---

### Post by ToddJ on 2011-07-16
I fixed it!!! Apparently, I just needed to change the setting to UBUNTU CLASSIC!!!
 
It works!! WOO HOO!!!

---

### Post by wildmanne39 on 2011-07-16
> **ToddJ said:**
> I fixed it!!! Apparently, I just needed to change the setting to UBUNTU CLASSIC!!!
 
It works!! WOO HOO!!!
Hi, thats good if you want to see if you can run unity you can run these commands in a terminal
```
sudo lshw
```
```
lspci | grep VGA
```
```
/usr/lib/nux/unity_support_test -p
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

