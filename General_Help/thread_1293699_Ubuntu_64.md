---
title: "Ubuntu 64"
date: 2009-10-17
forum: General Help
---

### Post by arnab_das on 2009-10-17
Is it just me or is the 64 bit version of Ubuntu really prone to hang ups and crashes? I have all my graphics drivers properly installed however most of the time i find the Add Remove programme crashes. I have had to get accustomed  to synaptic.

Hope Karmic is a better 64 bit version.

PS - I have used the 32 bit version and find it way better than the current 64 bit. Virtually zero crashes in the 1 year i have used the 32 bit version of Ubuntu.

---

### Post by falconindy on 2009-10-17
Running 9.04 64-bit here. Zero crashes (that I didn't cause myself) since kernel 2.6.28-15.48.

---

### Post by MaindotC on 2009-10-17
Only crashes I'm getting are when I try to run Counterstrike in Wine.

---

### Post by arnab_das on 2009-10-17
my ubuntu version is "2.6.28-15-generic"

is that the one everyone's using?

---

### Post by MaindotC on 2009-10-17
Actually I'm using 2.6.31-11.

---

### Post by phidia on 2009-10-17
I've been using 64 bit linux for years (several distros) and haven't noticed any downside. There is an upside if you are doing processor intensive work like video editing. 

I am using the 2.6.28-15-generic kernel right now with 9.04 and haven't had any crashes. Try looking at your logfiles to see if you can find the reason for what's happening (System>Admin>Logfile Viewer).

---

### Post by oldos2er on 2009-10-17
When I first installed 9.04 last April, I would experience occasional hard freezes (the kind that require Alt-SysRq REISUB to get out of). It only happened 3 - 4 times, but was bothersome nontheless, since this was new behavior. 

 Since upgrading my Nvidia drivers to 185, running kernel 2.6.28-15-generic, I no longer experience these freezes, and all's back to being stable as a rock.

---

### Post by coldReactive on 2009-10-17
Haven't had a crash either. Been using x64 for a while, off/on with windows.

---

### Post by sirgogo on 2009-10-17
I've been running 64 bit Ubuntu for a while as well. I haven't had any more crashes in 64 bit than I have had in 32 bit. The only downside to 64 bit is that some apps that you may download (not through synaptic) may not work with the amd64 architecture. Most do, however, so its not that big of a deal.

---

### Post by phidia on 2009-10-17
For apps that hiccup under 64 bit try [getlibs]("http://ubuntuforums.org/showthread.php?t=474790")

---

### Post by ArtLaForge on 2009-10-17
> **phidia said:**
> I've been using 64 bit linux for years (several distros) and haven't noticed any downside. There is an upside if you are doing processor intensive work like video editing. 

I am using the 2.6.28-15-generic kernel right now with 9.04 and haven't had any crashes. Try looking at your logfiles to see if you can find the reason for what's happening (System>Admin>Logfile Viewer).

I was very happy with 32 bit Jaunty it was solid, but very slow at editing my pictures though, so after reading so many threads about how good 64 bit was at "video editing" I thought I would try it for my pictures. Loaded "fresh install" Jaunty 64 bit took weeks to get the basic fundamentals working, like flash and java. Then I tried my pictures I have 4800+ pictures that the previous os I used renamed each picture with name(copy (2),(3) etc so I was trying to sort groups of pictures out to put in a separate file to bulk rename but after selecting about 200 pictures the nautilus would grey out and die. Had to force quit.

Mostly as a learning process I loaded 64 bit karmic alpha 1 on my other machine. By this time several ops had figured out the flash and java fix so that went smooth. But I still have the same problem with pictures, when I select the picture folder with 4800 pictures I can go out to diner while all the pictures get displayed, when I start selecting groups I get the greyed out nautilus screen and have to force quit. Maybe a script to sort them into smaller folders would take care of it????

---

### Post by Johnny B on 2009-10-17
i've had no problems running 64 bit, and i think its much better than 32 bit, especially because i have 6 gigs of ram.
dont bother getting accustomed to synaptic, karmic brings the new "ubuntu software center".

---

### Post by falconindy on 2009-10-17
> **arnab_das said:**
> my ubuntu version is "2.6.28-15-generic"

is that the one everyone's using?
I've been compiling my own kernels, mainly to get the benefits of a preemptive RCU ever since I switched to Ubuntu back in August. Of course, compiling your own kernel can work against you if you muck something up in the config process.

---

### Post by ArtLaForge on 2009-10-17
> **Johnny B said:**
> i've had no problems running 64 bit, and i think its much better than 32 bit, especially because i have 6 gigs of ram.
dont bother getting accustomed to synaptic, karmic brings the new "ubuntu software center".

Yes the 6gig ram was my main reason to go with 64 bit and I have been happy with the performance of Karmic 64 bit, except for my picture experiance post #11 But Karmic has not been released yet so I'll wait and see. I do not see any show stopper to go with 64 bit. :P

---

### Post by arnab_das on 2009-10-17
thanks for your response folks!

i have figured out what the problem is. its my nvidia driver. for some reason compiz keeps on showing "screen is not composited error". i tried compiz --replace but that way, i lose all the effects of compiz :(

---

### Post by arnab_das on 2009-10-17
now i know whats the root of all my miseries.

there's absolutely no proper nvidia drivers for ubuntu 64. the 180 version crashes while installing and there's some jockey error or something.

and now i had to uninstall compiz, awn and tone down my ubuntu to a basic version with zero graphics effects. no wonder it doesnt hang anymore!

pity...

---

### Post by arnab_das on 2009-10-17
finally solved the problem by downloading the latest nvidia driver from [Drivers - Download NVIDIA Drivers ]("http://www.nvidia.com/Download/index.aspx?lang=en-us")and following the instructions on [nVidia latest Drivers - How to install - (180.xx - 185.xx - 190.xx) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=990978")

---

### Post by oldos2er on 2009-10-17
There's a PPA with Nvidia 185 and beta 190 video drivers. There is a how-to here: [http://webupd8.blogspot.com/2009/08/how-to-install-nvidia-190xx-drivers-in.html](http://webupd8.blogspot.com/2009/08/how-to-install-nvidia-190xx-drivers-in.html)

---

