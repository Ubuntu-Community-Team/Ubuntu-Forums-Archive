---
title: "Screen Resolution problems"
date: 2010-05-07
forum: General Help
---

### Post by trevzilla on 2010-05-07
So I first want to start this question with a little disclaimer.  I have been on Ubuntu for a total of about 1 hour now, as I have finally made the switch from Windows. So far so good, but I do have some learning to do.

First off, when I got Ubuntu 10.04 installed, everything worked great!  Video lagged a little however.  No biggy.  The next time I booted up, it asked if I wanted to install video card drivers.  I thought this is why my video was lagging, so I said yes.  It then automatically installed my nvidia card drivers.

Then when I rebooted, I was greeted with a 640x480 screen resolution.  When I go to System->Preferences->Monitors, I am given a warning that says: "It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics drivers vendor's tool instead?"

Regardless if I hit "yes" or "no" I am brought to windows that should allow me to change resolutions.  However, the only resolutions I can choose are 640x480 and 320x240.  I know my "monitor" can support higher resolutions as I was running it at higher resolutions before the switch to Ubuntu.  (I put monitor in quotes, as I am using a large rear projection T.V. as my monitor)

So, any thoughts on how I can get a higher resolution?  Any help is very much appreciated!

Thanks so much!
Trevor

---

### Post by cak3 on 2010-05-07
The issue is likely related to your graphics driver/configuration. Try going to "System > Administration > Hardware Drivers" and see if there are any proprietary graphics drivers listed. If so, try installing them. You may need to run "sudo apt-get update" in terminal (or update the package database through the GUI) before the drivers show up.

if there are no drivers, or they don't work, post your hardware (especially video) specs here.

---

### Post by trevzilla on 2010-05-07
Thank you for the reply!

I went to System->Administration->Hardware Drivers and it found a proprietary driver from Nvidia.  It said that the Driver was already installed and in use.  (This is the driver I installed when I started having the problems.  Before I installed this driver, I had great resolution, however crappy video)

I tried running the command you gave me in Terminal, but nothing new happened.  Still the same problem.

Is there a good way to find out my system specs in Ubuntu, without having to tear apart my computer and physically look inside it?  I have a quite the "Frankencomputer" right now, as it is salvaged from about 4 other computers...

So sorry about being such a noob!

Thanks again!
Trevor

Edit: I just tried removing the proprietary driver, and sure enough, after a reboot, I have a good resolution again.  But once again, any video I try playing is VERY jerky.

---

### Post by dino99 on 2010-05-07
into console:

sudo rm -f /etc/X11/xorg.conf

into synaptic (system admin synaptic) search "nvidia" and remove/purge (right click) all the nvidia packages installed

then install: nvidia-current, nvidia-current-modaliases, nvidia-common, nvidia-settings

reboot

then check "hardware driver" and see if its activated, now you may have full resolution

about the video: install ubuntu-restricted-extras (into synaptic - repo tabs, all the repo need to be activated: main, universe, multiverse, ...)

---

### Post by trevzilla on 2010-05-07
I couldn't find a repo tab in Synaptic.

I ran the install command in terminal and got this error:
install: missing destination file operand after `ubuntu-restricted-extras'
Try `install --help' for more information.

There was no nvidia-current-modaliases.  Only nvidia-185-modaliases (which I enabled)

Other than that I followed all directions.  Now, it seems that I sill have 1024x768 resolution, but no other options whatsoever.  Streaming video is still very jerky.  So much so that it seems like the computer is frozen, except that the sound is still playing fine.  (I've let it buffer...)

Any more ideas?  Or did I do something wrong with those directions?

Thank you!
Trevor

---

