---
title: "No sound card after starting x"
date: 2009-11-01
forum: General Help
---

### Post by chocolatetoothpaste on 2009-11-01
I installed a command-line 9.10 system, installed openbox and a handful of other lightweight tools.  Well, if I log in to just a terminal and run 'aplay -l' it shows I have a sound card.  I can run alsamixer and see all my devices.  But, as soon as I run 'startx' and my openbox session loads, aplay -l says I have no sound card device.  I've tried to modprobe the drive, and a few other things, but I can't seem to get anything to happen.  Any help would be awesome.  Thanks!

---

### Post by chocolatetoothpaste on 2009-11-03
So, I figured out what's going on, I think.  After I start my openbox session, I have to put sudo in front of aplay.  If I do that, I see my devices, as well as sudo alsamixer gives me my audio mixer.  I'm not sure why I need to do sudo, if I just log in to my command line, I can do these commands as a normal user.  Before I go changing permissions, I'd like to know if anyone knows what the deal is with this and if it's something I need to "fix".  TIA

---

### Post by florentin on 2010-01-28
Please see the solution here
[http://ubuntuforums.org/showthread.php?p=8488044](http://ubuntuforums.org/showthread.php?p=8488044)

You need to run this:
sudo adduser <username> audio
then **restart your computer**.

---

