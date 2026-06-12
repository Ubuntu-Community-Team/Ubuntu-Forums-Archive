---
title: "Scratching my head at an issue, wonder If i could pick your brains?"
date: 2010-04-05
forum: General Help
---

### Post by SpookyKristian on 2010-04-05
Must say I made the jump to Ubuntu about a week ago and have found the OS fantastic, a bit of getting used to initially but I gt there - typically I like to solve my own problems and value the experience of knowing how to do it. But this one has me stumped

I have a 80gb internal HDD with a clean install of Ubuntu 9.10 and has been working awesomely all week, however turning system on today - and my system won't go past the initial splash/logo screen and boot into the OS. 

So far have tried - the various f keys to bring up system/BIOS menus to no avail. 
*Thinking maybe its a graphics card issue (as it is the graphics card logo on the splash screen) maybe the card loose etc - took side off system - took out card, reinserted. rebooted same issue 
*checked connections of HDD all fine. rebooted same issue. 
*Took out graphics card, put monitor cable into PC standard connector - same issue. 
*Tried a different hard drive which has a windows xp sp3 clean install on it. same issue - not going past initial splash screen.
A friend advised resetting bios - popping out the battery and reinserting it. Which I did - rebooted - still no progression past the splash screen. 

In the meantime have disconnected the windows hard drive and reconnected up just the hdd with ubuntu 9.10 on it. 

Any ideas?

Thanks in advance

---

### Post by djoxyk on 2010-04-05
when it freeze? on grub choice or when loads the selected OS? try to press 'escape' to see if there's any verbose output while loading

---

### Post by new_tolinux on 2010-04-05
Most systems shows a more useful BIOS-output when you press `ESC` when you see the BIOS splash screen.
If you know what machine you have, or which manufactorer produced your BIOS it's more easy to find out what key you need. Most times it's something like `F1`, `F2` or `F10`, but I've seen more weird combinations also.

---

### Post by SpookyKristian on 2010-04-05
Grub menu, no. 
When you pop system on - the splash screen of the radeon graphics card pops up for like 2seconds, then disappears then goes straight into Ubuntu. normally. Only not today. 

F key wise, i gave them all a shot and reboot next one, and no luck on neither F keys. (Usually F10)

---

### Post by djoxyk on 2010-04-05
is it asus motherboard? try 'del' instead of F's

---

### Post by SpookyKristian on 2010-04-05
it is yes, will give it a shot

---

### Post by new_tolinux on 2010-04-05
If I remember well, ATI doesn't produce BIOS-es.

F10 is by no way the default, as many Phoenix-BIOSes have F2 as their default. In case of Acer F10 actually activates the restore-process (to restore the pre-installed Windows). So it could really pay off to consult the manual of the machine/motherboard.
Like I said: I've seen more rare (weird) combinations also, for example `CTRL+ALT+Return`. You can even try `DEL`.

---

### Post by SpookyKristian on 2010-04-05
unfortunately no success with either, will try and sort out the motherboard manual. hidden somewhere in the depths of my cupboard. Thank you none the less.

---

### Post by estyles on 2010-04-05
> **SpookyKristian said:**
> *Thinking maybe its a graphics card issue (as it is the graphics card logo on the splash screen) maybe the card loose etc - took side off system - took out card, reinserted. rebooted same issue 
Try the same thing with the memory?  It sounds like it might be a memory issue(?).  If you have more than one stick of memory, try removing one, reboot.  If it doesn't work, try the other one...

---

### Post by djoxyk on 2010-04-05
Do you have live CD or any other bootable media? You can try to boot and see if it's video issue or your installation is broken.

---

### Post by SpookyKristian on 2010-04-05
aye, i have 2 sticks of ram. Popped um out and back in. did a reboot
A curious thing has happened. 

Whilst not straight away and immediate as it was before, took a good minute on it being onscreen the splash screen has disappeared and has gone black... and as im typing on this laptop, ubuntu has indeed loaded.

---

### Post by estyles on 2010-04-05
Good to hear.  It's not particularly surprising that it took a while to boot after pulling out a stick of RAM.  I'm not really a hardware guy, but I would guess that if it boots up and sees a different hardware configuration, it will do a quick test, probably including a memory test.  (edit: deleted the rest of what I wrote, because I mistakenly thought you said that you kept one stick out because it was bad...)

---

