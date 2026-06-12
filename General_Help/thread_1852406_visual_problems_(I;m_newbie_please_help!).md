---
title: "visual problems (I;m newbie please help!)"
date: 2011-09-30
forum: General Help
---

### Post by kevinjones30 on 2011-09-30
Hi all,

I recently moved over to ubuntu but I am a bit of a novice and am slooooowly learning my way around.

I've been having some graphics problems since installing and was hoping someone would be able to suggest a solution. 

I've attached a picture to this post so you can see what is happening - I'd say within 30 minutes of turning the computer on this glitch occurs to some extent - it distorts the desktop background image and makes text unreadable. There doesn't seem to be a consistent event that triggers it off, at least in the sense of something that I do...any suggestions anyone?

Many thanks,

Kevin

---

### Post by carranty on 2011-09-30
What graphics card do you have?  It may be a problem with that.  It could just be that it has some dodgy drivers installed that aren't working properly, have you tried choosing a different driver in System > Administration > Hardware Drivers?

Also, are you running compiz, or any other advanced visual effects?

---

### Post by kevinjones30 on 2011-09-30
Sorry how where can I see what graphics card I have / drivers are installed?

---

### Post by kevinjones30 on 2011-09-30
I have an integrated graphics card, sysinfo defines it as VGA compatible controller, not sure how to get more information than that...

---

### Post by carranty on 2011-09-30
Apologies, I should have said how.

If you open up a terminal (Applcations > Accesories > Terminal) and type 

[I]lspci | grep VGA

[/I]that should tell us the make and model of your graphics card.  I can then check around for known issues.

---

### Post by carranty on 2011-09-30
Please copy and paste the result to this thread.

To check drivers go to System > Administration > Hardware Drivers, it may come up with a recommended driver you could try changing to. If your using ubuntu 11.04 I'm not sure you can get to the drivers section that way (I'm on 10.04).  If so try typing

/usr/bin/jockey-gtk

into the terminal, that might bring it up.

---

### Post by kevinjones30 on 2011-10-23
Hi, sorry for late replying, my graphics card is Intel Corporation 82945G/GZ Integrated Graphics Controller ...i've tried installing the latest drivers using the below command, but if anything this seems to have made the problem worse!


sudo apt-get update && sudo apt-get install xserver-xorg-video-intel

---

### Post by dowcet on 2012-02-21
I have two different systems this problem, both have Intel graphics cards. Both are running Ubuntu 11.10, one of them a fresh install (but still running much slower then I would expect, possibly related?).  The text glitches get a lot better when I stick to Unity 2D, but still annoying. I noticed they tend to appear on certain letters (like right now, every letter "r" is messed up, [FONT=Verdana]everything else is fine.[/FONT]

When I run lspci | grep VGA:

> 00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

I have combed through other threads, most of it is very hard for me to follow. I did try the following command in case the output helps:

> brian@brian-ThinkPad-T60:~$ lsmod | grep i915
i915                  509519  2 
drm_kms_helper         32889  1 i915
drm                   192194  3 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915


And on both machines, there are no proprietary drivers. HELP!!

---

