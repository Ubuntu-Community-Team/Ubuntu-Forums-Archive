---
title: "Ubuntu won't load once grub selects it, fresh install doesn't help"
date: 2011-10-27
forum: General Help
---

### Post by razaz03 on 2011-10-27
See Title. 

I posted it yesterday when it happened [http://ubuntuforums.org/showthread.php?t=1870195](http://ubuntuforums.org/showthread.php?t=1870195) here and was told to reinstall, albeit one must've assumed this crash occured due to a tweak (seems unlikely in hindsight). This was with Ubuntu 11.10 (fresh install) and it is happening again with a fresh install of Xubuntu, which I fled to.

md5 checked on both downloads with a different usb used each time. quad core q6600 and 4gb ram nvidia 560 ti gpu asus p5k deluxe mobo. All the above components tested under Windows.

Didn't tweak Xubuntu at all, installed dropbox and that's all! Both distros lasted for maximum of one day; cursor still hangs and perpetually blinks after I select Ubuntu kernal from Grub, please help!

---

### Post by drs305 on 2011-10-27
If the flashing cursor appears 30-60 seconds after the Grub menu it could be a video driver problem.

One way to check is to add a kernel option to the boot commands. At the Grub menu, press 'e' to edit the highlighted menu entry. If the Grub menu doesn't appear during boot, hold down the SHIFT key during boot until it appears.

After pressing 'e', use the cursor to go to the end of the 'Linux' line. Remove 'quiet splash' and add 'nomodeset'. Press CTRL-x to boot.

If it boots to the Desktop, you will need to add the Nvidia driver. Press the DASH/Home button and type 'Additional' and then select 'Additional Drivers'. See if an Nvidia driver is available and if so, install it.

---

### Post by razaz03 on 2011-10-27
> **drs305 said:**
> If the flashing cursor appears 30-60 seconds after the Grub menu it could be a video driver problem.

One way to check is to add a kernel option to the boot commands. At the Grub menu, press 'e' to edit the highlighted menu entry. If the Grub menu doesn't appear during boot, hold down the SHIFT key during boot until it appears.

After pressing 'e', use the cursor to go to the end of the 'Linux' line. Remove 'quiet splash' and add 'nomodeset'. Press CTRL-x to boot.

If it boots to the Desktop, you will need to add the Nvidia driver. Press the DASH/Home button and type 'Additional' and then select 'Additional Drivers'. See if an Nvidia driver is available and if so, install it.

It booted!! Many thanks!

However installing the additional nvidia drivers was the first thing I did. I Installed the first one (version current) then the second with a (post-release updates) (version current - updates) brackets attached. The second one is active, both say they've been tested by Ubuntu developers, yet the first one (inactive one) has a [recommended] sign.

Should I revert to the first [recommended] one? Should I change back the settings in Grub after? How on earth would I have found that out in the first place? If there is a graphical problem, how is it loaded now after following your instructions, and is there any third party tool I can install that downloads the additional (graphics included) drivers for me? As I wouldn't want a powerful gpu without taking advantage of it in this OS.

Sorry for bombarding but I would be most grateful if anyone could help this newbie out with all of the above.

Thanks!

---

### Post by drs305 on 2011-10-27
Well, you know how to alter the menuentry if the driver you are currently using doesn't work. ;-)

There was a time a few years ago where I had to occasionally switch between an older Nvidia driver and the (then) latest one. It seemed the absolutely latest driver was always 'too advanced' for my modest card, and it would take a while for it to get tweaked enough for me to use.

I short, use the driver that works, and it may not be the newest. And note when there are updates - to either try a newer one again or to be ready to revert to the older one.

The 'nomodeset' fix worked as it tells the kernel not to load a lot of the modules that are normally loaded. If you have a bad or missing video driver, the system will boot with basic video capabilities and you are able to see the screen.

Beside the 'nomodeset' menuentry method, since you will know the video driver that works you could also boot the recovery mode to a root prompt. There you could use commands to purge a driver and install one you know works. I prefer the 'nomodeset' option but the other way can work as well.

---

### Post by razaz03 on 2011-10-27
> **drs305 said:**
> Well, you know how to alter the menuentry if the driver you are currently using doesn't work. ;-)

There was a time a few years ago where I had to occasionally switch between an older Nvidia driver and the (then) latest one. It seemed the absolutely latest driver was always 'too advanced' for my modest card, and it would take a while for it to get tweaked enough for me to use.

I short, use the driver that works, and it may not be the newest. And note when there are updates - to either try a newer one again or to be ready to revert to the older one.

The 'nomodeset' fix worked as it tells the kernel not to load a lot of the modules that are normally loaded. If you have a bad or missing video driver, the system will boot with basic video capabilities and you are able to see the screen.

Beside the 'nomodeset' menuentry method, since you will know the video driver that works you could also boot the recovery mode to a root prompt. There you could use commands to purge a driver and install one you know works. I prefer the 'nomodeset' option but the other way can work as well.

I certainly do now, although it wasn't as clear cut as that as it booted several times before sporadically dying, hence driver didn't immediately come to mind, but many thanks nonetheless [IMG]http://ubuntuforums.org/images/icons/icon10.gif[/IMG]. I think as a linux newbie this method suited me fine, if only I had discovered it sooner!

Thanks again, marking as solved.

raz

---

