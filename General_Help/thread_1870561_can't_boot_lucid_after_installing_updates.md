---
title: "can't boot lucid after installing updates"
date: 2011-10-27
forum: General Help
---

### Post by defed on 2011-10-27
i did a couple lucid 'auto updates' thru synaptic this morning, then on the next reboot, i can log in, but the boot hangs when it gets to the desktop. the sound plays, generic desktop wallpaper, blank gnome panel, mouse moves and that's it. loading in failsafe makes no difference.
 
i was able to get into synaptic using the live cd, and i can see the 7 updates i did this morning, just not sure how to undo them...or if it is even possible to revert back.
 
the only thing i can do from a boot is use ctl/alt/f1...just not sure what to do when i get there.
 
been searching the web for answers, but so far, haven't found too much.
 
thanks.

---

### Post by defed on 2011-10-27
i think i may know which update may be causing my problem, just need to figure out how to 'force version' in terminal, as it doesn't seem to work thru the graphical manager with the live cd.

---

### Post by defed on 2011-10-27
or not....rolled the 8 updates back, still hangs at desktop.

---

### Post by defed on 2011-10-27
i had a 'disk check' after one of my many reboots, passed.
 
now, in safe mode, it will load my desktop wallpaper and desktop icons, still no panels or mouse button functions.

---

### Post by 741Baus on 2011-10-27
Hi defed try this start in safe mode drop in to root shell
 
```
sudo apt-get install gdm && gnome-panel
```

```
start x
```

I had this strange behavior before after updates and this fixed it , you may get a message that these are already installed if so then I'm fresh out of ideas .
                     Peter

---

### Post by defed on 2011-10-27
thanks, i will try it.  i can't even fully boot in safe mode...but i can get far enough to ctrl-alt F1 and get into terminal, or i can boot in 'xterm'.
 
after it hangs, ctrl-print scr-k will log get me back to the login screen.  everything works fine there.
 
funny thing, i left it sit where it hangs....the HD is cranking non stop for the last 15 mins.  it finally loaded my desktop wallpaper and icons, and i could actually click on some things w/ the mouse, but still not right and no panel.
 
downloading a new iso, since i tried to install it onto another drive to try some things but my live CD has a problem.  i can run from it, but not install.

---

### Post by defed on 2011-10-27
when i tried to install both as you typed, i got ==> gdm - newest version already installed, and gnome panel:2678: gtk-warning **:cannot open display
 
if i did each separately, says newest version of each already installed.
 
i never was too good at manually controlling x...start x ==>  start: unknown job: x
 
i have seen other error messages that indicate a problem 'opening the display' while messing around...which seems like everything is working except for the fact it won't load x properly.

---

### Post by defed on 2011-10-27
whatever it's doing...if i leave it sit long enough, in terminal, it will give messages such as:
 
out of memory, kill process 2444 (gnome session) score 5999645 or a child
killed process 2478 (ssh-agent)
killed process 2499 (gnome-panel)

---

### Post by 741Baus on 2011-10-28
Sorry defed I put a space in second command should be 

```
startx
```

after reading your reply about gdm & gnome-panel already newest versions , I'm pushing the limits of my experience in trying to help you perhaps removing,purging & reinstalling both these may help.
                   Peter

---

### Post by defed on 2011-10-28
thanks.

i've got a new install running on another HD, was too much of a pain using the laptop.  been reading about gnome/gnome panel/x issues.  seems it may be something along those lines, as everything works fine at the log in screen...only locks up when it enters the desktop.

the new install installed the updates that i think may have messed up my other install....but it appears to be working fine still.  so not sure why it went bad.

---

### Post by 741Baus on 2011-10-29
Glad to hear you've got a back up machine , I had a computer hardware failure and the computer says no at boot wont boot to post I've done every thing I can think of even replacing battery no go so of to repair shop Monday ATM am posting from my smart phone 
      cheers defed 
             Peter

---

### Post by buffyfanatic250 on 2011-12-01
I'm having a similar problem with my Lucid install, except it didn't happen after an update. My power supply went up on me and whenever I turned it on nothing would happen. I replaced the power supply and now it boots up fine but it gets to the desktop and will only load Docky and the wallpaper before just hanging. Aside from the pointer from my mouse nothing else shows up but if I leave it for a while the screensaver will come on. Occasionally after logging in, a "power manager is still running" dialog box will show up before taking me to the desktop and hanging. I have been unable to find anything close to my problem aside from this thread

---

