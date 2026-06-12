---
title: "Can a second HDD improve boot time and access times ?"
date: 2010-06-26
forum: General Help
---

### Post by the8thstar on 2010-06-26
Hello,

I managed to install a second hand 10Gb HDD on my old P4. I want to see how I can use this extra disk to speed up Ubuntu 10.04 if possible.

I installed my swap onto this second drive but since I never use swap I can't see any real improvement. Next, I'm considering the creation of a new partition on that disk that would handle /tmp. Could that improve access times?

Finally, what other tricks could I use with this 2nd HDD to speed things up?

Thanks for your help and feedback.

---

### Post by Leppie on 2010-06-26
you could put /var on there as well.
have you checked with drive has the lowest access time?

---

### Post by the8thstar on 2010-06-27
What command can I use to check that?

---

### Post by btechcs on 2010-06-27
I don't think using /var on a different partition disk will fetch you significant speedup. 

BTW, to check the access times use:
 ```
sudo hdparm -t /dev/hda
```

---

### Post by dabl on 2010-06-27
You can add the -T option to the command that btechcs wrote, to get the timing out of cache, so 

```
sudo hdparm -tT /dev/hda
```

But, it is not likely that such a hard drive will make any difference -- it sounds like ~1997 drive technology.  A new fast hard drive would speed up booting.  After that, more memory, and a few tweaks like [[COLOR="Green"]**these**[/COLOR]](http://rudd-o.com/en/linux-and-free-software/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that) are about the best you'll be able to do. For on-screen responsiveness, a fast video card with reasonable memory will help.

---

### Post by cascade9 on 2010-06-28
I would go quite as far back as 1997 (IIRC, 8GB was about the biggest drive you could get back then) but its not much newer than that I would guess. 

IMO, adding an older, slower HDD wont help...and putting /tmp or /var on there might just make thinsg slower, even if the access times is the similar (which it wont be for a drive that old). The transfer rate from older HDDs is so much lower that it could well take longer to access files. 

BTW, I think you are sort-of right about "For on-screen responsiveness, a fast video card with reasonable memory will help" dabl, but anything from the last few years is more than enough. Or any decent card from this century.

I've got...er...had till it died, a GF4MX440, a 2002 card, and there is no difference for desktop use between that and the much newer cards I've run. The only time it might make a difference is at high resolutions. At 1024 x768, 1280x960 or 1280x1024 the MX440 is fine, but it is a bit sluggish at 1920x1440.

---

### Post by dino99 on 2010-06-28
the more hardware you install, the more slower you get

dont dream about a 10 gb, what do you expect ? :lolflag:

---

