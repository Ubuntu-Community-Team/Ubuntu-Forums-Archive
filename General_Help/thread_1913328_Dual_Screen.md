---
title: "Dual Screen"
date: 2012-01-22
forum: General Help
---

### Post by steven198807 on 2012-01-22
Hi trying to get Ubuntu to work so i can take advantage of a few programs that have 64 bit versions because my windows is 32 bit, i have used wubi to install and believe that its 64bit but not 100% sure.

When i first got it running the dual screens was working, i had to change the setting so it was not a clone of the first screen, so basic i could use the second screen as a place to dump other windows.
Now then i installed the additional driver for my gts450 and after restarting my second screen no longer works it just black, if i boot windows it works so its not broken.
The first screen is 1920*1080 while the other screen is 1024*768, also tried updating the system and still is black.
nvida app shows that it there is 2 screens with their names but I'm unsure how to enable it(when i try i get a messy screen ), also the display settings show only 1 screen with the the name as unknown.

please help,  i do not know how to use command line and would prefer not to use it at all, thank you ;)

---

### Post by kc1di on 2012-01-22
> **steven198807 said:**
> Hi trying to get Ubuntu to work so i can take advantage of a few programs that have 64 bit versions because my windows is 32 bit, i have used wubi to install and believe that its 64bit but not 100% sure.

When i first got it running the dual screens was working, i had to change the setting so it was not a clone of the first screen, so basic i could use the second screen as a place to dump other windows.
Now then i installed the additional driver for my gts450 and after restarting my second screen no longer works it just black, if i boot windows it works so its not broken.
The first screen is 1920*1080 while the other screen is 1024*768, also tried updating the system and still is black.
nvida app shows that it there is 2 screens with their names but I'm unsure how to enable it(when i try i get a messy screen ), also the display settings show only 1 screen with the the name as unknown.

please help,  i do not know how to use command line and would prefer not to use it at all, thank you ;)
What Driver did you install and what driver were you using before when it was working?
You may have to re-install the old driver.

---

### Post by steven198807 on 2012-01-22
> **kc1di said:**
> What Driver did you install and what driver were you using before when it was working?
You may have to re-install the old driver.

not sure it gave me 2 options and i chose the first one but after i switched to the second one, i found this image on the web to show yeah [http://i.stack.imgur.com/NhTLL.png](http://i.stack.imgur.com/NhTLL.png)

i just installed gnome 3 still can't get the second screen on ;(

---

### Post by steven198807 on 2012-01-22
OK i got it working now but not sure if it will stay when i restart later, had to play around in the settings in nvidia x server settings but its very buggy because i had to try the same thing about 4 times.
It is a bug i think because it reports both screens are screen number 0 instead of showing 0 and 1, maybe a developer needs to take a look as apparently I am not the only one it started in 10.04.

ill post back later today after i restart later, to busy at the moment.

---

### Post by steven198807 on 2012-01-22
Tried a restart, when i got to log on screen soon as i started to type my password the screen changed to a buggy noise look and then came back on again and the second screen started.
after that i put my password in again because it went back to blank and logged in to find a error message saying about resolution and it was trying 50hz or something when it should be 60hz on both but the error went of screen to fast. The screens are up and working but this maybe come a issue.

problems with Linux on day 1 , my friends said that would happen lol

---

### Post by steven198807 on 2012-01-22
The error when starting is the following

Could not apply the stored configuration for monitors
none of the selected modes were compatible with the possible modes:
Trying modes for CRTC 354
CRTC 354: trying mode 2944x1080@50Hz with output at 1920x1080@50Hz (pass 0)
CRTC 354: trying mode 2944x1080@50Hz with output at 1920x1080@50Hz (pass 1)


but this should not be happening as screen 2 does not support that resolution and its not set at that size ether

---

