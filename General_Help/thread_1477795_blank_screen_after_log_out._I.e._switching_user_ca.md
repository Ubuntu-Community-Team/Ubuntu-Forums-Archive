---
title: "blank screen after log out. I.e.: switching user causes nonfunction."
date: 2010-05-09
forum: General Help
---

### Post by quatar on 2010-05-09
Hi. I don't know how to google this problem because nothing actually happens... it only stop working!

My system has two users, say "user-one", who administrate, and "user-two", with default permissions.

I'm using "user-one", then I decide to use "user-two" so i select "user-two" from the menu in the indicator applet. When i've finished, i log out "user-two". 

When i press "log out", ubuntu is expected to show the locked screensaver of "user-one". On the contrary, it only shows a blank screen, where keyboard hits and mouse clicks are ignored. Nothing happens trying ctrl+alt+f1...f8; the caps lock light doesn't respond to the caps lock key. Only the "k" sysrq works fine but it obviously kill my session with "user-one".

I'm using Lucid i386 on a Sony Vaio VGN-NR31S/S laptop.

Thanks

quatar

---

### Post by oliwally on 2010-05-09
I've got the same problem using a desktop 'puter. Running Kubuntu 10.04, added a new user, logged out to switch user - this results in a black screen with keyboard/mouse totally unresponsive.

Any solutions?

---

### Post by quatar on 2010-05-10
I have also reported there: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/578139](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/578139)

---

### Post by RotsiserMho on 2010-05-16
I have this exact same problem.  Fresh install of Kubuntu 10.04.  If I logout, I just get a blank screen and can't do anything.  I'm on dual monitors...perhaps that's a contributing factor?

---

### Post by ankit singh on 2010-05-16
even i am suffering from this.

---

### Post by mygoldrush on 2010-05-16
I am having the same problem with 10.04 LTS,  I'm getting a blank screen when I try to switch users.  I then have to do a hard reset of the PC.  Is there a fix for this bug?

---

### Post by NotMarkus on 2010-05-21
Having the same problem. I did a hard reboot a few times, but then I found that **Ctrl+Alt+F8 (or F9 sometimes?) will bring up the login screen**. If I try to log in to the frozen account, it will give me a blank screen. But I can log in to the non-frozen account, and I can restart GDM from there, or I can just reboot from the login screen.

This bug is extremely annoying and has been around for years. It really deserves some attention.

---

### Post by tzg6sa on 2010-05-24
I am suffering from the same issue...

---

### Post by gee42 on 2010-05-24
Not sure of helps the dialogue but I can see these symptoms on my own recent fresh install of 10.04. I did some experiments to see if the nvidia drivers were involved and these are my findings.

Without the nvidia driver, and I assume using the Ubuntu drivers, I saw similar symptoms to those above. Login as user A switch to user B then switch back to user A and you get a black screen before any opportunity to enter password for the switch. I got different results without any pattern - sometimes a black screen, sometimes a very dim gdm screen. In all situations I was able to either switch back by just being able see the gdm screen or force a close of the X by using ctrl-alt-backspce.

My fx5200-based install gave me an option to use either the 96 or 173 nvidia drivers. With the 96 version I got very similar results to the Ubunutu driver and was able to recover as for the Ubuntu version.

With the 173 version the only recovery method was the power button!

My view is that it is not directly due to drivers, they just give different symptoms to an underlying issue?

---

### Post by gee42 on 2010-05-31
ok, I found another thread exploring this issue and tried the suggestion of uninstalling gnome-screensaver:

[http://ubuntuforums.org/showthread.php?p=9387908#post9387908](http://ubuntuforums.org/showthread.php?p=9387908#post9387908)

See my follow-up: I uninstalled and fixed the defect and then the defect remained fixed after I re-installed??

---

### Post by IngoRatsdorf on 2010-07-13
This one fixed it for me:
[http://kubuntuforums.net/forums/index.php?topic=3111707.0](http://kubuntuforums.net/forums/index.php?topic=3111707.0)

You have to terminate the server after session end. It seems to be an X-Server problem. You have to edit /etc/kde4/kdm/kdmrc for KDE, no idea about Gnome. Would assume similar settings to be applied.

---

### Post by Diego318 on 2010-07-26
Hi guys, 

Im still having this problem, that fix didn't work for me. 

specifically, when i log out I get a black screen with 5 blue squares at the top (looks like the background of the login screen), and I'm still able to use the mouse and change ttys. 

This only happened after i changed some system display settings (login splash screen, compiz..).  I have since switched them back to defaults. Still with the same issue. 

any suggestions would be greatly appreciated.  (also, this is my first buntu install :p)

System:

Amd X6
Asus integrated Radeon 4290  
Kubuntu 10.4

---

### Post by robc02 on 2010-07-28
Same problem here.
Tried reinstalling gnome-secreensaver - no change.
Tried uninstalling gnome-screensaver - no change.

I have now installed gnome-screensaver again - still no change.

Am on Lucid - fresh install. Using nvidia-96 proprietary driver for GeForce 3 Ti 200

---

### Post by singletrackmind on 2010-08-13
Same here. Setup an account for the wife and got it all nice and pretty for her (to convince her MS is evil and unnecessary) then the dang thing locks up every time. Not helping me build a case that's for sure! :) 

I've seen several posts regarding this. Anybody got a fix other than the screen saver workaround?

---

### Post by foxxa on 2010-08-30
Wife angry here too... once I convinced to go on a good os choice...
got happy with wobbly windows... got really annoyed by this... this is a dealbreaker...
I prefer BSOD than a death screen.
I really hate the idea of using one profile only. It's all deja vu all over again!!!!
¿Going back to Windows XP Home is a solution?

---

### Post by IngoRatsdorf on 2010-08-30
This has all to do with %&^*^*&*(&*(()*) nvidia driver.
I have switched to nouveau and all is working fine. Multiple session, even sleep mode.

Did all not work with the nviadia driver.

Problem: Absolutely no 3D and no openGL, so no desktop effects and some rather slow graphic performance. But HEY - at least working.

Extremely annoying really.

---

### Post by zwarich on 2010-09-13
I had this problem as well and tried various things suggested as workarounds all to no avail. It wasn't the screensaver, it wasn't sync to vBlack, etc. 

What finally fixed it was updating the NVIDIA driver from "version 173" to "current". System->Administration->Hardware Drivers

Hope this helps.

John

---

### Post by IngoRatsdorf on 2010-09-14
NVIDIA has released new drivers in August 2010 that added compatibility to X server > 1.7

Added  support for X.Org xserver 1.8.
Fixed  a bug that could cause X.Org xserver >= 1.7 to hang when restarted.

So I guess we should all retry then?

---

### Post by aarons6 on 2010-09-30
i have this issue as well.. fresh 10.04 kubuntu install with ATI graphics..
 
any fix?

---

### Post by e.meitner on 2010-10-27
Try hitting CTRL-ALT-F7 through F12. If one of these gets you back to a login screen then you may want to take a look at this bug report and click "Does this bug affects you" if you can reproduce it as described in the bug description.
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/40011](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/40011)

---

### Post by IngoRatsdorf on 2010-10-27
> **IngoRatsdorf said:**
> NVIDIA has released new drivers in August 2010 that added compatibility to X server > 1.7

Added  support for X.Org xserver 1.8.
Fixed  a bug that could cause X.Org xserver >= 1.7 to hang when restarted.

So I guess we should all retry then?

As I said before, this bug is related to display servers not compatible with the latest X.org. If you have Nvidia, update your driver through the nvidia website, do not use the repos, they are outdated.

The above fixed all issues for me and believe me, I tried everything else mentioned in this thread (and others).

---

### Post by Rebelli0us on 2011-12-07
Same problem here, switching users crashes the OS. We get a black screen and have to reset the machine. Using non-proprietary AMD driver.

Sometimes there's an error message about "mini-greeter" or something. Somebody fix it please, this bug destroys all active sessions!

---

### Post by Apv507 on 2011-12-11
I'm using the AMD driver installed from the site through Terminal and everytime I log out to switch sessions I get a black screen and have to restart several times before I can get my desktop to show.

---

### Post by Apv507 on 2011-12-11
> **Apv507 said:**
> I'm using the AMD driver installed from the site through Terminal and everytime I log out to switch sessions I get a black screen and have to restart several times before I can get my desktop to show.

I updated and restarted and my problem was solved.

Running a Radeon HD 5670 with drivers install like this:

[http://askubuntu.com/a/67344](http://askubuntu.com/a/67344)

---

