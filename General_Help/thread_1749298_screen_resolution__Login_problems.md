---
title: "screen resolution / Login problems"
date: 2011-05-04
forum: General Help
---

### Post by Mushu84 on 2011-05-04
After a lot of headache and time I was finally able to get Ubuntu 11.04 64bit installed along side my Windows 7 64bit installation.  The whole process was hindered by the screen resolution being really off, looked like this [LINK]("http://a.yfrog.com/img620/9272/ecwkz.jpg") (aspect ratio of (16:10) I believe it was).  After much fiddling i was able to get the installation started hoping that in the end it would let me set the res. correctly once it was installed.  About 75% of the way done it threw an error saying there was either a problem with the HDD or the CD, I know my HDD is fine, so I booted up windows and set up my USB thumb drive as the installation device, Unbootable.

My next attempt i hooked the laptop to my internet via cable and started the installation again, this time i found that I could set the res of the LiveCD(which was a pain in the neck! lol) and this time Ubuntu installed and upgraded and seemed all sorts of happy!

Once the PC rebooted and i selected to boot into Ubuntu, the(what i suppose is) login screen pops up but the resolution is messed up again and this time I can't navigate at all.  I've tried just typing in my password and hitting enter as i can see that it is by default selecting my user name to login with.

Any help would be amazing, I really would like to learn another OS and expand upon my knowledge of computers!

---

### Post by Mushu84 on 2011-05-04
So after speaking with a co-worker about this issue, he suggested that I boot into the terminal(ctrl+alt+f1) and follow the steps below.

use the command xrandr
without parameters it gives you the supported resolutions, and you can set the resolution using:

xrandr -s <resolution index from the resolutions list>
or
xrandr -s <x_res>*<y_res>

Any thoughts?  I'm gonna give it a try after work.

---

### Post by Mushu84 on 2011-05-09
Installation issue has been resolved by formating the partition using Win7 and reinstalling with the Live CD.  New issue with Disk usage:  [http://ubuntuforums.org/showthread.php?t=1754318](http://ubuntuforums.org/showthread.php?t=1754318)

---

