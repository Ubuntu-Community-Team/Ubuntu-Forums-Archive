---
title: "HELP! Stuck in Recovery Terminal!"
date: 2011-06-26
forum: General Help
---

### Post by paulrosk on 2011-06-26
OK I'm new to Ubuntu, been running PCLinuxOS for a while and thought I'd check out Ubuntu, I LOVE IT! Only one problem. I recently installed it and after getting the entire thing loaded and setup I messed up on a sound driver. Went to the LOGIN SCREEN settings and selected RECOVERY like a DOPE! Now I'm stuck in a bootup login screen that always goes to a small white terminal in the upper left corner! I've tried EVERYTHING from the forums to get back to booting into the GUI, no luck! Is there a way to reset the LOGIN SCREEN to boot to Ubuntu GUI from the terminal? I really don't want to reinstall and reconfigure this whole thing again!
 
Thanks for any help you can send my way ..
 
Paul

---

### Post by coldraven on 2011-06-26
Try ```
sudo /etc/init.d/gdm start
```or
```
startx
```

---

### Post by trizrK on 2011-06-26
> **coldraven said:**
> or
```
startx
```
Starting the X window system doesn't work

---

### Post by garvinrick4 on 2011-06-26
If you are stuck trying to get into 11.04 gnome unity interface:
```
unity --reset
```To get into a terminal if you cannot use below:
ctrl/alt/F1
If you need to start gdm
```
sudo service start gdm
```If you need to get to login screen from terminal:
```
gnome-session-save --kill
```If you just need to see if you can use 3D unity interface using compiz (all should say yes)
```
/usr/lib/nux/unity_support_test -p 
```

---

### Post by paulrosk on 2011-06-27
Thanks to all for the suggestions, I'll give then a try. I found a way to get out of the login terminal. First I have to issue this:
sudo service gdm stop

which gets me to a standard looking full screen terminal, then I issue this:

startx

and I get back to my GUI, but when I try to change the LOGIN SCREEN settings and attempt to UNLOCK the screen, UNLOCK does nothing, the screen remains greyed-out, I also notice some apps can't load, can't find certain things, so I'm only 1/2 way there.

Paul

---

### Post by paulrosk on 2011-06-27
OK tried the "unity --reset" system came back with command not found. I'm running Ubuntu 10-10 maybe that's whu. I did a "apt-get install unity" and it installed with errors, then when I ran it, came back with all kinds of errors, so I'm still stuck in the GUI not being able to "UNLOCK" the LOGIN SETTINGS screen.

---

### Post by trizrK on 2011-06-27
> **paulrosk said:**
> OK tried the "unity --reset" system came back with command not found. I'm running Ubuntu 10-10 maybe that's whu. I did a "apt-get install unity" and it installed with errors, then when I ran it, came back with all kinds of errors, so I'm still stuck in the GUI not being able to "UNLOCK" the LOGIN SETTINGS screen.
Can you show the errors?

---

### Post by paulrosk on 2011-06-27
The unity erros don't matter now I guess, I did a:

gnome-session-save --kill

and then a startx and I got back to my GUI boot
and was able to UNLOCK the LOGIN SETTINGS, set it back
to a normal Ubuntu boot screen and all is well, I boot up
right into the GUI now.

But here's the problem that started this whole mess, I was
messing around with different mixers and somehow install this thing called "JACK" which totally erased all my other mixer settings (which used to work) and screwed up the sound card
settings. When I went back in to remove "JACK" the package manager says it's an unsupported package and won't remove it!
I guess I must have removed some support files for "JACK" by
mistake and it's "lost" somehow. Now I have to figure out what I did and remove all of "JACK" somehow to get my ALSA mixer back! I can't even do a "reinstall" of "JACK" because now it's an
unsupported package! Wow did I ever mess things up!

I LOVE Ubuntu, but boy it can be "hostile" sometimes!

---

### Post by garvinrick4 on 2011-06-27
> OK tried the "unity --reset" system came back with command not found.  I'm running Ubuntu 10-10 maybe that's whu. I did a "apt-get install  unity" and it installed with errors, then when I ran it, came back with  all kinds of errors, so I'm still stuck in the GUI not being able to  "UNLOCK" the LOGIN SETTINGS screenYes unity --reset command was for 11.04 with gnome unity interface running on compiz.

---

### Post by paulrosk on 2011-06-27
I want to thank everyone who responded to my dilemma, thanks again! I got my GUI boot back and removed "unity" without any problems. Everything seems to be back to normal, but I still have that problem trying to remove that "JACK" audio package and my ALSA mixer comes up with an empty window, reports that the sound card can not be found. So I guess I somehow removed the sound card driver messing around installing "JACK". So I'm back to where I was when this whole "terminal logon" mess started. At least I have the system back, now I have to find out how to reinstall the sound card!

---

### Post by paulrosk on 2011-06-27
It seems by me messing around (due to a Python program that failed to locate the sound system) I must have removed the sound card from my system which is (I guess) why the sound packages installed come up as "unsupported". How do you reinstall hardware in Ubuntu? I checked all the menu options, nothing there about installing hardware, just a selection about "drivers" which comes up empty when I open it. So how do you make Ubuntu 10-10 see the hardware in your system and install the drivers for it?

---

### Post by paulrosk on 2011-06-27
OK, got the sound card reinstalled, the GNOME mixer works fine and the sound is back! But I still have the "remnants" of "JACK" in the package manager that I can not remove! Still comes back saying "Package Not Supported". Don't know if I should just leave this alone and ignore it now that ALSA is working again, or if it's going to cause problems in the future. Any Ideas?

---

