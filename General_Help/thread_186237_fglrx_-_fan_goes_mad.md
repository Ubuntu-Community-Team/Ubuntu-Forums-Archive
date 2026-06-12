---
title: "fglrx - fan goes mad"
date: 2006-06-01
forum: General Help
---

### Post by glxblt on 2006-06-01
Hi.

I'm running Dapper i386 on my A64 with an ATI X800 Pro. I installed it using the desktop image.

The original ATI drivers supplied with the installation didn't work, I was locked to 640x480. Installing fglrx helped, and everything was fine & dandy until I found out that the machine is damn noisy.

Yes indeed, the driver spins the poor ATI's fan at full speed constantly, right from when the driver is loaded. I have no heat problems with my computer, and the fan keeps quiet in Windows, only revving up under extreme load.

Gosh, I don't even know where to start. :( Any ideas?

---

### Post by Rackerz on 2006-06-01
[QUOTE=glxblt]Hi.

I'm running Dapper i386 on my A64 with an ATI X800 Pro. I installed it using the desktop image.

The original ATI drivers supplied with the installation didn't work, I was locked to 640x480. Installing fglrx helped, and everything was fine & dandy until I found out that the machine is damn noisy.

Yes indeed, the driver spins the poor ATI's fan at full speed constantly, right from when the driver is loaded. I have no heat problems with my computer, and the fan keeps quiet in Windows, only revving up under extreme load.

Gosh, I don't even know where to start. :( Any ideas?[/QUOTE]

Even though ATI isn't great with Linux support I'd try contacting them and telling them about this problem. I've got a 9800XT running with fglrx and the fan is quiet, my machine is quiet and the case sides are off! So I'm not sure what it could be.

---

### Post by Jacky_J on 2006-06-02
[QUOTE=glxblt]Hi.

I'm running Dapper i386 on my A64 with an ATI X800 Pro. I installed it using the desktop image.

The original ATI drivers supplied with the installation didn't work, I was locked to 640x480. Installing fglrx helped, and everything was fine & dandy until I found out that the machine is damn noisy.

Yes indeed, the driver spins the poor ATI's fan at full speed constantly, right from when the driver is loaded. I have no heat problems with my computer, and the fan keeps quiet in Windows, only revving up under extreme load.

Gosh, I don't even know where to start. :( Any ideas?[/QUOTE]

I'm getting a similar problem, if not the same one.  A few seconds after the desktop screen comes up, i hear the fan on my ATI X800 PRO start spinning.  It doesn't go away either.  As i reboot into Windows, the fan noise will go away after a few minutes.

Now i'm certain this is a problem with the ATI 8.25.18 drivers. When i had Breezy i updated the video drivers to this version, and i was getting the same fan problem, so i reverted back.  It's as if the drivers are causing the video card to spin the fan when it doesn't need to, or is causing it to do work when it's not doing anything else.  

I've tried using my old xorg.conf, with no success.  I'm tempted to go back to Breezy.

---

### Post by zak- on 2006-06-08
Same exact problem here with X800 XT :(

---

### Post by vertigo1980 on 2006-07-27
anybody figured how to fix this? I have an X800XL, and tried the newest fglrx drivers as well as the version before that, and the fan still revs up for nothing. completely quiet in windows unless playing games :(

---

### Post by Violaine on 2006-08-15
I've got the same problem with an X800 Pro, latest ATI driver, and Ubuntu 6.06 (x64).  It seems the fan speed is increasing because of a lot of heat.  By the time I can start the catalyst control center in windows it's cooled down to 70C.

There are a few other odd problems. The 3d screen savers stopped working after I installed the ATI driver. If I run one from the command line, for example /usr/lib/xscreensaver/lattice, that'll work, but if I use the --root flag (as I assume gnome-screensaver does), nothing happens.

Also running fgl_glxgears returns this text:
Using GLX_SGIX_pbuffer
Floating point exception

However if I use the -fbo flag, it works and returns this text:
Using GL_EXT_framebuffer_object

Another problem is that the latest Cadega will show spinning gears, even though it tells me the 3D test failed.

Is all this stuff connected somehow?  I don't know, being a noob.  It's too bad, I really wanted to use Linux, but I'm going to need 3d to work, and I'd like to not worry about burning down the house.  I've spent about 2 days googling, reading the manuals, and searching the forums to no avail.  Also I followed the howto steps to the letter, except I generated the Ubuntu/6.06 packages instead of Ubuntu/dapper.

Should I report these problems as bugs, or am I missing something obvious?  I'd have bought an nVidia card already but I don't have the money just yet.

---

### Post by Jacky_J on 2006-08-16
> **Violaine said:**
> I've got the same problem with an X800 Pro, latest ATI driver, and Ubuntu 6.06 (x64).  It seems the fan speed is increasing because of a lot of heat.  By the time I can start the catalyst control center in windows it's cooled down to 70C.

There are a few other odd problems. The 3d screen savers stopped working after I installed the ATI driver. If I run one from the command line, for example /usr/lib/xscreensaver/lattice, that'll work, but if I use the --root flag (as I assume gnome-screensaver does), nothing happens.

Also running fgl_glxgears returns this text:
Using GLX_SGIX_pbuffer
Floating point exception

However if I use the -fbo flag, it works and returns this text:
Using GL_EXT_framebuffer_object

Another problem is that the latest Cadega will show spinning gears, even though it tells me the 3D test failed.

Is all this stuff connected somehow?  I don't know, being a noob.  It's too bad, I really wanted to use Linux, but I'm going to need 3d to work, and I'd like to not worry about burning down the house.  I've spent about 2 days googling, reading the manuals, and searching the forums to no avail.  Also I followed the howto steps to the letter, except I generated the Ubuntu/6.06 packages instead of Ubuntu/dapper.

Should I report these problems as bugs, or am I missing something obvious?  I'd have bought an nVidia card already but I don't have the money just yet.

I was able to do 3D applications just fine on mine.  It was just that the fan was spinning the whole time.  
I don't know if the spinning fan problem is related to your 3D problems, but make sure your "glxinfo | grep rendering" says yes. 

I never figured it out, and after a couple hours of 6.06 i put 5.10 back on. Then I built a new computer with an nVidia card, so  I guess i'll never know. :-|

---

### Post by Violaine on 2006-08-16
glxinfo returns "direct rendering: Yes"

I just remembered another little oddity, glxgears never displays a framerate, even though it's working.  I bet that's connected to Cedega failing the 3d test, since it seemed to use glxgears.

Anyway, I'm going to switch to 32-bit Ubuntu to see what happens.  I fully expect the fan problem will still be there, but it'll be interesting to see if everything else works.

---

### Post by Violaine on 2006-08-16
32-bit was much worse.  The fan problem was still there, not a big deal really.  I had to log out to get rid of some video corruption in the lower panel.  The screensavers worked, if 2 fps is working.  When I ran one of them from the terminal, nothing happened.  Worse yet, glxinfo locked the system so hard I couldn't move the mouse or reset X.  Oh well, I'll try again when Edgy Eft is released.

---

### Post by Jacky_J on 2006-08-17
Well, since you're already this far, you might as well try Ubuntu 5.10.  Aside from a few minor annoyances, everything's the same.

---

### Post by Violaine on 2006-08-18
Things are looking up.  Whatever glitch caused all that trouble disappeared when I rebooted.  Now 32-bit is working better than 64-bit, just a little slower.  It should get better when I compile the kernel to match my processor.  glxgears still doesn't return a framerate and Cedega thinks it can't do 3d, but I don't care because it works anyway :)

---

### Post by Dropknee on 2006-08-23
I have a X800 XT PE and have the fan problem too, pls someone give a solution :(

---

### Post by neogenesis213 on 2007-08-04
I have x1900xt and I have the fan almost driving me deaf. Anyone know what to do?

---

### Post by Jacky_J on 2007-08-04
Sell your x1900xt and buy an nvidia card.

---

