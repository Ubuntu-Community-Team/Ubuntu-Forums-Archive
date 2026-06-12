---
title: "How do I get dual monitors working?"
date: 2012-04-28
forum: General Help
---

### Post by Zukaro on 2012-04-28
How do I set up multiple monitors in Ubuntu 12.04 with multiple graphics cards?
I have two graphics cards and two monitors; one monitor per card is how I have it set up (and I need it to remain in this setup).  How can I get my other monitor/graphics card working?

(both graphics cards are NVIDIA GeForce GTX 460)

I've looked around on Google and everything I've found only talks about using one graphics card.

---

### Post by Zukaro on 2012-04-28
Anyone?  I'm not sure what to do.

---

### Post by Zukaro on 2012-04-28
Is there any way to make Ubuntu detect my other GPU and use it?

---

### Post by MainframeGuy on 2012-04-28
Patience grasshopper - I am having some issues after an upgrade from Natty to Pengolin and my dual head has been knocked out, hence my return to these fora, so far my researches reveal that the "nvidia nouveau" driver will be needed and is not detected by default.

Unfortunately my dash seems to be broken and I cannot find a way to start synaptic so I am having issues with going further - but if you are experienced enough to make some sense of what I have said you may be able to proceed further (and it is best to wait a day or two rather than hours before bumping!)

[edit] see [http://ubuntuforums.org/showthread.php?t=1046504](http://ubuntuforums.org/showthread.php?t=1046504) 

also hopefully a more expert forum member might be able to post the "simple GUI" way to just take the latest drivers, since I notice that link is for latest 3Detc etc and may be slightly overkill to just fix dual head![/edit]

---

### Post by inspiredbylasers on 2012-04-28
I have the problem that my computer will not do mirror monitors with an attached LCD when running on Ubuntu partition.

---

### Post by Zukaro on 2012-04-28
> **MainframeGuy said:**
> Patience grasshopper - I am having some issues after an upgrade from Natty to Pengolin and my dual head has been knocked out, hence my return to these fora, so far my researches reveal that the "nvidia nouveau" driver will be needed and is not detected by default.

Unfortunately my dash seems to be broken and I cannot find a way to start synaptic so I am having issues with going further - but if you are experienced enough to make some sense of what I have said you may be able to proceed further (and it is best to wait a day or two rather than hours before bumping!)

[edit] see [http://ubuntuforums.org/showthread.php?t=1046504](http://ubuntuforums.org/showthread.php?t=1046504) 

also hopefully a more expert forum member might be able to post the "simple GUI" way to just take the latest drivers, since I notice that link is for latest 3Detc etc and may be slightly overkill to just fix dual head![/edit]


Okay; thanks.  I'll see if I can figure out the NVIDIA Nouveau driver and if that makes a difference or not.
(unless I just end up waiting for a more simple way :P)

---

### Post by MainframeGuy on 2012-04-28
> **inspiredbylasers said:**
> I have the problem that my computer will not do mirror monitors with an attached LCD when running on Ubuntu partition.
you may well be asked what your GFX card is - and for the OP here is a link to the nvidia site for your card (I believe this is the generic one, it is the one I need also anyway) [http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86/295.40/NVIDIA-Linux-x86-295.40.run&lang=us&type=GeForce](http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86/295.40/NVIDIA-Linux-x86-295.40.run&lang=us&type=GeForce)

---

### Post by inspiredbylasers on 2012-04-28
I'm pretty sure my drivers are all up-to-date/model.

---

### Post by Zukaro on 2012-04-28
> **MainframeGuy said:**
> you may well be asked what your GFX card is - and for the OP here is a link to the nvidia site for your card (I believe this is the generic one, it is the one I need also anyway) [http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86/295.40/NVIDIA-Linux-x86-295.40.run&lang=us&type=GeForce](http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86/295.40/NVIDIA-Linux-x86-295.40.run&lang=us&type=GeForce)

Thanks, I'll try that in a minute.

---

### Post by MainframeGuy on 2012-04-28
good luck all - and I am out of this thread having discovered my card was Radeon (doh!) The perils of working on too many things at once!

[EDIT] PROCEED WITH EXTREME CAUTION IF YOU ARE AIMING FOR DUAL HEAD SUPPORT - I have ended up with a system I am unable to log in to and for wich I cannot update my password even - I am thinking to re9install and move to 64 bit - at the moment resizing a partition....

I CANNOT SAY CLEARLY ENOUGH - IF YOU NEED DUAL HEAD DO NOT USE PANGOLIN AT THIS TIME

more details at this link [http://askubuntu.com/questions/127387/cant-login-through-gui-after-upgrade-from-11-10-to-12-04](http://askubuntu.com/questions/127387/cant-login-through-gui-after-upgrade-from-11-10-to-12-04)
now I am really out of this thread!
[/EDIT]

---

### Post by Zukaro on 2012-04-28
I tried installing NVIDIA's driver and it still doesn't work.

---

### Post by Zukaro on 2012-04-29
I've gotten it semi working.  I typed "sudo nvidia-settings" into the terminal and was able to enable my other monitor.  However, currently it appears blank white and is unusable.  When I put the mouse on that screen it turns into an X (the mouse turns into an X).

The NVIDIA settings allow me to get the "EDID" of the monitor, but I don't know how to use that to get it working, or if that's even what I'd use.



EDIT:
I got the second monitor working, BUT, it causes the system to become very instable.  There this thing called Xinerama, and when I enable that the second monitor works.  However, the error of RANDR not being present or something like that comes up because of it.  After disabling it, it causes more issues.  However, now that I've disabled the other monitor altogether it's working again (I got one error but I think rebooting will fix that).  It also makes everything look different, like, less clean (basically it makes everything use older icons).

Anyone know how to enable the other display without causing stability issues?
I didn't use the Ubuntu display settings to enable it, I used the NVIDIA settings (when trying to open the Ubuntu display settings I was given the error RANDR is missing (something like that) and it wouldn't open).  I can open it now, after disabling the display however.

---

### Post by *M* on 2012-04-29
Hi Zukaro, try issuing this command in Terminal

```
DISPLAY=:0.1 compiz --replace ccp &
```

Make sure to disable xinerama first

Then try 

```
DISPLAY=:0.1 gnome-terminal
```

If this starts a terminal in the second screen, probably missing the window-decoration, I can probably help you get dual screen working similar to my setup. The only problem I have at the moment is that I can't drag windows between screens (because I'm using separate X screens and twin view doesn't work with SLI afaik) and I've yet to get wallpaper working.

---

### Post by Zukaro on 2012-04-29
Currently my display is messed up now (videos on YouTube now appear blue even though I've disabled all the original changes I've made).  I don't know how to fix this other than reinstalling Ubuntu entirely; and at this point it's probably better to just reinstall (this is generally how things go with me, I'll set things up, mess them up, reinstall, and make them better and the way I wanted).

I haven't tried that terminal stuff yet however, I'll try that tomorrow.

---

### Post by *M* on 2012-04-29
> **Zukaro said:**
> Currently my display is messed up now (videos on YouTube now appear blue even though I've disabled all the original changes I've made).  I don't know how to fix this other than reinstalling Ubuntu entirely; and at this point it's probably better to just reinstall (this is generally how things go with me, I'll set things up, mess them up, reinstall, and make them better and the way I wanted).

I haven't tried that terminal stuff yet however, I'll try that tomorrow.

Yea I also had that blue youtube problem with Xinerama enabled, it doesn't happen with the method I use now though.

---

### Post by bordercore on 2012-04-29
> ***M* said:**
> Hi Zukaro, try issuing this command in Terminal

```
DISPLAY=:0.1 compiz --replace ccp &
```

Make sure to disable xinerama first

Then try 

```
DISPLAY=:0.1 gnome-terminal
```

If this starts a terminal in the second screen, probably missing the window-decoration, I can probably help you get dual screen working similar to my setup. The only problem I have at the moment is that I can't drag windows between screens (because I'm using separate X screens and twin view doesn't work with SLI afaik) and I've yet to get wallpaper working.
Hello.  I'm having similar dual monitor issues.  I used your technique to start a terminal on the second monitor, and it appeared without window-decoration.  How did you resolve this problem?

---

### Post by *M* on 2012-04-29
> **bordercore said:**
> Hello.  I'm having similar dual monitor issues.  I used your technique to start a terminal on the second monitor, and it appeared without window-decoration.  How did you resolve this problem?

Right, first of all on the screen that's working you want to run CompizConfig Settings Manager and take a note of each box that's ticked, either memorise it or press print screen and make an image of what's ticked. Note that the Ubuntu unity plugin doesn't have a tickbox but is enabled.

Now go to a terminal and issue this command
```
DISPLAY=:0.1 compiz --replace ccp &
DISPLAY=:0.1 ccsm
```

This will launch Compiz config on the broken monitor, but you should see that none of the options are ticks, thus the broken desktop. Now all you have to do is tick the boxes to match the compiz settings of the first screen and this should get it mostly functional. You might also notice that the window decorations break while ticking some of the boxes, don't worry though that can be fixed by either issueing the command again or it will be fixed automatically when you log out and back in.

If you are having problems with the mouse darting between the two screens, go to the Ubuntu Unity Plugin settings in compiz and under the experimental tab change edge stop velocity to a lower value.

Right, now you need a way to apply this as soon as you login, so make an appropriate folder somewhere and create an empty document called screenfix.sh and open it with a text editor paste this is then save it:
```
DISPLAY=:0.1 compiz --replace ccp &
```
Now right click on the file > properties > permissions > tick allow executing as program. Okay last step is to open the program Startup Applications from the unity menu. Now click add > give it a name, then browse to your screenfix.sh and add it. Close that all up and when you log back in your two desktops should load automatically.

I'm still working on getting wallpaper working so let me know if that's a problem for you too.



**Edit**: _Okay now for the wallpaper fix_

Make a directory somewhere eg:
```
mkdir ~/Nautfix
cd ~/Nautfix
```

Download the Source for Nautilus
```
sudo apt-get update
sudo apt-get build-dep nautilus
apt-get source nautilus 
```

Enter the newly created directory and download the patch/fix.
```
cd nautilus-*
wget https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/885989/+attachment/2590318/+files/nautilus.patch
```

Patch nautilus:
```
patch < nautilus.patch
```

When asked for the file to patch enter this:
```
./libnautilus-private/nautilus-desktop-background.c
```

Build and install the fixed Nautilus
```
sudo ./confiugre
sudo make
sudo make install
```

Kill old and run new nautilus and you should have two fully functional desktops!
```
sudo killall nautilus
nautilus &
```

---

### Post by Zukaro on 2012-05-01
Okay; it works now.  Thanks.  :)
Now I just need to get it so I can drag stuff from one monitor to the other (*isn't sure how to do that :v*).

---

### Post by Zukaro on 2012-05-02
I've set the mouse velocity thing to 1 (the lowest it will go) it still darts to the side of the other screen (when I move it to the other screen it basically teleports to the other side, however, if I slowly move it across the screen it doesn't dart).

---

### Post by *M* on 2012-05-03
> **Zukaro said:**
> Okay; it works now.  Thanks.  :)
Now I just need to get it so I can drag stuff from one monitor to the other (*isn't sure how to do that :v*).

You can't do that in an SLI setup unless you enable xinerama which disables compiz and makes everything look windows 95.

You can use twinview if you have one videocard or disable SLI

---

### Post by Zukaro on 2012-05-03
Okay; I'll just leave it how it is for now as it's not a huge issue (I can live with it :P).
Although, I don't think my video cards are SLI'ed (not really sure, but in Windows it say SLI is disabled and I need to get an SLI cable if I want them to be SLI'ed).

---

