---
title: "major issues: installing ATI 4650 w/ 10.10 stuck at prompt or.."
date: 2010-12-05
forum: General Help
---

### Post by Sxynerd on 2010-12-05
I just tried installing my new ATI HD 4650.  And now it's all stuck.

I have an HP A6600F with integrated Nvidia.  Jumping back and forth I went into Ubuntu and downloaded the current and correct driver for the ATI card.  I opened it, ran it in the Terminal, restarted, disabled onboard integrated graphics, moved the cable over to the new card.  At this point I get stuck at Prompt non GUI.

It's like I am in Terminal.

I then tried to go back to my integrated video card and I get the mouse & cursor with no other video display.  My only guess is drivers are conflicting and not allowing me into the full functioning GUI. 

Please help

---

### Post by Sxynerd on 2010-12-05
Code:
> sudo Xorg -configure
sudo mv xorg.conf.new /etc/X11/xorg.conf
sudo reboot

IDK how but this got me out of Command Prompt and back into avery basic GUI.  My cursor is doing the "Microsoft thinking" spinning thing.

I have no idea what to do next or even if this is permanent.  Should I risk restarting?

---

### Post by sikander3786 on 2010-12-05
Didn't you reboot after completion of driver installation?

I would suggest to reboot. Enable your ATI graphics card, plug the display to that one and power-on. And if it takes you to the terminal thing (tty) this time, try reconfiguring your graphics by,

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

```
sudo shutdown -r now
```

Lets see what happens then.

---

### Post by Sxynerd on 2010-12-05
> **sikander3786 said:**
> Didn't you reboot after completion of driver installation?

I would suggest to reboot. Enable your ATI graphics card, plug the display to that one and power-on. And if it takes you to the terminal thing (tty) this time, try reconfiguring your graphics by,

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

```
sudo shutdown -r now
```

Lets see what happens then.

I tried what you said but when it restarted it still kept me  in the same generic GUI.  

Everytime I go to install the ATI drivers it locks me in that "Command Prompt" screen.

I have just noticed that under "Additional Drivers", "ATI Fire GL" is active.  That is different from before.

Right now I have no control over the video card and all my border panels are really generic looking.  I also can not minimize any windows because they disappear.  If this were "Windows" I would compare it to "safe mode".

Nvidia is the onboard video card that I disabled through BIOS.  I have also tried "mark for complete removal" every Nvidia entry I could find through "Synaptic"

I also can not access any files or folders in my system.

---

### Post by sikander3786 on 2010-12-05
Remove the Nvidia drivers.

Remove the ATI drivers.

Remove xorg.conf.

Reboot and re-install ATI drivers.

```
sudo apt-get remove --purge nvidia-current nvidia-common nvidia-settings
```

```
sudo apt-get remove --purge fglrx fglrx-amdcccle
```

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.old
```

```
sudo shutdown -r now
```

Then go to System > Administration > Additional Divers and activate the drivers.

---

### Post by Sxynerd on 2010-12-05
> **sikander3786 said:**
> 

Then go to System > Administration > Additional Divers and activate the drivers.


I did everything you said and it seems to be kinda back to normal but the "Aditional Divers" is not in the menu where it was previously.  I can't find it to do the last step.

...hold that thought...  Somehow it got uninstalled.  I am reinstalling it now.

---

### Post by Sxynerd on 2010-12-05
You are a life saver.  Thank you.  I needed to upgrade my card so I could edit a video for my semester project.  :)  You just helped me get my "A."


The next time I do a fresh install of Ubuntu I shouldn't need to mess with any of the Nvidia stuff again because it wont ever be re-initialized, right?

If there is a fresh install of Ubuntu, would I be able to just directly update the driver from the ATI site or from Synaptic?  .or is there a specific step I would have to do in order to get the drivers to work?

I am asking all of these questions to I can mark the thread as solved, consolidate all the great info you gave me and edit it into the first post for myself and others that may need the info in the future.

Thanks Again.

---

### Post by sikander3786 on 2010-12-05
You are Welcome. Glad to know it worked for you :-)

The simple answer to your question is that before installing Nvidia drivers, remove ATI drivers (if present) and vice versa. And also remove the xorg.conf manually if not removed automatically ;-)

Whenever you plan to re-install, just don't install the Nvidia drivers. Plug your display to ATI and install ATI drivers from jockey-gtk i.e, Additional Drivers. No need to go to Synaptic or some other package manager.

Hope it is all answered :-)

---

