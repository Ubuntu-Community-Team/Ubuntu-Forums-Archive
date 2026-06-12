---
title: "Kernel panic after trying to get sound working - HELP!"
date: 2010-02-08
forum: General Help
---

### Post by Donny Bahama on 2010-02-08
Please help!

I'm a noob trying to setup XBMC on top of a bare-bones karmic install. ("[XBMCbuntu]("http://xbmc.org/wiki/?title=XBMCbuntu")") Everything (except sound) was working. 

Getting my (m-audio Transit) USB sound card to be recognized was a chore but I finally got the firmware installed and it listed properly in lsusb. I still had no sound, though (I think there was no default device set) and was trying to figure out how to do that. After installing Pulse Audio and rebooting, I'm now getting:

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

How do I recover from this?

---

### Post by Donny Bahama on 2010-02-08
Let me try to be a bit more explicit... I can display the LILO menu and get a boot prompt, but there's no kind of "safe mode" listed (and I'm not sure what I'd do when I got there.) I could also boot my live CD, but again, what do I do when I get there?

---

### Post by NightwishFan on 2010-02-09
Perhaps a reinstall would be your best option if you are able to backup data. Did you alter any partitions by any chance?

---

### Post by Donny Bahama on 2010-02-09
Thanks for the response. :)

No, no partitions modified. Just tried about a dozen different things to get sound working. 

The sound card I'm using is the M-Audio Transit (USB), which works fine in Windows, but for Linux, you have to jump through some hoops to get firmware on it. Now that I've accomplished that, maybe it'll be properly recognized and supported during the install process. That would certainly be worth the effort. 

This is a pretty fresh install anyway, so it's not like I have a lot invested in it.

Again, thanks for the help.

---

### Post by NightwishFan on 2010-02-09
If the sound fails again I will try to help you.

---

