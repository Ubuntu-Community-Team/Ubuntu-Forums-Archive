---
title: "Unity interface is now transparent"
date: 2011-06-03
forum: General Help
---

### Post by rejekt on 2011-06-03
The interface and everything was working fine at home. I packed up the laptop with me heading on a trip. I get to my location and power-up, I now can't see the Unity interface, but it's kind of there.

[IMG]http://img.photobucket.com/albums/v78/cuppb/misc/translucent_unity.png[/IMG]

I've tried to reboot the laptop, power off and back up, etc. I'm not really sure what would have cause this or where to even look at this point.

You can see at the very left that the arrow is there and at the top that the bar is kind of there, but not really. ><

Anyways, I'm gonna go get some dinner and try again later.

If anyone has an idea, thank you and I'll check back.

Brian

---

### Post by cobolt01 on 2011-06-03
Wow that's a strange one. Are you sure there wasn't anything that could have caused this? I'm not sure what's going on, but I'm keen to help you figure this out.
If nothing works, change the session type to "Ubuntu Classic (No effects)" or something like that at login, at the bottom of the screen. It only appears after you type in your username. Then:

First lets check your graphics drivers:
```

lspci | grep VGA

```
Does that seem right? What does it say?
You can try to check the Unity and Compiz settings. Install compizconfig-settings-manager
```

sudo apt-get install compizconfig-settings-manager

```
You can then access the it by System -> Preferences. Under the desktop tab, you'll find the Ubuntu Unity Plugin. It will be disabled if you are on the classic desktop. Click the Ubuntu Unity Plugin icon and make sure Panel Opacity is full. Check the other settings, if you want to reset all the settings to default, click Preferences in the bottom left of the CompizConfig Settings Manager main screen. Change the profile to unity and click reset to defaults. You may have to go back to the Desktop tab and check the Unity plugin again to re-enable the plugin for the unity profile, I don't know.

Let me know how all that goes :)

---

### Post by dFlyer on 2011-06-03
I would have suggested to shut down and reboot, but you've already did that. Is that the screensaver your using?? if it is can you press alt f2 and delete gnome-screensaver from .gnome/app/ in your home folder and reboot.

---

### Post by rejekt on 2011-06-04
@dFlyer: Yeah that was my first instinct. It's not my screensaver, my screensaver is the built-in 3d-matrix wallpaper. I haven't done much modification from the default install.

@cobolt01: Yeah, I've not seen this before.

> lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

That seems right, it's just an on-board graphics driver.

The opacity slider is full, and I even set the launcher to hide never.

The only thing I remember doing recently is package updates and not rebooting until I shut the laptop off for transport.

Edit:

I did change the type to Ubuntu Classic and it worked fine. Unity just isn't working like it was when I first installed Ubuntu. :(

---

### Post by cobolt01 on 2011-06-04
lol, I don't know its really broken.

---

