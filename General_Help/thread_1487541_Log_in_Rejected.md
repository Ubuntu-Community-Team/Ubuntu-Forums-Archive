---
title: "Log in Rejected"
date: 2010-05-19
forum: General Help
---

### Post by Ron O on 2010-05-19
Suddenly, my one week old "fresh install" of Xubuntu Lucid will not accept my login. It flashes to a black screen for a second, then back to the login screen with NO message (like invalid password)- just another offer to log in.  My prior session was uneventful and did not involve loading any new packages or updates. I tried booting from recovery mode, both from grub and from the installation CD. In recovery mode, it seems to accept my login but gives me a command prompt, at which point I am lost.

This happened once before and I just wiped out the installation and did a complete reinstall, but this time I have too much work in my installation to do this again, and would never trust another install. Lucid is my third version of Xubuntu (all fresh, no updates) and I have never encountered anything like this before. Can anyone please give me some guidance?

---

### Post by deathadder on 2010-05-19
Hi,

Is there anything in ~/.xsession-errors? I've seen posts that have said both .ICEauthority and .nvidia-settings-rc are set with root permission. These should be rw for your user only, if they are set as root then you can run the following to fix it:

```
sudo chmod 600 .ICEauthority && sudo chmod 600 .nvidia-settings-rc 
```

---

### Post by Ron O on 2010-05-19
Problem Solved but Unsolved. Xubuntu liked my bios settings, but changed its mind.

My password must be OK if it is logging me in at command line in recovery mode but not starting the GUI in normal boot mode. In normal boot mode, I entered a known bad password and got "authentication failed". But when I tried using my valid password, I did not get an authentication failure, just a loop back to the log in screen and a refusal to proceed.

At some point, perhaps in recovery mode, I read a message that my system bios was lacking certain security capabilities or that they were disabled. I went through the bios settings and found one entry I was never quite sure of- "Plug and Play O/S  Y or N". I changed it from Y to N and my system booted normally again. So I guess the problem is solved, but I am reluctant to press "problem solved" button because I cannot be sure if this really did it or if the system finally decided to let me in after repeated unsuccessful attempts to log in with a valid User ID and password. If it was the bios setting, why would it suddenly crop up after repeated successful logins for a week or two with the prior setting? Does anyone have a clue?

---

### Post by Ron O on 2010-05-19
deathadder- Thanks for your response but I have an ATI Radeon card. But I have to look at that log anyway. Would you happen to know where the most helpful logs are? I know of at least one whose location has been changed in Lucid- Jaunty- /var/log/fsck/checkroot  Lucid- /var/log/boot.log. The old Jaunty path if used in Lucid goes to a valid file, but it reports "nothing logged yet".

Booting is recovered but some of my settings have been lost and do not respond to resetting- like at shutdown, I get no option screen, even though checked in Sessions and Startup. But I guess that is a whole different line of inquiry.

---

### Post by Ron O on 2010-05-19
This system has resumed locking me out. The graphical login screen has a gray tray at the bottom of the screen rather than the usual blue, with most of the options missing. Once again, when I try to log in, it does not do so, and keeps looping back to the same login screen.

---

### Post by deathadder on 2010-05-20
Maybe the logs in /var/log/gdm/, you might want to have a look for errors (EE) and warnings (WW) in /var/log/Xorg.0.log. Is there anything in your ~/.xsession-errors?

It's possible you're session is corrupted somehow, as suggested in [this bug report]("https://bugs.launchpad.net/ubuntu/+bug/525476") can you deleted ~/.cache and everything in ~/.config/xfce4/? Doing so *will remove* any configuration you've done to XFCE, background etc. 

Another bug suggests that it's an issue with dozens of [xfdesktop processes running]("https://bugs.launchpad.net/ubuntu/+source/xfdesktop4/+bug/329616")...

---

### Post by Ron O on 2010-05-21
Thanks. Now taking a crash course in command line so I can attempt this from recovery mode.

---

