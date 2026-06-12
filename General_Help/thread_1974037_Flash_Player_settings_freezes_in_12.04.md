---
title: "Flash Player settings freezes in 12.04"
date: 2012-05-05
forum: General Help
---

### Post by linuxuser12345 on 2012-05-05
Hey, I'm using Ubuntu 12.04 x64 bit edition on several computers, and ALL are experiencing the same, annoying problem: When using Flash Player, and if I go to the Flash Player settings in the web browser window, the Flash box will become unresponsive to my actions. This makes it so I cannot exit out of the settings and I can't change any settings, which gets very frustrating. This also means that I cannot use my webcam or microphone in my web browser, so then I have to resort to using Windows... again. I tried using Firefox, Google Chrome, and Chromium. All experience the same problem.

This needs to be fixed! Has anyone found a workaround or fix?

---

### Post by JRV on 2012-05-05
Since today's updates I get no sound on flash and faces are blue.

---

### Post by AndrewWalker on 2012-05-05
I get told flash needs upgrading even though I'm up to date and nothing flash works at all.


Flash must die and the sooner the later!

---

### Post by soryu on 2012-05-05
same thing here i guess we just have to deal with it.:twisted:
on the bright side flash finally plays smoothly like in windows even HD,except in fullscreen

---

### Post by ub-newbie on 2012-05-05
05-05-12
OS: 10.04 64bit
Flash version: 11.2.202.233
Video: NVIDIA GeForce 8300 using VDPAU w/driver 195.36.24

"Adobe-flash plugin" installed via Synaptic.

Problems:  "Smurfs" & stuttering audio

Solution to "Smurfs": 
(from [http://askubuntu.com/a/131040]("http://askubuntu.com/a/131040://") with credit to Daniel Mario Vega on Launchpad)
```
cd /usr/lib/adobe-flashplugin
	sudo perl -pi.bak -e 's/libvdpau/lixvdpau/g' libflashplayer.so
```

This got rid of the Smurfs, but audio problem continues

---

### Post by claracc on 2012-05-06
The "flash" problem with ubuntu is discussed in this thread: [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

There are some workarounds you can try ( indicated in the thread) as downgrading flash.

---

### Post by linuxuser12345 on 2012-05-06
I am still getting the same problem. I submitted a bug report here:
[https://bugs.launchpad.net/arora/+bug/995699](https://bugs.launchpad.net/arora/+bug/995699)

---

### Post by mteppo on 2012-09-30
> **ub-newbie said:**
> 05-05-12
OS: 10.04 64bit
Flash version: 11.2.202.233
Video: NVIDIA GeForce 8300 using VDPAU w/driver 195.36.24

"Adobe-flash plugin" installed via Synaptic.

Problems:  "Smurfs" & stuttering audio

Solution to "Smurfs": 
(from [http://askubuntu.com/a/131040]("http://askubuntu.com/a/131040://") with credit to Daniel Mario Vega on Launchpad)
```
cd /usr/lib/adobe-flashplugin
	sudo perl -pi.bak -e 's/libvdpau/lixvdpau/g' libflashplayer.so
```

This got rid of the Smurfs, but audio problem continues
I was also experiencing "smurfs" in youtube - having NVidia 8500 GPU I was not able to turn on HW acceleration to get rid of this as this caused frequent crashes with other sites, namely and especially with Yle Areena ( [http://yle.fi/areena](http://yle.fi/areena) )
And as the Settings panel is frozen with my 12.04 Ubuntu's flash player (cannot untick the HW acceleration from there either) I stumbled onto this thread. The askubuntu linked article did not work anymore so cannot know what was discussed there :-(

For 12.04 the installation directory seems to have changed.
What I did was as follows:
First checking where this file is:
```

$ locate libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so

```
So the libflashplayer is now there, lets go there as well:
```

$ cd /usr/lib/flashplugin-installer

```
Making a back up never hurts - so backing up the file before changing it
```

$ sudo cp libflashplayer.so libflashplayer.so.bak
$ sudo perl -pi.bak -e 's/libvdpau/lixvdpau/g' libflashplayer.so

```

Now - this did it for me. YMMV. If it does not work you should be able to revert the changes by returning to the backup file (if you made one) or uninstalling / installing the flash.

```

$ sudo cp libflashplayer.so.bak libflashplayer.so

```

Thanks to UB - newbie on this - hopefully now I can enjoy all web video content without griefs of the flash player.

---

