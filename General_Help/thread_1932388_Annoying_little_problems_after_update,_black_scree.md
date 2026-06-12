---
title: "Annoying little problems after update, black screen after attempted fix"
date: 2012-02-27
forum: General Help
---

### Post by crazybasenji on 2012-02-27
I have xubuntu 11.10 installed on IBM ThinkPad T42. I started with Lucid, then over the past month have upgraded through Maverick and Natty to Oeneric to try and improve my wireless connection to a wireless printer. I could connect to the internet by wireless until this latest upgrade, then it seemed to get stuck in a loop of trying to connect. I would just turn it off and connect via the cable. Which didn't give me access to the printer. That was not a major headache because I could use other computers and other printers -- it just took longer.
 
Last week I got the notice for a bunch of "important securtiy" updates. I didn't scroll through the list to see if anything else was included, just went ahead and downloaded them.
 
Next morning when I started my computer, I noticed I didn't have the little window control buttons in Thunderbird -- I couldn't minimize the window, resize it, or close it except by using CtrlQ. Chromium wouldn't open full-screen size, and I couldn't change it. Firefox worked as well/badly as Thunderbird. Other windows acted the same as Chromium -- took up only about 1/4 of upper left hand part of screen with no way to move or change them. They also blocked my tool-bar, so I couldn't open anything else. Also, drop-down menus were messed up. They would disappear as soon as I moved my cursor off the arrow button. My address bar in Firefox wouldn't auto-fill URLs of websites I visit a lot. 
 
I thought I'd be clever and fix it myself, by using Psychocat's handy removal code to return to pure xfce, except I deleted the bits about banshee and gedit because I like those programs and didn't want them to go away. After I ran the uninstall, I restarted my computer, and now all I get is black screen, after what looks like "panicy" blinking following the xubuntu opening screen. I'm using my brother's laptop to send this (Windows!! It Burns!!!) Is there a way to restore things without doing a complete re-install and losing all my data? I have a lot -- but not all -- of it backed up.

---

### Post by crazybasenji on 2012-03-01
After searching this forum for the last three days, I found a thread describing "the magic key combination" which I was able to use to access the command line -- finally. But then I didn't know what to do, not being particularly knowlegable about using the command line. So I thought I'd try
 
sudo apt-get install xfce desktop 
 
and see if that would put things back. Instead I got this:
 
sudo: Can't open var/lib/sudo/me/tty1: Read-only file system
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened
 
*Now* can someone help me?

---

