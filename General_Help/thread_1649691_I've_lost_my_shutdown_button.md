---
title: "I've lost my shutdown button"
date: 2010-12-20
forum: General Help
---

### Post by onaridge on 2010-12-20
I've lost my shutdown button. I think it disappeared after an update of which there were quite a few lately. I have been using ctrl Alt Del. Is that safe to use? How do I get that button back?

---

### Post by j388m on 2010-12-20
You could add another type of shutdown button.  Right-click on the bar and select Add to Panel... browse for the shutdown panel.

This sometimes happens to me.  Although, it appears every few days... Strange!

---

### Post by MooPi on 2010-12-20
Lets check to see if you can shut down by other means. In terminal try ```
gksudo 'shutdown -r now'
``` This should reboot your computer and show that shutdown is working correctly.

---

### Post by Putnam11 on 2010-12-20
You could reset the toolbars if you haven't made any changes you don't want to go through again.
In terminal:```
gconftool-2 --shutdown
rm -rf~/.gconf/apps/panel
pkill gnome-panel
```
After you enter those lines into terminal, the panels should disappear for a few seconds then come back with their default settings.  Hope this helps!

---

### Post by efflandt on 2010-12-20
There was a space missing after -rf in that line, should be:
[FONT=monospace]
[/FONT]```
rm -rf ~/.gconf/apps/panel
```

---

### Post by MooPi on 2010-12-20
This should correct the issue. In terminal again, 
```
sudo apt-get install indicator-applet-session
```
Then right click on the upper toolbar and select Add to Panel> Choose indicator applet session.

---

### Post by onaridge on 2010-12-20
Tried adding the button but that is just a shortcut to the ctrl alt del method. Tried the sudo apt-get and got this: "indicator-applet-session is already the newest version"

Don't want to reset my panel as there is a lot of stuff in it.

So ctrl alt del isn't a good idea?

---

### Post by MooPi on 2010-12-20
Is the indicator applet available for the panel if you right click and Add to Panel?

---

### Post by ventrical on 2010-12-20
> **onaridge said:**
> Tried adding the button but that is just a shortcut to the ctrl alt del method. Tried the sudo apt-get and got this: "indicator-applet-session is already the newest version"

Don't want to reset my panel as there is a lot of stuff in it.

So ctrl alt del isn't a good idea?

Yep... Mine has been going off and on  using Maveric Meerkat but works great with 10.04.

  I used install from menu and started another thread for now. Looks like a bug or somthing.

---

### Post by ventrical on 2010-12-20
other thread here
[http://ubuntuforums.org/showthread.php?p=10262154#post10262154](http://ubuntuforums.org/showthread.php?p=10262154#post10262154)

---

### Post by onaridge on 2010-12-20
Moopi yes but it doesn't work the same way.

---

### Post by ventrical on 2010-12-21
Today I got this.

---

### Post by onaridge on 2010-12-21
and I just realized I have now lost my desktops on the panel. I don't see anything in the "add to" for the panel. How do I get these back?

---

### Post by ventrical on 2010-12-22
All is back to normal here. Reboot seems to  fix the prob. I hope the devs pick up on this. It doesn't happene to me with10.04. Only 10.10.

---

### Post by onaridge on 2010-12-22
Yes my workspaces came back with reboot but not the shutdown and I have 10.04 on this computer. Also the reboot removed my ability to use CTRl ALT Backspace to shut down.

---

### Post by QLee on 2010-12-22
[QUOTE=onaridge]Yes my workspaces came back with reboot but not the shutdown and I have 10.04 on this computer. Also the reboot removed my ability to use CTRl ALT Backspace to shut down.[/QUOTE]

Well, the key combination CTRl + ALT + Backspace, never did trigger a shutdown sequence, it used to kill the X server (essentially, log you off the GNOME session) but that functionality was taken out several releases back.

What happens when you just push and quickly release the power button (don't hold it ), does that initiate a shutdown dialogue?

---

### Post by SD_Korf on 2010-12-22
I've had a similar problem on 10.04 and 10.10. In my case nothing disappeared but they were shuffled around. Right now I've got my network icon on the far right, where the shutdown icon used to be. Unfortunately I can't remember the preceding steps when these situations happened. It has happened in both VMs and on my laptop.

I believe it is a bug. In the meantime, however, I'd love to know how to get things back to where they were. I'll try the "killall gnome-panel" at some stage.

Edit: Just remembered, the shifting happened when the screen was resized. Once when I attached an external monitor, the other time when resizing the window of the VM (I think). I also hit the "switch monitor" button (Fn+F4) on my laptop which sent the poor thing into a frenzy because not external monitor was attached. After that the buttons were messed up.

Oh, and onaridge, Ctrl+Alt+Del should not be a problem to shutdown. No worries there.

---

### Post by onaridge on 2010-12-23
Qlee yes it initiates a shutdown.

SD, I guess I will just use CTRL ALT DEL then to shutdown.

---

### Post by SD_Korf on 2010-12-24
'killall' didn't solve my panel problem.

Found this: [http://ubuntuforums.org/showthread.php?t=1295804](http://ubuntuforums.org/showthread.php?t=1295804)

Basically it refers to bug: [https://bugs.launchpad.net/gnome-panel/+bug/44082](https://bugs.launchpad.net/gnome-panel/+bug/44082)
which has been around since 2006. (onaridge - I think the workaround they give will allow you to save your customisations.)

I now want to try this: [http://www.starryhope.com/linux/ubuntu/2010/restore-the-default-panels-in-ubuntu/](http://www.starryhope.com/linux/ubuntu/2010/restore-the-default-panels-in-ubuntu/)

Later...

---

### Post by QLee on 2010-12-24
> **onaridge said:**
> Qlee yes it initiates a shutdown.

SD, I guess I will just use CTRL ALT DEL then to shutdown.

OK, so we know shutdown is functioning properly on your system.

Can you try a right click on the panel and choose Add to Panel, then go down the list and find a button called, Shut Down, it will be a button just for shutdown, the one I like is red but its look will depend on the icon set your theme uses. If you find that button in the Add to Panel list, try adding it to the panel and see if it works or see if there is some error message dropped.

---

