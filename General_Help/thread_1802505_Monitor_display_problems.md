---
title: "Monitor display problems"
date: 2011-07-12
forum: General Help
---

### Post by mkwn on 2011-07-12
I decided to set up a home theater using ubuntu, to replace windows 7 that was previously installed. However when I connected to my (no-name) TV with HDMI, I was getting "unknown signal" on my TV. I eventually managed to fix this by adding "nomodeset" to my GRUB config.

Now my problem is that my TV is not detected by Ubuntu and as a result the maximum resolution available is 1024x768. The display looks very blurry and stretched, and I think the color depth is too low as well. I have tried a number of fixes from other threads, but have been unsuccessful.

In case it's relevant, here's the graphics hardware I have:
```
$ lspci|grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

```I have tried to create an xorg.conf on the suggestion from [this page]("http://brainstorm.ubuntu.com/idea/18331/"), but all it did was reduce the amount of resolutions available to *only* 1024x768. I have also tried to use "xrandr" to create a new resolution mode, with almost exactly the same results as [this thread]("http://ubuntuforums.org/showthread.php?t=1594308") (I get some error "Failed to get size of gamma for output default" and if I ignore the error I can make the resolution appear in the ubuntu monitor settings, though when I try to select it I get a warning that the resolution is out of range for my monitor.)

Can anyone offer some advice on what I can do? At this resolution it makes a terrible home theater, and if I can't find a solution I will be forced to switch back to Windows.

Thanks,
Matt

---

### Post by Bucky Ball on 2011-07-12
What release are you using and how are you connecting to the TV? Mythbuntu you should probably have a look at for this:

[http://www.mythbuntu.org/](http://www.mythbuntu.org/)

It is designed for what you are attempting.

---

### Post by wildmanne39 on 2011-07-12
Hi, you might have a look at this guide it looks easier to understand to me. 
[http://grenage.com/xorg.html](http://grenage.com/xorg.html)

---

### Post by mkwn on 2011-07-12
Thanks for the quick replies.

I'm using 11.04 Natty, and I'm connecting with a DVI to HDMI adapter. My understanding is that Mythbuntu is a collection of useful tools and such for a home theater, but it shouldn't make a difference in terms of low-level display setup. I'm happy to install mythTV and such myself. Am I correct in this?

With wildmanne's link, I was able to get a list of supported resolutions, however I know my monitor and adapter are capable of more because I had 1920x1080 on Windows. Making the outlined changes to xorg.conf had no effect.

---

