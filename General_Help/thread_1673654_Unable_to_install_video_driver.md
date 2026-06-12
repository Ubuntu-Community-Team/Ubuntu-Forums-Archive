---
title: "Unable to install video driver"
date: 2011-01-22
forum: General Help
---

### Post by kulturloseramerikaner on 2011-01-22
Ok, I had my system running and triple-booting nice and smooth about 2 weeks ago, then experienced a HDD failure on the drive with Ubuntu. I got the new drive in, and reinstalled, but time around I'm unable to get the video driver installed.

I used the wiki [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide) to install it the first time. It worked a month ago when I upgraded my video card, and the instructions say that you need to have the lib32's all installed for the Catalyst driver to work, but now it's giving me this:

hirnrissigermann@HAL:~$ sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
ia32-libs: Depends: lib32gcc1 but it is not going to be installed
Depends: libc6-i386 (>= 2.3.6-2) but it is not going to be installed
Depends: lib32z1 but it is not going to be installed
Depends: lib32stdc++6 but it is not going to be installed
Depends: lib32asound2 but it is not going to be installed
Depends: lib32bz2-1.0 but it is not going to be installed
Depends: lib32ncurses5 but it is not going to be installed
Depends: lib32v4l-0 but it is not going to be installed
E: Broken packages

I tried to install each individually, and have had no luck. I just want to get my system as close as possible to the state it was in 2 weeks ago before the drive failure; where I should I go from here?

OK, update:

I had synaptic set to got only to the repos at the University of Chicago because that gave me the lowest ping, but these packages are apparently no longer there. I went back into Synaptic, set my repo server back to "US" and reloaded. Running sudo apt-get install ubuntu-restricted-extras on is installing those packages right now. :)

Update to the update:

Ubuntu found the driver on its own this time, and installed automatically. All is well.

---

