---
title: "Ubuntu stops at startup?"
date: 2011-07-10
forum: General Help
---

### Post by Iversen on 2011-07-10
Hello All.

I have a big problem. Tried to enable my LCD TV via HDMI on my Nivida grafik. The system needed to reebot, and now Ubuntu don't start!? The screen turns purble for some time, and then a black screen with alot of starting and stopping messages.

 There is one fail: "Stopping automatic crash report generation"

At the bottom it says:

"Starting GNOME display manager"
"Starting Userspace bootsplash"
"Stopping Userspace bootsplash"

Then the curser is just blinking in the bottom of the screen.

I have tried the system recovery function at startup, but it is not responding. I realy need to get my system back up and running, so I hope someone can help me!?

---

### Post by Iversen on 2011-07-11
No one??

---

### Post by Eleos on 2011-08-07
I am having the same problem.  Doesn't look like anyone knows a solution, my search reveals several people asking the question with no reply.  If I figure it out, I will post here.

-Eleos

---

### Post by Spyderkid on 2011-08-07
we'll what you can do is try and boot into failsafe mode or whatever its called and try and recover some of your files onto a hard disk or USB.
If you need to know how to move them to usb via command line you need to...
```

cd TO THE DIRECTORY WITH THE CHOSEN FILE
mv FILNAME DEVICENAME 

```
then once you backed up your stuff you can either re-install or check the hard disk for errors.

You can check the drive for errors. Use the liveCD and run an "fsck -f" on the drive.



then we'll go from there

---

### Post by Eleos on 2011-08-07
Ok, I reinstalled 11.04.  Here is what I did:

Opened a terminal, typed:

sudo apt-get install startupmanager 

In startup manager, I set the resolution to 1024x768 and color to 24 bits.

Then:

pressed ctrl+alt+F1

sudo service gdm stop

sudo apt-get --purge remove xserver-xorg-video-nouveau

sudo sh NV*

The installation told me that nouveau was still there, and created some kind of config file (it was too fast for me to copy), and the installation failed.  I then typed:

sudo service gdm start

Then I rebooted, and the dim screen is gone, at higher resolution.

I don't know why, but the last time, I rebooted, and was able to complete the installation of the NVIDIA driver, but then it hung at "Stopping User Bootsplash", so I am leaving well enough alone and not going to try and complete the installation.

I hope this is helpful for someone.

-Eleos

---

