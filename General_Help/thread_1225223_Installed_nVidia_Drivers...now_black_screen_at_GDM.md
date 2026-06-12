---
title: "Installed nVidia Drivers...now black screen at GDM"
date: 2009-07-28
forum: General Help
---

### Post by jdeppel on 2009-07-28
I apologize if this has been asked before...I did search, but with the search terms I was trying, I received thousands of results...However, most info regarding the problem I'm having were from people using Feisty or earlier...so I'm hoping someone here can help.

I downloaded the latest official drivers from nVidia for my card (GeForce FX5900UT) from the command line (using CTL+ALT+F1), and all seemed to go fine, no errors. However, upon trying to exit the command line (CTRL+ALT+F7 right?), I was greeted by a completely black screen, except for a cursor blinking in the upper left hand corner. I decided to reboot the machine, and after the Ubuntu load screen finished, instead of the GDM login screen, I have a blank screen. No drum sound, nothing, which leads me to believe it's not COMPLETELY a graphics problem.

Now, I installed the drivers because I was having problems in Jaunty with X-Server randomly crashing at times, noticing some threads online mentioning installing the latest drivers direct from nVidia alleviated the problems.

Should I reconfigure X-Server or does anyone have a workaround? I can't even boot up in Recovery Mode...unless I choose the Root Shell option.

---

### Post by Zorael on 2009-07-28
When X fails to initiate graphics it'll stop completely, so no drums are to be expected.

The log file for X is at **/var/log/Xorg.0.log**. Does the end of it say anything of interest?

It has to be read after X failed to start, so I'd suggest you try to boot up into the black drum-less screen, then ctrl+alt+f1 and copy that **Xorg.0.log** file to an alternate location (home dir?). Then paste the contents here. Use 'fix X' from the recovery menu if you want to revert to the non-accelerated nv driver (so X starts, allowing you to start a browser).

Getting X to start (e.g. via fix X) will overwrite the log file, so you have to make a copy of the log when it couldn't start.

---

### Post by jdeppel on 2009-07-29
Well, the log file wasn't there, probably due to my efforts to try to get X-server reconfigured. I also tried the xfix option in Recovery Mode which apparently did nothing. The system sort of boots now, but instead of a GUI, I'm dropped to TTY mode. 

I'm just going to take this as a sign from a higher power that I'm supposed to install Karmic.

---

