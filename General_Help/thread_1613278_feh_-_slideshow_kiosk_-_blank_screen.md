---
title: "feh - slideshow kiosk - blank screen"
date: 2010-11-04
forum: General Help
---

### Post by AiBo on 2010-11-04
I have pieced together a number of old components we had sitting around to construct a promotion kiosk in the lobby of our facilities. Built into a kiosk we installed an old monitor, mounted in the top of the kiosk is an old dell desktop. The goal is simple. Have a slideshow of upcoming events cycle through on the screen. Yes, I know using GUI desktop is a bit of overkill for our needs, but I am most familiar with with it as it is my day-to-day OS.

Everything works fine except two annoying issues. I would love some help getting them worked out!

I am using feh to call the photos on start-up via adding a command via ->Preferences->Start-up Applications

Code: Select all
    feh -FZ -D8 /home/aibo/Pictures 



First issue here (the minor issue): The system boots from power off right into the slideshow, but the taskbar at the bottom remains visible. How to get the taskbar not to show?

Second issue (the major issue): After a few minutes the screen goes blank! Move the mouse and feh is still running, but after a few more minutes same thing. Of course the idea is to have the kiosk completely hands off.

What I have tried:

1. Setting the Screensaver to 2 hours -> no effect, after a few minutes screen blanks
2. Checked the Power Management, setting everything to NEVER, still after a few minutes screen blanks
3. Checked the BIOS, not setting for blank screen or power save
4. Tried removing Power Management from the ->Preferences->Start-up Applications, after a few minutes screen blanks!!

I am not sure what else to try!! Any ideas out there?

Thanks in advance!

---

### Post by P4man on 2010-11-04
Im gonna try with the first one, that seems easy. Just add a delay

'sleep 5 && feh .....' 

Problem is that some gnome panel items load after feh and will cause it to come to the front. Alternatively, delete the panels :)

As for the second issue.. no idea that you havent tried already. If you keep using the machine, does the screen remain visible? Is the monitor going in to standby mode or does it stay on displaying black ?

---

### Post by AiBo on 2010-11-04
Yes, if I simply move the mouse (or any other interaction with the computer) it comes out of blank screen/standby.  Feh is still rolling the slideshow.  It seems just the screen goes blank.

Is this at the kernal level?  Something X is doing?

Thanks for the sleep suggestion for feh!

---

### Post by AiBo on 2010-11-05
Ok found some hope here ...

[http://ubuntuforums.org/showthread.php?t=1283057](http://ubuntuforums.org/showthread.php?t=1283057)

trying it now:

Re: Disable Blank Screen on Idle
Ok. So I've found a solution. First, you can find some background information here. Apparently, this screen blanking behavior is built into Xorg.

I've figured out how to turn it off using these commands:

Code:

xset s off
xset -dpms
xset s noblank

---

### Post by bdaman80 on 2011-01-01
Do you think the xset needs to be set everytime the computer starts? Or one time good forever.

---

### Post by AiBo on 2011-01-02
Sorry, I am not sure.  However, I will say that this code has solved our needs!

---

### Post by bdaman80 on 2011-01-02
I believe I have made a couple of scripts that will work fine for my needs.  

I have a cli ubuntu 10.04 install that has Xorg, feh, unison, OpenSSH server, and is setup to auto login and start xserver. One script syncs pic folder with server on startup via unison, then kicks on feh. The other is ran every hour via cron. It syncs pic folder with unison, then kills current feh and restarts feh. I am sure that it can be done better, but I figure hourly update is good enough for my needs. 

Thanks for the reply

---

