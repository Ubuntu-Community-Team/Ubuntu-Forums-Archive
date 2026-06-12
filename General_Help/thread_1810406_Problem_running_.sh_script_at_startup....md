---
title: "Problem running .sh script at startup..."
date: 2011-07-23
forum: General Help
---

### Post by djimenez1st on 2011-07-23
Hi everyone:
I recently joined the ranks of Ubuntu users, and I'm damn proud of it... but, I've been having some trouble running a script. Here's the whole situation...

I recently installed 11.04 on my laptop and everything went well enough... except for the nvidia x drivers for my video card. It seems that proprietary drivers have to be installed separately, and without them the compiz/unity won't be able to run properly (visual effects and such). I installed the nvidia drivers but I got into some trouble while connecting my lcd tv to my laptop; It seems that the nvidia x drivers are unable to recognize the right resolutions that my tv usually handles (I use windows 7 also, and it works just fine). It all comes down to the resolution difference between my laptop and my tv, which keeps me from viewing or using my tv in high resolutions.

I looked up some options on the web. I found some saying that this could be fixed by modifying the xorg.conf file (does not exist on 11.04...), or running a command line for xrandr..... which is what I am doing. I created a .sh file as follows:

[I]#!/bin/bash
xrandr --newmode 1368x768 85.25  1368 1440 1576 1784  768 771 781 798
xrandr --addmode VGA-1 1368x768
xrandr --addmode LVDS-1 1368x768
xrandr --output VGA-1 --mode 1368x768
xrandr --output LVDS-1 --mode 1368x768 [/I]

Then I looked around for a way to make it run at startup and I ran into a solution in this forum (doesn't work for me). Which consists of creating a file as follows:

[I]#!/bin/sh 
# run fix-resolution at boot  
case "$1" in 'start')     /usr/local/bin/fix-resolution/fix-resolution.sh start     
;; 'stop')     
;; *)    
 echo "Usage: $0 { start | stop }"     
;; esac exit 0[/I]

Now a symlink has to be created:

* cd /etc/rc2.d ln -s ../init.d/fix-resolution S70fix-resolution*

And Finally, make the script executable:

* chmod +x /etc/init.d/fix-resolution*

This seemed to work for the user that posted originally, but it still doesn't work for me...
Now, I don't think the problem is the script itself since I can always run it like this:

* /etc/init.d/fix-resolution start *

Somehow, the script won't start when booting...

I appreciate the attention and any solution you may have for this dilemma....
Thank you in advance...

---

### Post by galvatron408 on 2011-07-23
What you posted says that the script should be run in run level 2 but you're in run level 5. see the info below.


[http://en.wikipedia.org/wiki/Runlevel](http://en.wikipedia.org/wiki/Runlevel)

cat /etc/rc5.d/README 
The scripts in this directory are executed each time the system enters
this runlevel.

The scripts are all symbolic links whose targets are located in
/etc/init.d/ .

To disable a service in this runlevel, rename its script in this
directory so that the new name begins with a 'K' and a two-digit
number, and run 'update-rc.d script defaults' to reorder the scripts
according to dependencies.  A warning about the current runlevels
being enabled not matching the LSB header in the init.d script will be
printed.  To re-enable the service, rename the script back to its
original name beginning with 'S' and run update-rc.d again.

For a more information see /etc/init.d/README.

---

