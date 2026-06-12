---
title: "Videos not displaying properly"
date: 2011-03-29
forum: General Help
---

### Post by Kilron on 2011-03-29
Ok, I've had Xubuntu for a few weeks now and was going to watch a video I had on my hard drive, but whenever I play anything, it looks weird.  It plays correctly otherwise, but there is a bunch of garbage over the picture.  I included two screenshots taken in Movie Player, first was taken with the regular screenshot button, the second was taken using Movie Player's screenshot function.  As you can see in them, Movie Player takes a screenshot correctly for some reason.  I have tried in both VLC and Movie Player, and both MP4 and FLV format on both, nothing changes.  I have no idea what causes this, because watching Youtube videos works perfectly fine.

I use an ATI Radeon 9200 with the open source drivers (as no others are available for my card unfortunately :/), and while I have had some problems with certain games, Compiz works pretty well.  Is there some codec I might need to install?  Because I already added the Medibuntu repository and installed the restricted extras.

---

### Post by Kirboosy on 2011-03-29
Hi! I'm not 100% sure this will fix your issues but its worth a shot...

[QUOTE=Jason_25]Ctrl-alt-f1, login

     Code:
     sudo dpkg-reconfigure xserver-xorg 
Choose appropriate settings, when you get to the driver section, choose vesa.  Once you exit that, type:
     Code:
     sudo /etc/init.d/gdm restart 
I guarantee this will get you going.[/QUOTE]

Taken from [this thread]("http://ubuntuforums.org/showthread.php?t=163989")

If the problem persist I would remove the open-source drivers, reboot, and reinstall...


~Caboose

---

### Post by Kilron on 2011-03-29
When I typed in the reconfigure code, it didn't do anything. :-?

EDIT: I guess this method does not work with anything newer than Gusty, according to what I read here: [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)

---

### Post by Kirboosy on 2011-03-29
Well I honestly have no idea what it could be besides a driver issue at this point. Google isn't helping much either...

Sorry I can't be of more help. :(

---

### Post by Kilron on 2011-03-29
Well, I can still try reinstalling.  How do I go about doing that?

---

### Post by Kirboosy on 2011-03-29
Well I'm not sure where it is exactly in Xubuntu but you need to go under your Administration section and select "Additional Drivers" and then select deactivate for the driver. It should do its thing then...Then reboot and reinstall it. 


Hopefully that fixes it. I take it you are running Xubuntu 10.10?

---

### Post by Kilron on 2011-03-29
Yes, I am running 10.10.  However, when I go to System>Hardware Drivers, it gives me the "no propietary drivers are in use" message.  There is no Additional Drivers option as far as I can tell.

---

### Post by SeijiSensei on 2011-03-29
Try installing **smplayer** from the repositories and see if that works better.

---

### Post by Kirboosy on 2011-03-29
How did you install the drivers before then?

---

### Post by Kilron on 2011-03-29
Nope, that doesn't work either. :(

> How did you install the drivers before then?

My mistake, I assumed open source drivers was referring to the ones included with Xubuntu.  That's the ones I am using, because ati dropped support for this card some time ago, leaving me with nothing else to use.

---

### Post by Kirboosy on 2011-03-29
Maybe [these drivers]("http://support.amd.com/us/gpudownload/Pages/linux64-radeon-prer200.aspx") will be able to be installed and fix the issue? (those are 32 bit [64 bit can be found here]("http://support.amd.com/us/gpudownload/Pages/linux64-radeon-prer200.aspx"))

Hopefully Ubuntu lets you install even if they are old.

---

### Post by Kilron on 2011-03-29
When I tried to run the .run file, I got this:

```
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: unable to detect
Removing temporary directory: fglrx-install
```

---

### Post by Kirboosy on 2011-03-29
The x-server might be to new for that old driver...:(

Try opening Synaptic Package manger and type 'Radeon' in the quick search box...

Mark the following for reinstall...

xserver-xorg-video-radeon
xserver-xorg-video-ati


I'm not sure but if that doesnt fix it you may wanna try installing the "fglrx" package...I would reboot and everything first to make sure it did/didnot work.


~Caboose

---

### Post by Kilron on 2011-03-30
Yeah, according to what I've read, I'd have to roll back pretty far to use that driver.

Unfortunately, I already tried to install fglrx before, and it did not work.  The only other driver I can use is the Open Source Edge Driver, from here:

[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")

That one is actually the one I've been using, not the default open source driver that comes installed (again, my mistake, I had forgotten I had added that repository).  In fact, aside from Compiz, I can't say I noticed a huge differemce in overall performance, so I've thought of removing it and seeing if going back to the default drivers fixes the video.

EDIT: I seem to have fixed it, in VLC at least.  I change the output from default to X11, and it works.  Sorry to put you through all that trouble.

---

### Post by Kirboosy on 2011-03-30
Sweet. I'm glad you got it working. :) 

I didn't even think about changing the VLC settings. (On my computer I can only play videos in VLC because Totem and mplayer throw I/O errors. Also I like VLC the best since its so efficient.)

---

### Post by Kilron on 2011-03-30
Weird, I have no problems with SMplayer.  In fact, it runs even better than VLC.  Props definitely go to SeijiSensei for recommending it.

---

### Post by SeijiSensei on 2011-03-30
You're welcome.  I only wish that some enterprising distro packager would make smplayer the default media player.  That would probably ruffle some feathers over at the GNOME project, though, and we certainly can't have that, can we?

---

