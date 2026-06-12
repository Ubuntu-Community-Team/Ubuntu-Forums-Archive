---
title: "Sloooooooow 10.04"
date: 2010-06-14
forum: General Help
---

### Post by joecichocki on 2010-06-14
I have a Compaq Presario with a 1.6GHz processor and 2 gigs of memory. I was running Ubuntu 9.10 on it, and then when the latest, 10.04 came out, I upgraded. For me, it has been a downgrade. Opening JPEGs in the Gnome viewer takes an average of 10-15 seconds. Using the viewer to move from picture to picture is excruciating. In the older version of Ubuntu, it was basically instantaneous. My experience with GIMP has also slowed down. Opening any kind of tool also takes ten seconds or more. Saving anything is slow too. Slideshows, although set in preferences to a three second pause, take ten seconds or more from picture to picture.
 
Is there any adjustment I can make? In my appearances preferences, I am set to the most basic - and thus the fastest. Is there a fix for this slowness? Or would I be better off going back to 9.10???
 
Thank you for any help

---

### Post by oaxacamatt1 on 2010-06-14
Hey Joe,
I don't know exactly why you are getting such excruciating repsonse times for 10.04 but there are a few things you can try.

One of the first things I do after a clean install is load up a couple programs like 'BootUp-Manager' and 'HTOP' for starters. Both can be found in the 'Applications/Ubuntu Software Center'.  

BootUp-Manager allows you to turn off the different services that Ubuntu loads and starts by default. For example, I never use Bluetooth so I turn it off.  There are lists of services that are ***OK*** to turn off all over the web, so read up first.  ***Note***: Turning off some can ruin your whole day or week. ;))  A similar tool to this prog is using the 'System/Preferences/Startup Applications' and unchecking services there.

HTOP is a prog that allows you to view all (or almost all depending on how you set it up) the processes that are running at that moment.  You can then 'kill' the PID by number.  ***ALSO*** note that you can turn off the wrong process and really screw up your day/week/computer if your not careful.

One more thing I might suggest is that you can always turn of the Compiz or 'fancy' visual effects by going to 'System/Preferences/Appearence' and then goto 'Visual Effects' tab and set to 'None'.

HTH,
Matt

---

### Post by NCLI on 2010-06-14
Do you have the proprietary drivers installed for your video card? If not, that could be the problem.

---

### Post by RJ12 on 2010-06-14
> **NCLI said:**
> Do you have the proprietary drivers installed for your video card? If not, that could be the problem.

Do you have any drivers at all?

---

### Post by cbrunhaver on 2010-06-14
open up a terminal and type this command and post the results.

lspci | grep VGA

---

### Post by Mr Cool Span on 2010-06-14
I don't thing it the video driver,
i have just finish a minimal install and install gnome core and it also slow at boot up, i get the pub-el screen and about 10 sec later i get the menu bares, i have the install the Ati fglrx drivers whit same sellout

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics

And before you clame that it is the Ati ther do this, i can telle you it do the same whit my nvidia card
But i don't have the answer.

---

