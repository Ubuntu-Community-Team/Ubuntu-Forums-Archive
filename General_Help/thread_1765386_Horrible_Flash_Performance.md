---
title: "Horrible Flash Performance"
date: 2011-05-23
forum: General Help
---

### Post by SonyFoLife on 2011-05-23
does anybody have horrible flash performance? like when flash actually works for me i have horrible, horrible, choppy framerates and random bits of black popping up at random . . .
Does anybody have any ideas/fixes for this?
I've just been making due . . . but i would really like to be able to watch youtube again . . .
OH! i use Ubuntu 11.04 Natty 64-Bit, Chromium (From The Repos) but i also have this problem on Google Chrome (actually flash doesnt work at ALL on chrome) and Firefox.
Please help . . . ?

---

### Post by linuxinstalledfromhdd on 2011-05-23
Open Firefox and install the Flash Aid plugin:

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

Once you have it installed, click execute.

---

### Post by SonyFoLife on 2011-05-23
Will this help in Chromium? (My perferred browser)

---

### Post by linuxinstalledfromhdd on 2011-05-23
Well try it in Firefox for a moment and see what the results are like. It should help.

---

### Post by SonyFoLife on 2011-05-23
it helped a bit . . . definently not perfect though . . . now i must trry and find something for chromium

---

### Post by linuxinstalledfromhdd on 2011-05-23
Well make sure you try all the different settings in Flash Aid first. 

If you used the default settings you now have the Beta version of Adobe Flash. You can also try the Stable version from the drop down menu in Flash Aid.  And there a ton of tweaks you can use in the program to make it run better.   

Once you get it the way you like it then copy the files over to the Chromium directory.

~/.mozilla/plugins/ 

/opt/google/chrome/libgcflashplayer.so

---

### Post by SonyFoLife on 2011-05-23
Oh, Okay :D thanks for the help . . . god i hope this works

---

### Post by SonyFoLife on 2011-05-23
okay, so, i'm in firefox . . . and i opened the flash-aid menu thing (god i sound like such a noob) and it says that to change anything . . . i have to change the script . . . and i have no idea where to start . . . i dont know what to change . . . or to what


please help a poor little noob that just want to watch things again?

---

### Post by linuxinstalledfromhdd on 2011-05-23
No problem.

I was just changing my firefox browser flash plugin while i was waiting for you.

Here is how you do it.

Click on Tools >> Add-ons >> Flash Aid Preferences >> Click the Expert Mode at the Bottom of the menu.

Then you need to click the Tab at the top that says Installation Options. 

Now click the drop down menu and select any of the different versions of flash to install. 

Then you go back to the previous screen and click execute. 

You can even install the Google Flash if you like their flash better.   Give them all a good try and see what works best. 

When you find the one that works the best you can simply copy that plugin to the google chrome flash plugin's directory and rename it to match the google flash plugin.  That's it.

---

### Post by SonyFoLife on 2011-05-23
uh . . . okay so i got it working right . . . now wwhere is Firefox installed by default? (i wouldn't have changed it,s o thats more than llikely where it is for me XD)

---

### Post by SonyFoLife on 2011-05-23
okay i think i found it but it doesnt have a plugins folder just a java script executable . . .

{EDIT] its not a mozzilla folder its named firefox

---

### Post by linuxinstalledfromhdd on 2011-05-23
Install Chromium and it will use your newly installed Flash Plugin you installed with Flash Aid.

Open and cut and paste this into your Terminal:

sudo add-apt-key ppa:chromium-daily/ppa
sudo apt-get update
sudo apt-get install chromium-browser

And this will install the PPA for the latest version of Chrome Browser, in Terminal cut and paste:

wget -q -O - [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) | sudo apt-key add -
sudo sh -c 'echo "deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main" >> /etc/apt/sources.list.d/google.list'
sudo apt-get update
sudo apt-get install google-chrome-stable

---

### Post by lovinglinux on 2011-05-23
Hi,

First of all, I recommend getting the new [Flash-Aid 2.1.1]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/versions/"), which has a nice Wizard and several improvements.

If you are using Chromium (not Chrome), then there is nothing you need to do, other than running Flash-Aid installation wizard. Chromium will detect the plugin as well.

If you are using Chrome 64bit, it will also detect the plugin without any additional steps.

If you are using Chrome 32bit, then you will have to turn off the plugin that is bundled with Chrome. You can do that by typing **about[noparse]:[/noparse]plugins** in the address bar.

If you experience any problems with Flash-Aid, click the "Help" menu, then Generate Report, then attach the generated *firefox-report.txt* file created in your Desktop, so I can take a look at your system info.

---

### Post by johanPO on 2011-05-24
I must say that I agree that Flash is one of the things that works better on WIndows. 
I have a Thinkpad Edge with an Intel HD graphics card. Under windows (it was installed on the machine when I bought it) watching a 1080p video from youtube works perfectly fine. Under Linux it is slightly choppy and the sound is out of sync..

---

### Post by linuxinstalledfromhdd on 2011-05-24
That's because adobe doesn't support linux as much.  Try the beta version of Flash.

---

### Post by johanPO on 2011-05-24
That is possibly true, but does not help much ;-). 

I am running 10,3,181,14 that is the latest that I found. Is that the one you mean?
The only other thing I can find is the Adobe Flash Player "Square", but that is from November and meant only for developers..

---

### Post by linuxinstalledfromhdd on 2011-05-24
Have you tried Flash Aid plugin for firefox yet?  By default it will install the Beta Flash for your system.  It worked great for me. No more flash issues.   It takes 1 minute to get that up and running, and you should be fine.  Make sure to use a nice guide when installing the PPAs and everything like this:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

I tried Natty, wasn't very happy with the performance. Switched back to 10.10 and it runs like a dream.  I can't complain. I'm not going back to windows now.  But it does take some time to get everything configured and installed on Ubuntu.  That's the way it is.

---

### Post by Vaphell on 2011-05-24
> But it does take some time to get everything configured and installed on Ubuntu.

much less time than on windows actually. Ok, first time can take a lot but only because you lack experience, each attempt is more breezy that the previous one. Not only many apps and drivers in ubuntu come out of the box, pretty much everything can be installed from single central repository - you just mark bunch of stuff, press [Apply changes], sip your tea for few minutes while package manager downloads and installs things, voila. On top of that you can automate the task, once you know what packages you need (handy in case of reinstall). In windows you need to meticuously scour dozen of sometimes shady websites and manually run 50 different setup.exes to have all the drivers and tools you need. Granted, most people get their windows in preinstalled state, fine-tuned to fit the hardware configuration but windows installation from scratch is something that can cause depression. Every time i had to reinstall XP and customize it, i had to spend 2 days to shape it to my liking. I dreaded at the thought of the process alone, while with ubuntu it's more like 'ok, it's 1hr tops, let's do this' :-)

---

### Post by johanPO on 2011-05-25
> **linuxinstalledfromhdd said:**
> Have you tried Flash Aid plugin for firefox yet?  By default it will install the Beta Flash for your system.  It worked great for me. No more flash issues.   It takes 1 minute to get that up and running, and you should be fine.  Make sure to use a nice guide when installing the PPAs and everything like this:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

I tried Natty, wasn't very happy with the performance. Switched back to 10.10 and it runs like a dream.  I can't complain. I'm not going back to windows now.  But it does take some time to get everything configured and installed on Ubuntu.  That's the way it is.

Yes I tried the flash aid, and it helped getting closer to a Windows performance. Don't get me wrong. I do NOT like Windows. I have it as it was on my PC and for certain things like Itunes, there are no Linux solution. I Boot into Windows on my personal PC maybe once a month...  Yesterday it was a sanity check to see if it was the PC or adobe. And it was adobe messing things up. 
Does anyone have any insights to if this is maybe also a graphics card issue, or is compiz messing things up? I have already disabled the sync to vblank.

Cheers

---

### Post by lovinglinux on 2011-05-25
> **johanPO said:**
> Yes I tried the flash aid, and it helped getting closer to a Windows performance. Don't get me wrong. I do NOT like Windows. I have it as it was on my PC and for certain things like Itunes, there are no Linux solution. I Boot into Windows on my personal PC maybe once a month...  Yesterday it was a sanity check to see if it was the PC or adobe. And it was adobe messing things up. 
Does anyone have any insights to if this is maybe also a graphics card issue, or is compiz messing things up? I have already disabled the sync to vblank.

Cheers

Flash GPU acceleration and Compiz doesn't work well together.

---

