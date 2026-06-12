---
title: "Small internet bothers since 10.04 update"
date: 2010-05-11
forum: General Help
---

### Post by nintendude7cubed on 2010-05-11
I've been using ubuntu along side my windows xp installation for the past few weeks.. Frankly I barely need xp anymore because i was overjoyed to find out that ubuntu 9.10 worked with my evil ralink 2600 chipset on my wireless pci card. I used 9.10 faithfully i really haven't used xp here at home in a couple weeks. So i finally decided to go through the trouble of upgrading to lucid. Since its an LTS i thought I may as well do it so i can guarantee myself 3 years without requiring myself to update for support versus the 18 months for non LTSs. I didn't need a disk or anything it was quite a nice install when you have xp. It makes me wonder why microsoft can't be this nice to ubuntu when installing the two OSs in reverse order. 

Anyway I got finished updating and i have just a couple of things on my mind. 

The latest version of firefox is included which was a big convenience, however, I'll click on it and firefox will faithfully pop up, but it will take around 20 seconds just to load the start page. On a broadband connection thats unacceptable. The interesting thing is if i go to youtube or something, It'll take about as long as the startup page did to load, but then it'll load my video pretty much faster than the loaded page does in windows. This never happened on Karmic. I'm wondering what i could do in order to fix this. 

Trying to fix this brings me to question 2.. how do you get the network manager to display its signal again in the upper right hand corner by the volume button. For some odd reason my wireless signal disappeared from my indicator applet and is nowhere to be found. Its probably really simple but I really have only scratched the surface of the totally different interface ubuntu has to offer in the past couple weeks.

If you were patient enough to read up to this point, thanks and i leave you with one last question not as much as a help question as a, "does this happen to you" question. I noticed now since youtube is the biggest pain and decided to fix what was never broken, they decided to change what the video player looks like. However, there are certain videos (even brand new ones) that for what ever reason play in the old player. This wouldn't be a problem to me, unless you were actually able to control the player. I'm wondering if this type of thing is happening to anyone else in ubuntu or in other operating systems for that matter.

---

### Post by lovinglinux on 2010-05-11
> **nintendude7cubed said:**
> The latest version of firefox is included which was a big convenience, however, I'll click on it and firefox will faithfully pop up, but it will take around 20 seconds just to load the start page. On a broadband connection thats unacceptable.

Disable [ipv6](http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html) and [tweak your DNS cache settings](http://firefox-tutorials.blogspot.com/2010/05/preferences-tweaks.html).

> **nintendude7cubed said:**
> I noticed now since youtube is the biggest pain and decided to fix what was never broken, they decided to change what the video player looks like. However, there are certain videos (even brand new ones) that for what ever reason play in the old player. This wouldn't be a problem to me, unless you were actually able to control the player.

If you are on a 64bit system, then [install the 64bit flash version](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html).

---

### Post by GSF1200S on 2010-05-11
Ill chime in on question 2. Open a terminal and type:
```
nm-applet
```
Does your wireless icon come back? If it doesnt or the terminal says it isnt installed, try:
```
sudo apt-get install network-manager-gnome
```
and then again from a terminal try:
```
nm-applet
```
It should load fine, and it should load when you startup the desktop. If it doesnt, report back here and ill tell you how to make a simple script that will run when gnome runs (dirty hack, but I dont use network-manager-gnome and the applet showed up for me when I did). Hopefully someone else will have an idea of why it doesnt show up and can provide a more elegant solution.

Alternatively, you can use wicd instead of network manager:
```
sudo apt-get install wicd wicd-daemon wicd-gtk
```
You will have to remove network manager in order for wicd to work, since network manager prevents all other networking tools (even dhclient (!) and other cli tools) from working:
```
sudo apt-get remove network-manager network-manager-gnome
```
and reboot so wicd will work.

Wicd can be found in Applications>Network, but the applet should run in your system tray.

---

