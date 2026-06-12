---
title: "LiveCD works better than installing?"
date: 2009-07-09
forum: General Help
---

### Post by stowercraft on 2009-07-09
I'm in a pickle.

So...when booting up a LiveCD, HD flash video in fullscreen plays smoothly.  Everything in a LiveCD environment seems fine and dandy.

Now...after installing onto the hard drive and booting up, HD flash videos in fullscreen play extremely choppy...extremely unlike the portrayal by the LiveCD.

I've compared both xorg.conf files of the LiveCD environment and the local installation and both are identical.

What other factors are there that make the LiveCD better than the local installation?  The graphics card in question is an Intel 945GM in a notebook computer.  If the xorg.conf files are identical, what modules can you think of that would separate the two, performance-wise?

So what are these developers slipping into the LiveCD by default that they are leaving out from the installation by default?


Any takers?

---

### Post by caco on 2009-07-09
What is your system's memory size? What sort of hard disks are in your box? My guess is since everything runs from RAM when using livecd against when installed...

[[IMG]http://brainstorm.ubuntu.com/idea/20470/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/20470/)

---

### Post by stowercraft on 2009-07-09
Intel Core2 T7200 (2.0GHz)
2GB RAM
120GB SATA HDD (standard 5400RPM 2.5" notebook HDD)

---

### Post by JoeSef-IL on 2009-07-09
I Think that is better to install it because it will be much more fast!
 
(Due your PC info.)

---

### Post by danwood76 on 2009-07-09
There are differences between the install and the live cd.
The live cd is setup so that it will work with the maximum amount of hardware in the best possible way.

Since you are using an intel graphics card there are some things you can try.
This thread has a good guide to getting a solid intel setup:
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

Try and follow the safe configuration first.
The issues you are having are probably due to certain people experiance problems with the intel drivers and some stuff was disabled.

---

### Post by stowercraft on 2009-07-09
Hmm....so there's no easy way (analogous to a diff) to figure out which modules are being loaded with LiveCD that aren't in a default installation?  

Would it not be wise to load up a LiveCD and copy its root directory and override the local installation's root directory in order to maintain those LiveCD configs & modules that allow flash to work so well?

---

### Post by stowercraft on 2009-07-09
Well actually, just typing up that post, I figure that I might as well run an lsmod on the LiveCD and then compare it to an lsmod in the installation and see if any missing modules appear to fix the problem.

Now for different configuration files (aside from the xorg.conf which has been confirmed identical between the two), anyone have any suggestions as to which configuration files i should compare between the two?

---

### Post by danwood76 on 2009-07-09
Its not that different modules are being loaded but a different version of the driver.

Have you installed all the updates?
Follow that guide, it should sort your problems out.

---

### Post by danwood76 on 2009-07-09
Please see the release notes also:
[http://www.ubuntu.com/getubuntu/releasenotes/904#Performance%20regressions%20on%20Intel%20graphics%20cards](http://www.ubuntu.com/getubuntu/releasenotes/904#Performance%20regressions%20on%20Intel%20graphics%20cards)

---

### Post by happyponcho42 on 2009-07-11
Alright now, this should be stickied for everyone else who has the Intel 945GM that experiences problems with full screen flash video playing choppily.

I ran a diff on the entire filesystem of the LiveDVD and compared it to a local installation to figure out why the LiveDVD is able to play the fullscreen HD flash videos flawlessly, yet the local installations are unable to do the same.  I found the following:

> 
diff /mnt/oldroot/etc/csh.env /etc/csh.env
21a22
> setenv LIBGL_DRIVERS_PATH '/usr/lib64/dri:/usr/lib32/dri'


So...the solution is to edit your /etc/csh.cshrc file and add
```
setenv LIBGL_DRIVERS_PATH '/usr/lib64/dri:/usr/lib32/dri'
```
...then reboot and go ahead and test out some HD flash videos on hulu.

---

### Post by danwood76 on 2009-07-11
If you had read the thread I poseted you would have read the reason that the dri was disabled and the proper way to run it.

---

