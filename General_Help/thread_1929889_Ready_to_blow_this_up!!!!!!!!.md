---
title: "Ready to blow this up!!!!!!!!"
date: 2012-02-22
forum: General Help
---

### Post by meduser on 2012-02-22
On the advice of some members on this site, I formatted my hdd, and reinstalled Kubuntu.... a simple "20 min" installation has me banging my head off the wall now for two flippin days..

My partitions are now setup right. I don't however have a pc that I can use. I have dual monitors, and am running the 11.10 Kubuntu. 

I had my pc running, and all seemed ok. I then went to activate the 3d in graphics. I have a geforce210, with dual monitors running..1 vga, and 1 dvi. After activating 3 d...i was told I need to restart for the graphics to be right. So I rebooted, and the pc started up. When Kubuntu came to the login screen, I only had one monitor....that's weird...usually have 2.  Enter my password, and kubuntu starts. Only one screen, and the panels from the screen are all over the place. So, after reading..I saw that I needed to purge nvidia, using terminal. I did that. I then restarted the pc. At the login screen I get both displays. I log in, and can see the wallpaper that I have added. The panels are all over the place, and the screen will not stop flickering. after 10 seconds of that, the screen goes black. I can enter into a tty, but as soon as I leave the tty screen, the monitors go black again. I went and had a smoke, and when I came back I had the same desktop on both screens, but no panels. If I right click on the screen, I get run command, add widgets, add panel, activities, lock widgets, lock screen, leave, configure page.

If I click on any of those it does nothing. If I try to go to the activities in the top right of the screen, it flashes for all of a microsecond, and then disappears again. If I reboot the pc, it starts all over again. I cannot get anywhere, except tty, by pressing ctrl-alt-f2.

I am so frustrated by Linux at this point. I couldn't spare the "20 minutes" to reload Kubuntu, and now I am 2 days into this, with nothing working. I am a student, and needed to be using my springbreak doing my assignments, not farting around with linux. I need to get this fixed asap.

Anybody...please....help....me.....:p

---

### Post by snowpine on 2012-02-22
> **meduser said:**
> I had my pc running, and all seemed ok. 

Repeat the process, stop here, and get your school work done.

Use "messing around with 3-d-accelerated-dual-monitor-widgets" as a reward for having completed your assignments, cool? :)

---

### Post by meduser on 2012-02-22
> **snowpine said:**
> Repeat the process, stop here, and get your school work done.

Use "messing around with 3-d-accelerated-dual-monitor-widgets" as a reward for having completed your assignments, cool? :)

what does that mean? No way to rescue this in tty? No not cool.


I really don't have all day to do this again. I am sure I am not the only one who has enabled the 3d graphics and had issues. Reinstalling should not be the end all all the time. I had my pc setup the way I like, but the home folder was in the same partition as the root folder, and I ran out of room. There has to be a way in terminal to fix the display.....

I thought linux was supposed to be nicer to use than windows. So far....I hate it. I have had nothing but issues, and the only response seems to be..re install...what a joke

---

### Post by meduser on 2012-02-22
I just discovered that I can go into gnome desktop, and everything is still there...so it is an issue with the kde environment. How can I reinstall the kde environment?

---

### Post by snowpine on 2012-02-22
Do your school projects require you to use KDE or can you use Gnome? 

Just trying to help you see the bigger picture here. :)

---

### Post by meduser on 2012-02-22
ok..all fixed. Did not have to reload...heres what I did..

I went into gnome environment, and entered the terminal.
I then mv .kde to back up.
I then restarted the pc, and entered into the kde environment. 
Because I had moved the .kde file, kubuntu recreated the file (from what I have read). 
Now all is fine. I am back up, and able to navigate. From what I can gather, the KDE desktop environment was corrupted when the Nvidia drivers where purged.

---

### Post by meduser on 2012-02-22
> **snowpine said:**
> Do your school projects require you to use KDE or can you use Gnome? 

Just trying to help you see the bigger picture here. :)

I am in a class for IT, and one of the 5 courses I am in is a Linux course. We are using Fedora, and some Ubuntu, but that is mostly for comparison. I am using Kubuntu, sort of as a middle ground. I am trying to submerse myself into Linux, but keep hitting roadblocks along the way

---

### Post by snowpine on 2012-02-22
Fedora and Ubuntu are very nice, I have used both of them in the past. Good luck with your class. :)

---

### Post by meduser on 2012-02-22
Thank you. I have just had a rough go of things with Linux. Up until 5 weeks ago, I had never even seen a linux system. 

I like Kubuntu for the most, just find it to be harder to trouble shoot when you are so new to it, and because I am so new to it, I am making a tonne of mistakes.

---

