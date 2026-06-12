---
title: "Remote Desktop Live CD"
date: 2009-08-03
forum: General Help
---

### Post by brad84 on 2009-08-03
I've done a bunch of searching and I'm surprised that I haven't been able to find anything on this topic.

I want to build a Live CD that starts an rdesktop session to a pre-determined server on startup.

The goal is to build this CD and hand it out to staff, faculty, and students so that if they have issues with their computer and need to get to a working one they simply pop the CD in their computer, restart, and poof: they're at a Windows terminal server login prompt.

Could someone point me in the right direction? I've already looked over this page: [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization) and found it helpful, but I need help setting up start-up scripts and how to add them to the livecd.

Thank you!!!!!

---

### Post by brad84 on 2010-01-12
It's been 6 months and no replies?

Is this not possible to do?

---

### Post by bodhi.zazen on 2010-01-12
Do you have the scripts ? Adding them to the live CD should be easy.

---

### Post by brad84 on 2010-01-12
Well all I want is a fast livecd that doesn't have any user interaction which runs:

rdesktop -u username -d mydomain -bfNP termserver.mydomain.com

Then if the rdesktop session is closed, it re-opens the session.

The goal is to have a "thin client" on a cd which I can distribute for when our users have computer issues and need a working system immediately.

---

### Post by bodhi.zazen on 2010-01-12
Sounds like you need a script to act as a wrapper script. Do you have such a script yet ? 

Now that I understand what you want, are you asking someone to write a script for you and then package it onto a live CD ?

What step are you on and what assistance do you need.

---

### Post by brad84 on 2010-01-12
I can figure out the wrapper script on my own. My problem is I don't know how I would go about adding it to a LiveCD. 

I'm messing around with Suse Studio right now but the results are a little heavier than I would like and I can get it to run my command on start up.


Thank you for your help! :D

---

### Post by bodhi.zazen on 2010-01-12
OK, once you have your wrapper script, follow the directions on your previous link for customizing the Live CD.  Basically you need to extract the casper file system, call your script from /etc/rc.local (you may need a sleep of 10-20 before calling your script).

Then package up the iso, including compressing the file system and modifying the md5sums.

Again, rather then re-writing the wiki page, which step are you on or what is it you do not understand ?

---

