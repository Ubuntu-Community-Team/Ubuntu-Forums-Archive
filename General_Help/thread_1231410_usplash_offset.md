---
title: "usplash offset"
date: 2009-08-04
forum: General Help
---

### Post by sdlynx on 2009-08-04
I reinstalled Ubuntu and everything was fine, but I needed to run ```
sudo update-initramfs -u
``` and now the splash screen while booting/shutting down is offset to the right and down.  Also, the shadow isn't on the bar.  Honestly this doesn't impede performance much at all but I'd like it back to normal.  I've tried reconfiguring usplash, and it has the resolution correct... Can anyone help?

---

### Post by Don1500 on 2009-08-04
> **sdlynx said:**
> I reinstalled Ubuntu and everything was fine, but I needed to run ```
sudo update-initramfs -u
``` and now the splash screen while booting/shutting down is offset to the right and down.  Also, the shadow isn't on the bar.  Honestly this doesn't impede performance much at all but I'd like it back to normal.  I've tried reconfiguring usplash, and it has the resolution correct... Can anyone help?

Believe it or not I had this problem and bumped for a week with no answer. Try to put "791" in the resolution for menu.lst (Its an option, I just don't have my Ubuntu machine or I could show you where.) I'm sure if you search menu.lst you can find it. Read the instructions for the option and slide "791" in there. It sets up a resolution for the splash screen. This number worked for me and moved my splash to the center.

---

### Post by sdlynx on 2009-08-04
lol alright thanks I'll give it a shot

---

### Post by Tteddo on 2009-08-04
You could also install Startup Manager. That gives you all kinds of control over startup.
> sudo apt-get install startupmanager

---

### Post by Don1500 on 2009-08-04
> **sdlynx said:**
> lol alright thanks I'll give it a shot

Only use 791, every other number I tried, even though my monitor could handle it, the screen was off center. (you can do a search of the forum to find a list of the numbers available)

And I came back to add....
```
Screen	640x480	800x600	1024x768  1280x1024  1600x1200
Colors 	-	-	-	-	-
256	769	771	773	775	796
32,768	784	787	790	793	797
65,536	785	788	[COLOR="Red"]**791**[/COLOR]	794	798
16.8M 	786	789	792	795	799
```

---

### Post by sdlynx on 2009-08-04
ah, interesting.

I have startup manager already btw and it can't seem to fix the problem.  However my screen size is 1280 x 800 not 1024 x 768 or anything 4:3...

---

### Post by Tteddo on 2009-08-04
> **sdlynx said:**
> ah, interesting.

I have startup manager already btw and it can't seem to fix the problem.  However my screen size is 1280 x 800 not 1024 x 768 or anything 4:3...

You are only picking what the video card displays during the splash screen part of booting, so it's kinda like whatever works. I had a computer come through here last week that needed 800x600 8 bit or it was blank (that's how I heard of the Startup Manager). I was looking for the best experience for a new Ubuntu user so I wanted it to work right even with an old Intel card.

---

### Post by sdlynx on 2009-08-04
oh, alright, well I'll keep that in mind

it seems to have fixed itself for the moment

---

