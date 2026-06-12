---
title: "Adobe Flash simple fix for choppiness!"
date: 2009-09-24
forum: General Help
---

### Post by DodgeV83 on 2009-09-24
I posted this on the 64bit forums, but it should apply to all Ubuntu (maybe even all Linux) users.

It seemed no matter what I did, flash was incredibly choppy on my dual-core recent Dell laptop. I had simply given up lately and decided it was just something I'd have to deal with as long as I was with Linux. This was a contributing factor to me dropping Linux for Windows a while back, but I figured I could do without flash videos...

Well today I had enough and looked again for a solution. I noticed the video was noticeably better when the laptop is plugged in, even though choppiness was still abundant enough to make me simply not want to watch any flash videos full-screen.

After trying all the beta NVidia drivers and everything else on the forums, I never thought to check my CPU.

My research brought me here:

[http://maketecheasier.com/how-to-control-your-cpu-frequency-in-ubuntu/2009/04/10](http://maketecheasier.com/how-to-control-your-cpu-frequency-in-ubuntu/2009/04/10)

I simply added the **Gnome CPU Frequency Scaling Monitor** to my panel and set it to as high as it goes, 2.4GHZ.

FLASH IS PERFECT NOW!

I hope this helps someone out!

Edit:  Found another factor.  Even after this "fix", it gets completely choppy again (unwatchable for me) after going into **suspend mode** and coming back.  Going into Hibernate mode does not have this effect.  **No more suspend mode for me!**

---

### Post by slimdizzy on 2009-09-24
I get a "Page Not Found" error trying to access that site.  Mirror or other link?

---

### Post by Bucky Ball on 2009-09-24
> **slimdizzy said:**
> I get a "Page Not Found" error trying to access that site.  Mirror or other link?

+1

Yep, page not found.

---

### Post by NoaHall on 2009-09-24
Right click panel -> Add to panel -> CPU Frequency monitor
Left click on the CPU, change frequency up or down.

Also see in my sig for better, proper 64 bit flash.

---

### Post by DodgeV83 on 2009-09-24
hmm, the copy/paste of my previous post messed up the link!

[http://maketecheasier.com/how-to-control-your-cpu-frequency-in-ubuntu/2009/04/10](http://maketecheasier.com/how-to-control-your-cpu-frequency-in-ubuntu/2009/04/10)

---

### Post by DodgeV83 on 2009-09-25
Found another factor.  Even after this "fix", it gets completely choppy again (unwatchable for me) after going into **suspend mode** and coming back.  Going into Hibernate mode does not have this effect.  **No more suspend mode for me!**

---

### Post by Khakilang on 2009-09-25
Try that but say "Frequency Scaling Unsupported 1.59GHz (100%)". Its say it don't have the drivers to support. But its good to experiment. Thank for sharing.

---

### Post by maximalistic on 2009-09-25
wow so easy! have my cpus been running at 1ghz instead of 3ghz all this time!?

---

### Post by Rumpty on 2009-09-25
> **maximalistic said:**
> wow so easy! have my cpus been running at 1ghz instead of 3ghz all this time!?

No, they should have been speeding up "ondemand". That is the default setting, but apparently that setting is not agressive enough to keep Firefox fully up to the mark. I have read of (and tried) a change to made the CPU speed-up cut in earlier.

---

### Post by cottfcfan on 2009-09-25
I`m using a Dell 531 inspiron, and had the same problem.
 What worked for me, was entering setup at boot and disabling the AMD "cool & quiet" function.
 Watching Flash Video after that, CPU dropped by about 40% and video was perfect.

---

### Post by Rumpty on 2009-09-25
It's a pity to disable the Cool and Quiet function though. It is a good feature, saves power and heating. In Ubuntu, my computer consumes 70 watts when it is sitting doing nothing, and 100 watts when it is very busy. I guess that is the cool and quiet working?

Have a look at 
[http://allredb.wordpress.com/2009/05/07/speed-up-flash-and-firefox-in-ubuntu-jaunty-904/](http://allredb.wordpress.com/2009/05/07/speed-up-flash-and-firefox-in-ubuntu-jaunty-904/)
for a useful tip, and you can keep the Cool & Quiet as well.

---

