---
title: "Ubuntu 12.04 - Xscreensaver Not Starting"
date: 2012-04-28
forum: General Help
---

### Post by A4orce84 on 2012-04-28
Hello Everyone,

I currently purged gnome and installed xscreensaver to have some type of screensaver with Ubuntu 12.04.

I tried adding the xscreensaver to my startup applications, using the following guide:
[http://www.liberiangeek.net/2012/04/add-enable-screensavers-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/add-enable-screensavers-in-ubuntu-12-04-precise-pangolin/)

However, I do not believe it is starting when I turn on my computer.

If anyone could offer any additional time or assistance, it would be GREATLY appreciated! =)

Thanks,

--Asif

---

### Post by A4orce84 on 2012-04-28
Ttt

---

### Post by zombifier25 on 2012-04-29
Try starting xscreensaver-demo and see if it screams about xscreensaver not currently running.

---

### Post by A4orce84 on 2012-04-29
Here is the output when I ran the command:

[IMG]http://img.photobucket.com/albums/v405/A4orce84/Selection_001-1.png[/IMG]

So it doesn't appear it was running when I started my computer. =(

---

### Post by Amndeep7 on 2012-04-29
Well there is one thing that you can do to help, just a minor thing - if I'm not mistaken, the argument that you used with the command that you used to auto-start the XScreensaver should be ```
-no-splash
``` and not ```
-nosplash
```.  Then try logging out and logging back in again.

---

### Post by A4orce84 on 2012-04-29
Nope, still not working unfortunately after logging in and back-out after making the "-no-splash" change.

---

### Post by yinnus on 2012-04-29
same message here when i type xscreensaver-demo but i don't get the message about starting it so i assume it's running.  however when i open the prefs for xscreensaver it REALLY slows down my system.

btw.  i'm running 12.04 on a 27" imac with a core i5 and 8 gigs of ram..

---

### Post by Amndeep7 on 2012-04-29
[FONT=Verdana]K, I think I have it working now (since I realized that it wasn't working for me either) - after following a long and convoluted chain of events parts of which may or may not have been necessary.  

1) Open up the terminal.

2) Get rid of XScreensaver (don't need to get rid of settings so not a purge) - [/FONT]```
sudo apt-get remove xscreensaver*
```[FONT=Verdana] - also get rid of all attempts to open it up automatically - I have it set so that I can see all of the autostart commands ([/FONT]```
sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop
```[FONT=Verdana]) so all I needed to do was go to start-up applications menu thats under the gear.  

3) Now this sounds counter intuitive, which leads back to my very first statement, but reinstall gnome-screensaver - [/FONT]```
sudo apt-get install gnome-screensaver
```[FONT=Verdana]

4) Log out and log back in again.  

5) Open up the terminal again.

6) If you don't have [/FONT]```
htop
```[FONT=Verdana], get it.  Then use the F3 search button, type in  "gnome-" and use the arrow keys to get down to the screensaver, press F9  (and then ENTER) to kill it and all of its brethren. 

7) Now get rid of it - [/FONT]```
sudo apt-get remove gnome-screensaver
```[FONT=Verdana]

#8 (cause 8 parentheses keeps on turning into a smiley face)  Reinstall xscreensaver - [/FONT]```
sudo apt-get install xscreensaver*
```[FONT=Verdana] -so as to get all of the extra packages.

9) Log out and back in again.  Open up the terminal again.  

10) This goes back to the website of the guy who created Xscreensaver ([http://www.jwz.org/xscreensaver/man1.html](http://www.jwz.org/xscreensaver/man1.html)) - so now get [/FONT]```
gconf
```[FONT=Verdana] and then do the following command so that gnome/ubuntu doesn't try to restart gnome-screensaver - [/FONT]```
gconftool-2 --type boolean -s /apps/gnome_settings_daemon/screensaver/start_screensaver false
``` - you can also change this through the gui of gconf by opening up gconf in the dash (should show up as configuration settings) and then navigate to the directory thats in the command and then turn off this option.[FONT=Verdana]

11) Now add in the autostart command - so under the gear click on the startup applications button and then click add - the way I did it was to title it Xscreensaver, say that it "Starts Xscreensaver" and then I said that the command it should run should be [/FONT]```
xscreensaver -nosplash
```[FONT=Verdana]   (seems that its acceptable either way about the '-' in the middle, but most people seem to go without, which it what I changed it to).  

12) Now to make it run when you do CTRL+ALT+L like for gnome-screensaver: [/FONT]```
sudo ln -sf /usr/bin/xscreensaver-command /usr/bin/gnome-screensaver-command
```13) Log out and log back in again, should have auto-started.  You can check this by opening up the terminal and running ```
xscreensaver
```You can manipulate settings via either opening it up from the dash or through running ```
xscreensaver-demo
``` which gives errors that I spent some time googling around to figure out how to fix but couldn't find anything.  

Hopefully this fill fix things up for you, like somehow or other happened to me, also I apologize for any mistakes in English, I was too lazy to double check everything, finally, I just want to say that I have absolutely no liability in case everything goes wahoonie-shaped.

---

### Post by A4orce84 on 2012-04-29
Hey Amndeep7,

It worked! Xscreensaver starts when Ubuntu starts now!

The ONLY thing left (which I don't know if this is possible) is that after coming out of standby, my machine goes straight into my desktop.

Is there a way to force it to login, or into xscreensaver and then login?

Thanks again for the help, you rock man!  =)

--Asif

---

### Post by Amndeep7 on 2012-04-29
I appear to be experiencing this as well (along with my graphics going haywire) whenever I resume from the suspend.  I've trolled through the internetz and wasn't able to find a way to fix this - all I can suggest is commenting on this by launchpad bug report: [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/968163](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/968163), I have done this as well.

Also, its wonderful to hear that the xscreensaver stuff worked out.

---

### Post by Amndeep7 on 2012-05-01
Just a reminder to set the thread as solved.

---

### Post by FlyingMG on 2012-10-14
thank you for this post. This helped me solve the same problem, even if I do not really understand, why this has to be done that way... I must have forgot some step the first time I uninstalled gnome to reinstall xscreensaver.

---

### Post by yanosk on 2012-11-17
what's wrong with just adding xscreensaver to startup applications, splash or nosplash ? works for me ...

---

### Post by bpeyser on 2013-02-26
> **Amndeep7 said:**
> 
[FONT=Verdana] 12) Now to make it run when you do CTRL+ALT+L like for gnome-screensaver: [/FONT]```
sudo ln -sf /usr/bin/xscreensaver-command /usr/bin/gnome-screensaver-command
```13) Log out and log back in again, should have auto-started.  You can check this by opening up the terminal and running ```
xscreensaver
```You can manipulate settings via either opening it up from the dash or through running ```
xscreensaver-demo
``` which gives errors that I spent some time googling around to figure out how to fix but couldn't find anything.  


FYI, to fix this error:
```
$ xscreensaver-demo

(xscreensaver-demo:13980): libglade-WARNING **: Could not load support for `gnome': libgnome.so: cannot open shared object file: No such file or directory
```you just need to install [FONT=Courier New]libgnomeui-0[/FONT]
```
$ sudo apt-get install libgnomeui-0
```(along with its dependencies)

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=661174](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=661174)

This is on Ubuntu 12.04 LTS running Cinnamon:
```
uname -srvmo
Linux 3.2.0-38-generic #61-Ubuntu SMP Tue Feb 19 12:18:21 UTC 2013 x86_64 GNU/Linux
```

---

### Post by cadusius on 2013-11-25
A little extra help for anyone with this error. I went to synaptic and installed libgnome2 perl and I stopped having the error when I tried xscreensaver-demo in terminal. Hope this helps

---

### Post by robin15 on 2014-02-27
Well first we have to make the distinction between xscreensaver and xscreensaver-demo.  xscreensaver-demo is the gui for xscreensaver settings.

xscreensaver-demo is an application and does not have to be added to the start up 
programs menu.  What we want is to start the xscreensaver daemon at start up.  After trying all the various solutions.  Changing all the places where there was a Type=applicaton (sic) to Type=application and adding nosplash to command line in the start up programs  menu it still did not start at boot time.  So no the problem was not solved for me.  Without going into details of how I arrived at this solution.

This is what worked for me.  In the additional start up programs menu the command line I used was this.

xscreensaver %F

problema resuelto

check out this site which IMO should be in every linux users knowledge base.

[http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html)

I hope this works for you.
cheers

---

