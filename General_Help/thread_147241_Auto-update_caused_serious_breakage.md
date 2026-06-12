---
title: "Auto-update caused serious breakage"
date: 2006-03-19
forum: General Help
---

### Post by Steve- on 2006-03-19
I recently had the auto-updater update my kernel. Apart from the ultra annoying fact that it resets my grub config, after rebooting it has broken several parts of my system. The things I know about:

1) Sound. It works on the inital login screen, i get the noise when I can log in. But when I'm inside gnome, I have a speaker with a red cross on it in the system tray, and when I click it, I get a long error the first time, and "No volume control elements and/or devices found." from then after. I tried checking my sound drivers, but that brings problem number two.

2) Synaptic doesn't start. I go to open it, pop in my password and nothing. Nothing at all happens. I can't see it in the system monitor, but I can't say I know what i'm looking for.

Before the problem, I was trying to install my printer in linux. This involved following lots of crappy documentation for the very confusing system. I installed the updates and began trying to get my printer working without noticing I was meant to reboot the kernel. The following process involved problems such as not being able to "sudo gedit ..." a file and having trouble adding myself to a new group. The Users and Groups section wasn't openable before the reboot and not after

I hope someone can suggest something.. this is all such a mess...
I better get my files transferred over to windows so I can do the printing there :/


UPDATE: sudo seems to be completely broken. I can't edit my bootloader to get back to windows!
UPDATE: I am now in windows at least, but sudo is still busted, along with all those other problems.

---

### Post by Steve- on 2006-03-20
Hmm, does this mean I'm going to to re-install Ubuntu then? Seen as noone is able to give me any help...

"sudo -s" asks for my password, but it doesn't give a root prompt. So sudo is still there, but it isn't working?

---

### Post by MJSOnline on 2006-03-20
Nope.  try to boot from the live CD.  Then check your root folder....

---

### Post by Steve- on 2006-03-20
What am I checking my root folder for? I don't see anything special.

---

### Post by Steve- on 2006-03-20
Ok, problem solved.

It seems the tutorial I was following to allow me to set up CUPS properly, got me to clear all of the groups my user is in. The result? Bad things with audio, admin, video. Everything really.

Good news is nlogax could help me in the IRC Channel and I have sudo and friends back. Bad news? There are some remenants of badness on my PC.

The most notable is that the Volume Control has lost function, as mentioned in my first post. Where abouts can I configure it? I do have sound at least.

---

