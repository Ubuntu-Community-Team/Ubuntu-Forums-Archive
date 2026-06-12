---
title: "Lost Sound, Shut Down and Mounting Drives"
date: 2010-08-19
forum: General Help
---

### Post by mozilla2004 on 2010-08-19
I installed Ubuntu 10.04 a few days ago and the system worked perfectly even up until last night.


This morning or late last night, I allowed Ubuntu/Gnome's Update manager to download all the latest packages and install them.


This morning, I noticed several things aren't working:

1) My computer doesn't play sound any more.  The volume icon shows the speaker icon and 3 dashes as opposed to 3 waves, even after I set the volume to maximum.

2) The system no longer automounts my external HDs.  I keep getting messages like "Unable to mount Storage, not authorized"

3) I can't shut down my computer from the task bar.  Everytime I press shut down, it just logs me out and bring me to a login screen.  Restart is also the same.  The only way to shut down the computer is to hold the power button on my desktop for 5 seconds.


How do I begin to resolve all these issues?

---

### Post by sureshsaragadam on 2010-08-19
1. Please check with the /Applications/Sounds and Video/PulseAudio Volume Control options, 
    Check for the the volume, set to un-mute
2. Timely create a new user account and then try login, logoff

---

### Post by mozilla2004 on 2010-08-19
I figured it out.  I installed nVidia video card drivers and that broke my sound system, my ability to mount drives, and my ability to shut down the computer.

I disabled the nVidia drivers by going to System > Administration > Hardware drivers

Now everything works properly again.

---

