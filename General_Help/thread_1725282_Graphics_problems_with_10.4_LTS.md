---
title: "Graphics problems with 10.4 LTS"
date: 2011-04-09
forum: General Help
---

### Post by meburke on 2011-04-09
I just upgraded from 9.10 using the button on the update manager. I am experiencing a couple of graphics problems.

I have a PNY NVIDIA GeForce 9800GT graphics card which worked beautifully on 9.10. Now, my system boots up in "low graphics mode" and and I have to restart X in order to get my full screen resolution. Graphics are slow and jerky, even slideshows. Xscreensaver disables move and fade in order to preserve resources.

It shows the right monitor (Acer 20" 1680x1050).

When I try to look at my nvidia settings, I get an alert that says I am apparently not using the nvidia drivers, run nvidia-xconfig from root and restart X. However, X never restarts. I'm left in terminal mode.

Taking out the nvidia card leaves me with a munged screen I can't see/read/navigate from.

This only happens with 10.4. On the other hand, the live CD works great, as does the Live 10.10.

Interestingly enough, I was just trying to post this message about 30 minutes ago and the display completely hung the system.

Can anyone point me to some resources for making this work?

Thanks,

Mike

---

### Post by 01mf02 on 2011-04-09
In such a case, I'd create a new user and try it from there.
Also maybe I'd move xorg.conf away to a safe location and then try starting X with a fresh xorg.conf. I think there's an nvidia tool which does that ...

Also, how did you install the nvidia-drivers? Via standard tools?

---

### Post by meburke on 2011-04-10
How do I mark this [SOLVED] ?

OK, I noticed that I had the version .19 Nvidia drivers in a shell script in my Downloads file (from my previous ubuntu installation). I went to the Nvidia site and found out that the current version was .44 . So I downloaded the new drivers to my Downloads directory.

When I rebooted my system, it told me that X was in low-graphics mode (among other things it couldn't load nvidia drivers) and on the next screen I chose to drop down to the console. I then switched to my Downloads directory to verify the file was there.

I made sure gdm was not working ( service gdm stop said "no instance" and ps -ef verified it) and then ran:

```
sh ./NVIDIA-Linux-x86-260.19.44.run
``` 

This little script told me a bunch of things. First, it told me I had a misconfigured previous version of the older Nvidia drivers. It told me that the Nvidia kernel module failed to compile and configure properly. It told me that the Nouveau drivers were installed, maybe misconfigured, and that they would have to be uninstalled before I could proceed.

Then, it offered to uninstall the Nouveau drivers by running a script that modified the startup script. I chose to let the utility run the script and it told me to reboot my system and try to run the installation again.

I did this, and now everything works. Not only that, but it ran a cleanup script to look for conflicts in the configuration files and the GTK configuration files.

I hope this helps someone else, and I appreciate the suggestions.

Mike

OT: Seriously, would any regular BBS/Forum users tell me how I should change the tag to [SOLVED] ?

TNX, meb

---

### Post by pme 72 on 2011-04-10
If you navigate back to the top of the posts there should be a Menu item "Thread Tools". If you click on that there should be an option to mark the thread solved. I believe that option is only visible to the originator of the post.

---

### Post by meburke on 2011-04-16
Thank you.

---

