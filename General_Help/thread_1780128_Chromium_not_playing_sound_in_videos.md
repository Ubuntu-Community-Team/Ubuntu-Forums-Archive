---
title: "Chromium not playing sound in videos"
date: 2011-06-11
forum: General Help
---

### Post by ottorecker on 2011-06-11
Chromium is not playing any sounds with video (youtube, etc.)   Sound output on my system is working fine and working fine with firefox embedded videos.  I have uninstalled and installed and tried changing other settings with no resolution......

I am new convert from win to ubuntu and would appreciate any help...

thx.

---

### Post by linuxinstalledfromhdd on 2011-06-11
There are many different plugins you need to install on Ubuntu after a fresh install.. Please review this list and see if there is anything you missed.. 

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

If that doesn't work I would uninstall chrome/chromium and install the PPA repository for chromium and chrome and reinstall it from there.. You can also do that with the above list as well. 

Goodluck.. and welcome to Ubuntu :)

---

### Post by ottorecker on 2011-06-11
thanks for the welcome....and I did go through the list...good advise....so...

uninstalled chromium.  installed chrome... sound works on videos w/chrome...

installed chromium.   no sound with video....this seems very strange to me.  Is there some setting in chromium that I can get to to fix this problem?

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **ottorecker said:**
> thanks for the welcome....and I did go through the list...good advise....so...

uninstalled chromium.  installed chrome... sound works on videos w/chrome...

installed chromium.   no sound with video....this seems very strange to me.  Is there some setting in chromium that I can get to to fix this problem?

In Firefox, please go into Tools >> Add ons >> PLugins and list all the different plugins you have installed on Ubuntu? We will worry about chromium in a minute. :)

Also did you install the Chromium PPA? Uninstall Chromium in Synaptic Package Manager, and right click to select Completely Remove.. And then reinstall Chromium from the PPA. Easy way to do this is use Ubuntu Tweak to add the repository if you don't have it.

---

### Post by ottorecker on 2011-06-11
Firefox and Chrome are functioning fine.  Both play sound with video files.  The add-ons installed in Firefox are (briefly)    	 	 	 	 	Divx, google talk, icetea, quicktime, shockwave, VLC, Windows media player.

I removed (completely) everything I could find that had any reference to chromium in synaptic package manager and then re-installed chromium from the ppa.  Still no sound from video.  I am not sure what else to do.  I have no problems using chrome but it would be nice to find out why I can't get any sound out of the chromium browser.

---

### Post by linuxinstalledfromhdd on 2011-06-12
> **ottorecker said:**
> Firefox and Chrome are functioning fine.  Both play sound with video files.  The add-ons installed in Firefox are (briefly)                            Divx, google talk, icetea, quicktime, shockwave, VLC, Windows media player.

I removed (completely) everything I could find that had any reference to chromium in synaptic package manager and then re-installed chromium from the ppa.  Still no sound from video.  I am not sure what else to do.  I have no problems using chrome but it would be nice to find out why I can't get any sound out of the chromium browser.

Did you install the nightly PPA for Chromium? Maybe there is a update?
```

sudo add-apt-repository ppa:chromium-daily
sudo apt-get update
sudo apt-get upgrade

```
That would be the repository for the latest updated version.

---

### Post by ottorecker on 2011-06-12
OK...I finally got it to work...thank you for your help....

After downloading the latest build and installing it I still had the same problem with no sound from the videos.  I had a package call earcandy installed earlier which I had uninstalled recently so I thought I might try to re-install it to see if that would make a difference.  Initially it did not but when I checked the preferences of the earcandy package there was a setting for output audio that was set to "auto" for the chromium browser.  I set that preference to "internal analog" (something like that) and viola, sound.  This earcandy program initially crossfades audio and seems to have no problem handling the 'auto' audio selection from other packages.  I use my laptop's HDMI output to watch clips on my TeeVee so I do change the audio output often in ubuntu's sound prefs and I really like that the volume doesn't assault you when you pause/start playback using earcandy.  Again, the earcandy prog audio output selection of "auto" doesn't have a problem handling this.  I am not sure who to submit a bug report to.....

I really like this OS and doubt I will ever go back to windows.  I am not sure why I didn't do this earlier (Buying a laptop sans OS was a good motivator) .  There are just a few programs (2 exactly) that I need to run in windows and unfortunately do not run well in Wine.  Next step, virtualbox running xp.  Hopefully it will go smoothly.

Thanks....

---

