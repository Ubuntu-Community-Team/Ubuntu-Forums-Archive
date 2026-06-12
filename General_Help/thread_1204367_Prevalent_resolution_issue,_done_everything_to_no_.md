---
title: "Prevalent resolution issue, done everything to no avail!"
date: 2009-07-04
forum: General Help
---

### Post by phait on 2009-07-04
I'm setting up my grammas comp with Xubuntu, latest alternate install (the reg. install would hang to black screen after awhile, I did some searching and alternate/txt install was suggested -- worked great).

The comp has 192 MB RAM and either a 2MB or 4 MB Trident 9680 card. I don't know if it's PCI or ISA but the tower is old... although it does have USB 1 ports.

Anyway, Xubuntu runs fine but the resolution is 640 x 480 or so. When I go to change it, I can go to 400 x 300, 320 x 240 or something - that's it.

Now, I already searched the forums extensively and viewed threads and solutions to the same problem. I've done every command suggested, I've customized xorg.conf (which btw has nothing listed in it as far as specific hardware models -- this tells me Xubuntu isn't reading/recognising the card model/brand one bit)... I'm so frustrated. I've spent 22 hours awake on this the other day, and since getting Xubuntu installed, a few more hours today.

SO I guess I am left burning a 4th distro (the other 3 CDs are of no use for me personally)? Like what? I tried gOS but not the alternate install... frankly if anything is from Ubuntu I'm afraid I'll have the same problems.

---

### Post by overdrank on 2009-07-04
Hi and welcome, I do not have much experience with the Trident graphics, but you may try when booting into recovery mode and use the xfix option to help with graphical issues.
If xubuntu is the only os then you can press the esc key when the grub is loading and select recovery mode. Then you should be given 4 options and the last is xfix, when xfix is complete then you should be given the choice to boot normally.
I have seen the the past that users had luck with Hardy 8.04 as it had a tool ```
gksu diplayconfig-gtk
``` but I must confess it has been awhile since I have used xfce.

---

### Post by phait on 2009-07-05
Hi thanks. I can try that howerver I read displayconfig-gtk was removed (to many others frustration), which explins why when I've used it, it just hangs the system. And apparently it's not available to install.

---

### Post by phait on 2009-07-05
Bump. Sorry, just hoping to get this resolved within a few days to get my comp back to gram. I appreciate the help. Meanwhile any suggestions about displayconfig-gtk would be appreciated.

---

### Post by CatKiller on 2009-07-05
> **phait said:**
> I've customized xorg.conf (which btw has nothing listed in it as far as specific hardware models -- this tells me Xubuntu isn't reading/recognising the card model/brand one bit)

No, it just means that you're running a newish version. There isn't much in a default xorg.conf these days. While you can still put stuff in there for manual configuration, mostly it's automatically handled.

Some more details might be useful, such as which version you're running, what monitor you're using, that kind of thing.

---

### Post by Zimmer on 2009-07-05
> **phait said:**
> 

The comp has 192 MB RAM and either a 2MB or 4 MB Trident 9680 card. I don't know if it's PCI or ISA but the tower is old... although it does have USB 1 ports.

Anyway, Xubuntu runs fine but the resolution is 640 x 480 or so. When I go to change it, I can go to 400 x 300, 320 x 240 or something - that's it.

Now, I already searched the forums extensively and viewed threads and solutions to the same problem. I've done every command suggested, I've customized xorg.conf (which btw has nothing listed in it as far as specific hardware models -- this tells me Xubuntu isn't reading/recognising the card model/brand one bit)..
...
What does the xorg.log tell you is going on??? 

and..
[http://www.xfree86.org/4.3.0/Status34.html](http://www.xfree86.org/4.3.0/Status34.html)

is your card mentioned here?

The 'trident ' driver may be what you are looking for...

---

### Post by phait on 2009-07-05
CatKiller, Xubuntu 8.04.1 Hardy Heron

Monitor is a 15" Samsung Syncmaster 512N LCD, max res 1024 x 768 (although that's my monitor, my gram has a 15" CRT).

Zimmer, thanks I'll get back to ya in a few hrs.

---

### Post by CatKiller on 2009-07-05
> **phait said:**
> Monitor is a 15" Samsung Syncmaster 512N LCD, max res 1024 x 768 (although that's my monitor, my gram has a 15" CRT).

Normally, resolution problems are caused by one of the monitor, the graphics card, or the graphics driver not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo nano /etc/X11/xorg.conf
``````
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       aa-bb
        VertRefresh     cc-dd
EndSection

```You'll need to replace aa-dd with the values for **your** monitor.

(Ctrl-O to save, Ctrl-X to exit)

According to [this page]("http://www.shopping.com/xPF-SyncMaster-15-TFT-LCD-Flat-Panel-Monitor-Black-512N"), the values you need for the monitor you're currently using are ```

        HorizSync       30-61
        VertRefresh     56-75

```If you have similar problems with the other monitor as well, you'll probably need to find similar values for that monitor too. To find the values for your monitor I just did a search on the model number.

---

### Post by phait on 2009-07-05
Hey that worked, thanks a lot.

Only issue left is when I drag a window around, or scroll in Firefox, it lags some. This didn't happen on the XP Pro install she had previously, it ran fine at 1024 x 768. Also when I closed the terminal, the wallpaper was like shifted for a few seconds, but only a portion the size of the terminal window. Those kind of things that happen in displays when a driver isn't installed (especially on Win machines)... although there is by default a Trident driver installed... but again, my Xorg.conf has nothing in it.

Guess I could check the log if that'll help.

---

### Post by phait on 2009-07-05
Bump. I won't be able to access her PC anytime soon, bringing it back today. If anyone has last minute/hour idea as to the lag.

Again thanks so much guys!

---

