---
title: "desktop shifted on screen, really confused :???:"
date: 2010-08-01
forum: General Help
---

### Post by LifeEnemy on 2010-08-01
I attached screen shots of what's happening. Basically half of my desktop turned black, with my wall paper shifted over halfway, but the icons are all in the same place. The left half keeps the image of whatever window was just over it. Really annoying.

I tried using the "force quit" tool for the gnome bar, but it acted like there was nothing there, just desktop.

I've been thinking of upgrading (running 9.04 right now). Would it be a good idea to update with this going and see if it gets fixed? I didn't want to try without asking in case it causes some major problems.

Thanks for reading!

---

### Post by themusicalduck on 2010-08-01
Could give upgrading a go, 10.04 works really well. If you do though, I would do a fresh install if you can rather than upgrade through the update manager.

Also, burn off a CD of 10.04 and run it in a live CD session to see if everything works well first.

---

### Post by LifeEnemy on 2010-08-04
is there a particular reason to do a fresh install? I don't want to have to reload everything I have. Although I do have my /home on a separate partition. Is there anything stored **not** on the home section that would require me to reinstall?? Sorry if that's a noobish question.

Also, if anyone has any different suggestions that require less work, I'm open to trying those first. It's hard to find time to devote to upgrading my comp and making everything work, so if there was someway to fix this until I find the time, it'd be a big help.

Thanks for putting up with me.

---

### Post by hawthornso23 on 2010-08-05
That looks like a video driver/card issue to me. Video memory is being used in the wrong way by something. What sort of video setup do you have? Try switching to the proprietary/free driver. Does the switch make a difference? 

try switching between metacity and compiz

```
metacity --replace
```
```
compiz --replace
```

in a terminal. Try reinstalling just your video drivers.

---

### Post by LifeEnemy on 2010-08-06
I'm using a Dell XPS M1530, with a GeForce 8400M GS. I'm using the NVIDIA driver, version 180.44 right now.

I did the switch to metacity (not sure why I didn't think to try that before). I thought it worked, but it kept the same problem slightly modified. When using metacity, the black part of my screen was just a copy of the same section of my desktop image that is on the right side, and windows don't leave a trail. However, the icons are still shifted onto the right side (some off the screen) just like before. I tried dragging them to the side, but they move back to the right half of the screen. My cairo dock desklets don't mind staying on the left half, though.

Sorry for the wall of text. Any suggestions from here?

---

### Post by hawthornso23 on 2010-08-09
Sorry - I'm an ATI kind of guy - don't know much about nvidia 
drivers.  But try reinstalling and reconfiguring the video driver
before you do a complete reinstall. 

Also try booting up in safe mode from grub and seeing if the screen
looks normal (albeit low resolution). If it does then that just confirms 
it is most likely a video driver issue (rather than something hardware
related. 

If you are thinking about a complete reinstall anyway then you've got 
nothing to lose by experimenting a bit. Search Synaptic for anything 
video related and mark plausible looking stuff for complete reinstallation.

Good Luck.

---

### Post by hawthornso23 on 2010-08-09
One last thought.

Have you used an external moniter recently? Just have a quick look in System-preferences-moniters and make sure it doesn't think you've got a dual moniter setup or something weird like that.

---

### Post by Quackers on 2010-08-09
What happens when you run System > Administration > Hardware Drivers? Is an updated driver available?

---

### Post by LifeEnemy on 2010-08-09
Problem solved! At least that's how it seems at the moment. I ran ubuntu under recovery mode and a menu came up with options like resume startup, root shell access, etc. One of them was "xfix" that said it would attempt to automatically fix graphics problems. Hit enter and it did it's thing, then I went to "resume." 

When I booted up the desktop was back to normal, but it looked like metacity was loaded (compiz is default). I couldn't use any higher-graphics features, and eventually figured out that GLX/nVidia drivers had been uninstalled. I ran "EnvyNG" to get them back (kept it from a different problem) and now everything seems ok! Not sure what happened to it in the first place, but thanks for all the helpful input and pointing me in the right direction :D

---

### Post by hawthornso23 on 2010-08-10
Woo hoo - well done!

It gives you a real kick when you fix a problem like that. 

Excellent.

---

