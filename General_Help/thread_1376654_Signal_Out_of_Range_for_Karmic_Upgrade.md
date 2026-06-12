---
title: "Signal Out of Range for Karmic Upgrade"
date: 2010-01-09
forum: General Help
---

### Post by shortsightedPenguin on 2010-01-09
Anyone knows the workaround for 
> 
Input Signal Out of Range Change Settings to 1440 x 900 - 60Hz


?

It happened after I upgraded from Jaunty to Karmic. Thanks.

---

### Post by dcstar on 2010-01-10
> **shortsightedPenguin said:**
> 
It happened after I upgraded from Jaunty to Karmic. Thanks.

It means your monitor is not being detected correctly, try and replace the /etc/X11/xorg.conf file with a default version.

---

### Post by shortsightedPenguin on 2010-01-10
> **dcstar said:**
> It means your monitor is not being detected correctly, try and replace the /etc/X11/xorg.conf file with a default version.

Hi David, I have no idea what is the default value. I'm right now using Vista to find solution for it, and I just kinda looked everywhere to get help before booting in Karmic again. Will I also have the same path as 

```

/etc/X11/xorg.conf

```

?

Thanks.

---

### Post by shortsightedPenguin on 2010-01-16
I don't have the filename in /etc/x11/xorg.conf

Any cure for this? I have been using Vista for the past one week. I'm slightly disappointed by Karmic Koala. Haven't resolved the sound problem and now I can't even stay in Desktop for longer than a minute, due to Input Signal Out of Range.

---

### Post by jamesisin on 2010-01-16
I did find this post which may or may not be of use to you:

[http://ubuntuforums.org/showthread.php?t=1324239](http://ubuntuforums.org/showthread.php?t=1324239)

---

### Post by shortsightedPenguin on 2010-02-07
> **jamesisin said:**
> I did find this post which may or may not be of use to you:

[http://ubuntuforums.org/showthread.php?t=1324239](http://ubuntuforums.org/showthread.php?t=1324239)

Yeah, it works. Thanks. but it's kind of like in a jittering condition.

---

### Post by jamesisin on 2010-02-07
So that post fixed part of but not all of your problem?

---

### Post by shortsightedPenguin on 2010-02-08
> **jamesisin said:**
> So that post fixed part of but not all of your problem?

Yeah, I mean Karmic is giving me lost of hope. The sound isn't working. 

Back to this resolution, it works OK except it tends to display bulky resolution. It's heavier than before I'm not sure what is the problem. I had to re-do the steps after a major update ever since I stopped using for weeks. After redoing is fine now.

Constantly worrying about what to come next. 

Thanks for the link, it was a good exercise using linux. Good for education. :)

---

### Post by gradinaruvasile on 2010-02-08
What video card do you have?

I had this problem with nvidia gf 210. The solution was to install the proprietary drivers.

---

### Post by jamesisin on 2010-02-08
Take a look at this thread for audio/video solutions:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

and this one for solutions concerning PulseAudio:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by shortsightedPenguin on 2010-02-13
Hi Gentlemen, I'm not proceeding with the sound yet, because the resolution problem recur each time I restart the system. I'm using Vista at the moment. 

I will check back to see what the heck is the problem. I thought I fixed the resolution problem. But I " have " to do it each time I restart the system. That is creating the XORG file, and lines of codes. Weird really.

---

### Post by efflandt on 2010-02-13
You haven't mentioned what video card/chip you have or if you are using any special drivers for it.  X changed in 9.10 (which by default does not even have xorg.conf).  So maybe an old setting in xorg.conf is tripping you up.  You might just try renaming it to something like xorg.conf.old and see what happens without it.

If you are still booting a Jaunty kernel, sound will not work.  What does **uname -a** show for kernel version?  Even with a proper kernel, sound may be initially muted.  Does System > Preferences > Sound show something other than a Dummy device for Output?

---

