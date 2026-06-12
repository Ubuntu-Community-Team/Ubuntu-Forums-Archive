---
title: "Restoring XWindows functionality"
date: 2011-06-03
forum: General Help
---

### Post by meburke on 2011-06-03
My system boots directly to the terminal and I need coaching on getting back to entering XWindows/Gnome desktop.

Here's how I got into this mess:

I had upgraded to 10.10.

When I checked to see why I couldn't do math on my graphics card gpu's, I found it was disabled.

I enabled it and I got a message that my driver was out-of-date and a new version could be installed for me. (But it was working and I probably should have left it alone...)

I clicked the button to upgrade, and then was back to not having an nVidia graphics card and nothing could fix it. I should have known better: I had a similar problem in my previous installation and had to manually install the drivers from the nvidia script.

So I downloaded the latest drivers package (which is newer than the launchpad package) and tried to install it, but got the famous message that I couldn't install it while gdm was running.

(Now this is where it gets interesting...) I couldn't stop gdm!

NONE of the normal stuff I've used to stop the service worked. I tried stopping with the service command, init.d stop and even tried to kill the process manually. No matter what I did, gdm would reassert itself. No matter what, I would find myself rebooting into X.

I found a forum post that said the only way to fix this was to rename the conf file and restore it after I installed the nvidia drivers. I did that, and now the system seems to just dump me to the terminal session. (Meaning, I can't tell if it even tries to start gdm.)

The reconfig didn't fix it, there is definitely something wrong with the .conf and init scripts, and before I wade into X11 hell I would like a map. Can someone point me to a set of instructions for testing and repairing XWindows from the command line? I'm willing to spend this whole weekend bringing my knowledge up-to-date. It might be good for me to go back to the very basics and do some incremental troubleshooting.

The nVidia card is a PNY GeForce 9800 GT. I can write code to thread and do complex math (from the command line)since I installed the drivers, and it seems to be working very well.

Thank you,

Mike

---

