---
title: "Ubuntu is slow"
date: 2010-06-12
forum: General Help
---

### Post by boebi on 2010-06-12
I just installed Ubuntu on my new laptop (I totally love it btw) but for some reason it seems to be simply slow.

I thought Linux was supposed to be more lightweight and faster than Windows but right now this is not the case. A lot of the time I run 2 windows next to each other, one has a movie playing and the other has stuff like my internet browser.

Now anytime I try to enter a new URL and the suggestion box shows up in Firefox, the movie laggs and stutters, whenever I open another program, same happens.

This never happens in Windows so I'm confused.

My laptop specs btw:
Intel i7-620
8GB ram
2x 285m nvidia graphics cards in sli
(before anyone asks, yes I am sure this are my specs lol, it's a custom build)

Is there any way I can make things go smoother?

---

### Post by an0dos on 2010-06-12
> **boebi said:**
> I just installed Ubuntu on my new laptop (I totally love it btw) but for some reason it seems to be simply slow.

I thought Linux was supposed to be more lightweight and faster than Windows but right now this is not the case. A lot of the time I run 2 windows next to each other, one has a movie playing and the other has stuff like my internet browser.

Now anytime I try to enter a new URL and the suggestion box shows up in Firefox, the movie laggs and stutters, whenever I open another program, same happens.

This never happens in Windows so I'm confused.

My laptop specs btw:
Intel i7-620
8GB ram
2x 285m nvidia graphics cards in sli
(before anyone asks, yes I am sure this are my specs lol, it's a custom build)

Is there any way I can make things go smoother?

Is this a WUBI install? Have you installed the proprietary nvidia drivers?

---

### Post by boebi on 2010-06-12
I believe WUBI install is when you start the installation from inside windows?

This is not the case, I used the the cd and booted from that.


About the drivers, it prompted me if I wanted to install new (or enable new) drivers when I tried to turn up the effects at the Appearance settings, I did that.

I just found out that there are new drivers on the nvidia website but installing them seems to be a real hassle?

---

### Post by Rodney9 on 2010-06-12
I am using Xubuntu on my laptop and it runs fast.

---

### Post by boebi on 2010-06-12
My laptop's specs are better than most of the community's their desktop's and they can run Ubuntu without any problems.

So I'm stuck really, I don't see why it's lagging. 


I just installed the latest nvidia driver (found it, couldnt be easier) and it looks like SOME of the stuttering is gone now. Although I'm still having issues with slow loading.

---

### Post by an0dos on 2010-06-12
> **boebi said:**
> My laptop's specs are better than most of the community's their desktop's and they can run Ubuntu without any problems.

So I'm stuck really, I don't see why it's lagging. 


I just installed the latest nvidia driver (found it, couldnt be easier) and it looks like SOME of the stuttering is gone now. Although I'm still having issues with slow loading.

I'm using a 2.8ghz Phenom x3 with 2GB of RAM without any slowdown issues. In principle you should not be having any problems with lag. I'm not a linux expert so I will be grasping for straws here. 

Have you checked the system monitor to see if any processes are taking an inordinately large amount of CPU or RAM?

If you turn off the desktop effects, does your performance improve?

---

### Post by Smart Viking on 2010-06-12
Something is definitely wrong here since the specs are sick!

Are you running 64Bit? 

Maybe it can have something to do with 2x GTX 285, i use GTX 285 myself but not two of them, you could try to only use one to see what happens. :)

---

### Post by limestone on 2010-06-12
I'm running on a 2Ghz processor and 2gig RAM with shared video memory and mine runs like a porsche :P

---

### Post by limestone on 2010-06-12
> **boebi said:**
> I just installed Ubuntu on my new laptop (I totally love it btw) but for some reason it seems to be simply slow.

I thought Linux was supposed to be more lightweight and faster than Windows but right now this is not the case. A lot of the time I run 2 windows next to each other, one has a movie playing and the other has stuff like my internet browser.

Now anytime I try to enter a new URL and the suggestion box shows up in Firefox, the movie laggs and stutters, whenever I open another program, same happens.

This never happens in Windows so I'm confused.

My laptop specs btw:
Intel i7-620
8GB ram
2x 285m nvidia graphics cards in sli
(before anyone asks, yes I am sure this are my specs lol, it's a custom build)

Is there any way I can make things go smoother?

It could be something with the 2x graphic or did you install an x86_64 instead of i386?

---

### Post by 3rdalbum on 2010-06-12
Have you checked the System Monitor to see whether there's a program that's running away with your CPU power? This can happen, just see what program it is in the Processes tab, and then right-click it and choose "End Process". If this doesn't work, then you may need to consult some information online about forcing processes to exit.

---

### Post by an0dos on 2010-06-12
> **Smart Viking said:**
> Maybe it can have something to do with 2x GTX 285, i use GTX 285 myself but not two of them, you could try to only use one to see what happens. :)

+1

Based on what I've read on these forums, I don't think Linux support for SLI is quite there yet. 


One other thought: I've found that some computers do not seem to work equally well with all linux distros (ie some require less tweaking to get things to work).

If Ubuntu gets to be too much of a headache, you can always try out opensuse or linux mint (although linux mint may not help very much since it is an ubuntu-based distro).

---

### Post by ell02 on 2010-06-12
ummm,not to be a wise guy.But did u install it?

I used the the cd and booted from that.

---

### Post by boebi on 2010-06-12
Yeah I obviously installed it :

I checked and my CPU was at something like 25% so that should be alright. 

But I've been spending 6 hours on trying to get a Dual Boot working (still not working) and another problem popped up!
Whenever I try to play a video file, everything looks blue-ish! I inserted my dvd of 24, for people who know the series, and at the beginning when the digital 24 comes up its simply BLUE.

Whenever I start the Nvidia X Server Settings it turns back to normal. But if I then try starting it again, it's still blue. So the actual starting of the Nvidia settings is somehow fixing it. Any ideas?

---

### Post by boebi on 2010-06-12
> **pont.andersson said:**
> It could be something with the 2x graphic or did you install an x86_64 instead of i386?

Yes I installed x86_64, should I try something else?

I was assuming the 32/64bit rule was the same with Linux, that there's a RAM limit at 3.4GB so I took the 64bit one.

---

### Post by eyeofreason on 2010-06-12
I have nearly this same rig. I have never been able to get good sli support to work  . I have the proprietary driver installed for the 1 nvidia gf8600gt and i also occasionally see a blue hue.  However I have lighting speed compared to the windows boot.  

As far as a dual boot , the way i do it is install windows first then Ubuntu and the Ubuntu install cd and grub loader handle everything for you.

---

### Post by boebi on 2010-06-12
Yeah well that didn't work out very well. What I finally got working is setting my SSD with Windows 7 to 1st boot and use EasyBCD2.0 beta to add GRUB2 to the list. Now it's going through 2 bootloaders but alteast its working ^^

Then back to the speed, I think that the new Nvidia driver actually gave me a performance boost but all of the sudden I get this blue hue as you said. Problem is it's ALWAYS there for me. Any ideas on how to get rid of it?

EDIT: I got a fix for the blue hue:
[source](https://answers.launchpad.net/ubuntu/+source/totem/+question/7373)
> 
launch gstreamer-properties from terminal
change the video output plugin to custom
change the video output pipeline to:

ffmpegcolorspace ! video/x-raw-yuv,format=(fourcc)YV12 ! xvimagesink

---

