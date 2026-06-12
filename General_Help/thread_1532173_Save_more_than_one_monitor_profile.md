---
title: "Save more than one monitor profile?"
date: 2010-07-16
forum: General Help
---

### Post by miststlkr on 2010-07-16
My experience with  gnome is quite limited and I am only marginally more familiar with X so please forgive if this is an overly simple question.  

I have Ubuntu 10.04 running on a laptop which I often use with an external monitor in dual monitor mode while at home.  It seems there would have to be a way to save more than one monitor/display profile so I can quickly and easily switch to the dual setup when i get home rather than have to manually adjust the positioning anf resolution of both screens each time.  On X I would dig around in x.conf, perhaps write a script/launcher to toggle the x.conf file currently being used.... but I don't have any clue how gnome handles such things.   Could someone point me in a direction to look into it?

Thanks for your time

---

### Post by dcstar on 2010-07-16
> **miststlkr said:**
> My experience with  gnome is quite limited and I am only marginally more familiar with X so please forgive if this is an overly simple question.  

I have Ubuntu 10.04 running on a laptop which I often use with an external monitor in dual monitor mode while at home.  It seems there would have to be a way to save more than one monitor/display profile so I can quickly and easily switch to the dual setup when i get home rather than have to manually adjust the positioning anf resolution of both screens each time.  On X I would dig around in x.conf, perhaps write a script/launcher to toggle the x.conf file currently being used.... but I don't have any clue how gnome handles such things.   Could someone point me in a direction to look into it?

Thanks for your time

System-Preferences-Monitors or whatever tool the hardware driver you use has installed.

---

### Post by miststlkr on 2010-07-16
Yes, then I reposition the displays to vertical rather than horizontal layout, change the resolutions, etc. then go to System - Prefrences - Appearance - Visual Effects and change the setting up from the lowest.  I got that far.  I am looking for a way to perhaps save the way I like it to a second config file and load that when I add/remove the monitor rather than having to spend the few minutes every time I decide to use the computer away from the desk.  It's a minor nuisance, granted, but I thought it was worth asking if there was a way to do it.  I am pretty sure with X I would be able to create a second x.conf file and write a script that would check which was currently being used then restart X using the other... but in gnome I haven't the foggiest.

---

### Post by lunatico on 2010-08-25
I'm also looking for a solutions to this.

The first thing to know is that this will be different with different graphic cards. ATI, Nvidia, Intel... And different with the type of graphics drivers you choose to use, open source, proprietary, etc...

The most integrated with gnome would be whatever you get by default right after installing. In this case you will just use System -> Preferences -> Monitors to configure your different setups. But as you said, it won't remember them, it won't save like configuration profiles.

I don't like to extend my desktop, I just clone them. Which makes things a bit easier. I don't see the point on extending when you have the option of creating many workspaces. Just a matter of taste.

There is a very good application that automatically detects your screens and configure them to their preferred resolution in either cloned or extended modes. Unfortunately it stopped working for me in 10.04 so I wrote a little script. You can try it and see if it works for you.
Disper: [http://willem.engen.nl/projects/disper/](http://willem.engen.nl/projects/disper/)

So this is how I work. Normally at my desk my laptop is docked, with the lid closed and with a 24 inch monitor connected. When I undock I just open the lid and everything is fine. When I go to meeting I just plug the projector and configure via the Monitors application, most of the time I use extended just so that my laptop screens resolution stays the same. But some times I have to clone which is fine, the only problem is that projectors will normally support lower resolutions than the laptop screen so the laptop screen will get that lower resolution, which some times messes up the position of the applets in the panel.
When I get back to my desk, with the lid closed I just dock the laptop back in and I get on the monitor the same as I have on the laptop screen, but the thing is still extended. So what I do is that I have this command attached to a shortcut key.
```
xrandr --output LVDS1 --auto --output VGA1 --auto --same-as LVDS1
```
That clones my screens back.

---

### Post by lunatico on 2010-08-25
I just realized that the command
```
xrandr --output LVDS --auto --output VGA --auto --same-as LVDS
```
was not longer working as expected for me because I recently changed my monitor to one that can take higher resolutions.
So I just modified it with
```
xrandr --output LVDS --mode 1680x1050 --output VGA --mode 1680x1050 --same-as LVDS
```
and have that bind to a keyboard shortcut using compiz settings manager.

---

### Post by miststlkr on 2010-08-25
Hm... That line, modified of course, may work for what I was looking to do.  presumably I could change that to something like 

```

xrandr --output [[netbook display name]] --mode 1024x600 --output VGA --mode 1680x1050 --above LVDS 
```


and set that to a keystroke combination.


THANKS!!!

---

### Post by lunatico on 2010-08-25
Yes it should work.
You probably know this but just do
```
xrandr -q
```

To see how your laptop screen and external monitor are called.

---

### Post by miststlkr on 2010-08-25
No, I didn't.  I haven't used linux in years [played with a Red Hat distro in the mid 90's]], but I remember enough that the first thing I tried would have been *man xrandr* to figure out how to use it.   Thanks for stating what you assumed was the obvious though, there are a lot of beginners for whom the obvious isn't quite so obvious. [[myself included]]

Cheers!

---

### Post by lunatico on 2010-08-25
> **miststlkr said:**
> No, I didn't.  I haven't used linux in years [played with a Red Hat distro in the mid 90's]], but I remember enough that the first thing I tried would have been *man xrandr* to figure out how to use it.   Thanks for stating what you assumed was the obvious though, there are a lot of beginners for whom the obvious isn't quite so obvious. [[myself included]]

Cheers!

I'm no expert myself! That's the beauty of Ubuntu and of this forum, you'll always find helpful people.

Good luck with that!

---

### Post by miststlkr on 2010-08-25
Absolutely!   This board has been an outstanding resource for me so far.  I like to hang out and ask in the IRC chan as well, but I do tend to have better success/solution rate here on the forums.

---

### Post by furball4 on 2010-11-27
I am trying to get a certain monitor setup to function and I am having a terrible time wrapping my head around what is necessary. Hoping to get some help here.

System: ThinkPad W510
Video Card: NVIDIA Quadro FX 880M (GPU 0)
Driver: nvidia
Internal Display: LEN (DFP-0) 1920x1080 [Connection Link: Dual; Signal: LVDS]
External Display: DELL 2007FP (DFP-1) 1600x1200 [Connection Link: Single; Signal: TMDS]

I have this working just fine at my home desktop. I have my external monitor plugged into the laptop's DisplayPort port with a DisplayPort -> DVI-D cable and I use the TwinView setting in the *NVIDIA X Server Settings* program to extend my desktop onto the second display. The automatic result of my setup was a single X screen, numbered Screen 0, with dimensions of 3520x1200. This makes sense to me, and I can pretty much see how this is saved to xorg.conf:[INDENT]    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: 1920x1080 +0+0, DFP-1: 1600x1200 +1920+0
[/INDENT]The one thing I can't see is where DFP-0 and DFP-1 get identified. The only time they appear in xorg.conf is in these lines.

Anyway, my problem arises at work. There I have exactly the same setup, except I have a powered signal splitter between my laptop and the external monitor. It's the same screen I use at home, same resolution, same everything. But I'm splitting the image out to another identical display so that the person sitting across the desk from me can easily see whatever I place on my secondary display. The problem is, the splitter interferes with the laptop's ability to auto-detect the display, with the result that no image is output to that display. Instead it behaves exactly as if I had started X without anything plugged in at all. If it would only send exactly the same signal that it does at home, everything should work just fine. How can I make it do this?

---

