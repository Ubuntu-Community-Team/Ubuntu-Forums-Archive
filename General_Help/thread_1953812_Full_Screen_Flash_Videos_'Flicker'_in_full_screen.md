---
title: "Full Screen Flash Videos 'Flicker' in full screen"
date: 2012-04-06
forum: General Help
---

### Post by watgrad on 2012-04-06
Hi,
I installed Joli OS (a variant of ubuntu lucid) onto an old Dell Optiplex computer - intending to use it as a media pc connected to our TV.
Most things work well right after installation - (had to tinker a bit to get sound going through hdmi) - I can play online streaming videos from youtube, network station websites, ted...etc.  However, some flash video streaming sites (not all), don't play properly in full screen mode.  The video plays with sound, but random white bars flash on the screen.  Videos will play for a while fine, then the white flickering will start.  
Other sites play streaming video with no problems.
My specs are:
Nvidia GS 8400 (GeForce 210) video card
1G ram
Pentium 4 3.2 Ghz dual core
Nvidia driver 260.19.36
flash version 11.2.202.228
The ubuntu/joli os version 1.2

My question - how do I go about trouble shooting flash video streaming problems?  There are so many suggested paths to follow when searching on line - many of the suggestions are for older versions of ubuntu or flash...
Can anyone help with ideas of where to start trouble shooting this?
Thanks!

---

### Post by lovinglinux on 2012-04-07
Disable hardware acceleration and check if it gets better.

See [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

BTW, you CPU might not be enough to play Flash smoothly, since it uses a lot of CPU cycles. I had a CPU similar to yours and flash overheated the CPU after a few minutes watching YouTube videos.

---

### Post by watgrad on 2012-04-09
Hello - thanks for the suggestion.
I tried disabling the hardware acceleration option, it didn't seem to change anything. 
The strange thing is that most websites with streaming videos play fine -just some sites consistently cause the flickering...
I will work through the suggestions on the other thread you started to see if anything helps.
Thanks again

---

### Post by watgrad on 2012-04-11
Hello,
I was able to fix (sort of) my issues with flash-flickering but would still appreciate advice.

Using Flash-Aid I was able to install flash 9.0 in Firefox while still keeping Flash 11.1 in Chrome.  The flickering disappears in firefox with 9.0 - and is still present in chrome with 11.1.

I also tried flash 10.1 in firefox, but that also caused problems (this time you could see the normal flashplayer window from the website flashing on and off while in full screen mode...weird.

I understand that the older versions of flash have security issues, also, the video is choppier in flash 9.0 (unlike the flickering - the video seems to miss frames.

Anyway - I post this here in case there is something else I could try or have not considered.

Thanks for any advice you can give...

---

### Post by lovinglinux on 2012-04-11
Have you tried to login with Unity 2D instead of 3D? It might be a Compiz+Flash issue, since Flash doesn't play well with Compiz.

---

### Post by watgrad on 2012-04-11
This is an install of Joli OS - which is based on Ubuntu Lucid - it uses some kind of HTML5 frontend...the only compiz component installed is 'compiz window decoration library'.
Thanks...

---

### Post by xyzzyman on 2012-04-11
I had issues with JoliOS and some multimedia on a Core 2 Duo T9400 with 4GB of RAM. You may want to take a look at XBMCbuntu, or doing a minimal install of Ubuntu and building up from there... That 1GB of RAM could get tight if you go with a full distro that isn't lightweight like x/lubuntu or arch.

---

### Post by lovinglinux on 2012-04-12
> **watgrad said:**
> This is an install of Joli OS - which is based on Ubuntu Lucid - it uses some kind of HTML5 frontend...the only compiz component installed is 'compiz window decoration library'.
Thanks...

Oops, totally missed that. Sorry.

---

