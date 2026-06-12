---
title: "Where Is The Screens and Graphics Tool?"
date: 2009-12-14
forum: General Help
---

### Post by crokett on 2009-12-14
or what package do I need to install to find it? 

It is not under System->Administration
It does not come up as a choice when I right click Applications then Edit Menus.  

I have Ubuntu v9.10 installed under Virtual Box in Windows 7 with Guest Additions installed.  I am trying to get the resolution past 1024x768 to the max my system supports.

---

### Post by cormano on 2009-12-14
Its on preferences>display

---

### Post by crokett on 2009-12-14
I saw that.  Max resolution is what I already have.  I also have 'unkown' monitor listed.  I believe I need to select a VirtualBox video driver, except one is not there. I think I can select it from the Screens And Graphics tool except I can't find the tool or a package to install it from.  System->Preferences->Display doesn't give me an option for a monitor to select.

---

### Post by akakingess on 2009-12-14
Have you tried adding the "Resolution Switcher" application? I know it's in Karmic, but don't know about 8.10. Just a suggestion and see what you can find.

---

### Post by crokett on 2009-12-14
Tried that.  The problem is Ubuntu thinks the max resolution supported is 1024x768.  I found some instructions to change that by setting the monitor type to the Virtual Box driver.  They both say to use the Screens and Graphics tool.  I can't find that on the system anywhere.  I thought about editing X11.conf directly and adding the resolution but apparently that file doesn't exist any more.

---

### Post by ST3ALTHPSYCH0 on 2009-12-14
They (foolishly IMHO) took out the Screens and Graphics tool. If your machine has an xorg.conf it will be used, but it's no longer required. I used an 8.04 live CD to use the screens and graphics tool. Click the resolution link in my sig if you're interested in the whole story. I've been trying to figure out who to petition to get SandG back, but brainstorm says it's not an idea and launchpad says it's not a bug.

---

### Post by crokett on 2009-12-14
Hmmph.  Why would they do that?  Thanks for the tip.  This a VM for me to play with - so not sure I will go through all that. I will think about it.  Thanks for the workaround though.

---

### Post by ST3ALTHPSYCH0 on 2009-12-14
Evidently screens and graphics had a nasty tendency to break working configurations.... my question is why someone would use it if they were properly set up... and why they wouldn't back up a known working configuration before making changes.

---

### Post by crokett on 2009-12-14
Well fix it, don't remove it cause it is busted.

As to why people don't back stuff up, my day job is fixing mission-critical solutions that have gone sproing.  You'd be amazed at how many people don't have regular backups of their systems.

---

### Post by ST3ALTHPSYCH0 on 2009-12-15
I can't say much... I don't have any backups for want of space and money to purchase more space.... but I do backup a working config fiel before making changes. If I can't find the right people to beg to get it back I would.... and I'd let everyone else who has had to figure out how to manually edit a blank xorg.conf know too!

---

### Post by akakingess on 2009-12-15
> **crokett said:**
> Well fix it, don't remove it cause it is busted.

As to why people don't back stuff up, my day job is fixing mission-critical solutions that have gone sproing.  You'd be amazed at how many people don't have regular backups of their systems.

All I have to say is +1 !!!!!

---

