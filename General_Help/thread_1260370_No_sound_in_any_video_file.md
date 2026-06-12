---
title: "No sound in any video file"
date: 2009-09-07
forum: General Help
---

### Post by jamesje on 2009-09-07
Hello all,

I have been fiddling around with kubuntu 9.04 for a bit but i don't have sound with Youtube or any other programs like VLC-player.

I have tried many of the standard fixes but, for some reason all things on internet don't seem to work for me. with all distro's with everything xD i always get like one or two steps going for me then they all fail.. i dont know what i do wrong maybe i am just dumb *sad face* but i also don't want to be a burden so if you see a thread of me in the future and you don't want to waste time then you don't have to ^^ thank you so much in advance.

James

---

### Post by ankspo71 on 2009-09-07
Hi,

Do you have the necessary codecs installed, such as gstreamer? I found a small site for testing audio and video files that might be useful... [http://dougneubauer.com/mhcctest/](http://dougneubauer.com/mhcctest/) .  I believe all of those will be playable by installing gstreamer codecs. You can install the individually in Synaptic Package Manager, or you can install one big meta-package called kubuntu-restricted-extras. These extra codecs are not installed by default because of licensing reasons I think. On that site you can see more test links down below at the bottom of the page.

VLC should play audio and video without a problem, if it was installed from within ubuntu's repositories. I believe there are extra plugins for VLC available for different sound servers too. Be sure you are using the latest flash player too, because version 9 has no audio for me when I downloaded it from the adobe site. I think the last time I tried Kubuntu, youtube told me Konqueror wasn't compatible. So try Firefox (or another) if you continue to have problems.

One thing that threw me off when I installed linux, is that the mixer channel volumes were turned off (or down to where I couldn't here anything). So be sure to have all of those turned up and not muted.

If you are not able to play audio like you were able to do on the live CD, then there was probably a configuration problem during the install of Kubuntu. I'm an amateur at linux so I don't know how to fix that, but some other people here might.

---

### Post by jamesje on 2009-09-07
Thank you for that. it was the mixer panel that was being a bit lame. That things can be so simple >.< xD thanks again!

---

