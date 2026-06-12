---
title: "Problem playing full screen flash movies"
date: 2012-06-03
forum: General Help
---

### Post by NautiusMaximus on 2012-06-03
I have a brand new Ubuntu 12.04 system, and I'm having problems watching flash movies (eg on YouTube) in full screen. If I watch at original size it's fine, but full screen becomes very poor quality, looking like it's dropping a great many frames. It's also difficult to get out of full screen by pressing escape in the normal way. It works after a while, but not until pressing escape many times.

This seems to be a well known problem, but sadly not with such well known solutions. I found this thread:

[http://ubuntuforums.org/showthread.php?t=1593363](http://ubuntuforums.org/showthread.php?t=1593363)

which seems to be the same problem, but the solution that seemed to work for most folks on that thread, linked to at 

[http://www.noobrescue.com/blog/flash-fullscreen-doesnt-work-on-ubuntu-10-10](http://www.noobrescue.com/blog/flash-fullscreen-doesnt-work-on-ubuntu-10-10)

didn't work for me.

If I view fullscreen movies on YouTube in html5, then they work just fine. If I watch movies at original size on YouTube in flash, then they work just fine. It's just fullscreen movies in flash that don't work.

I have a 64 bit system, using the latest version of Chrome browser (Version 19.0.1084.52) with its built-in flash player. I have an NVidia graphics card.

Any ideas?

Thanks
NM

---

### Post by Paddy Landau on 2012-06-03
How well do the videos work when using Firefox?

I know that Adobe Flash does cause some problems with some hardware, because of a lack of support. If you're happy to go with Firefox, you can use the add-on Flash Aid to help get your Flash working properly.

---

### Post by NautiusMaximus on 2012-06-04
Thanks for that, Paddy.

I tried viewing the videos in Firefox, and it was just the same as in Chrome, ie dreadful.

I tried using Flash Aid as you suggested, but it didn't make much difference.

Anything else I could try?

---

### Post by Paddy Landau on 2012-06-04
Sorry, at this point I don't know what else you could do.

---

### Post by inashdeen on 2012-06-04
Have you tried changing its resolution. well, if on youtube, there is a gear icon to change em. maybe that is the problem ???

---

### Post by NautiusMaximus on 2012-06-04
Yes, I've tried at various resolutions from very low-res up to 1080. Result is the same each time.

---

### Post by GreatDanton on 2012-06-04
Could you post your computer configuration?

---

### Post by inashdeen on 2012-06-04
Do this fix em?
[http://www.youtube.com/watch?v=Z6xnPaL4h70]("http://www.youtube.com/watch?v=Z6xnPaL4h70")

---

### Post by NautiusMaximus on 2012-06-05
Thanks for the suggestions.

@GreatDanton:

My configuration is this:
CPU: AMD Phenom II X4 965
Motherboard: Gigabyte 990XA-UD3 
Graphics card: Nvidia Geforce FX 6200
RAM: 8 GB
SSD drive for root partition: Crucial M4 128GB
HDD for home partition: Western Digital Caviar 2TB

I think that's everything of relevance, let me know if I missed anything.

@inashdeen:

No, it didn't fix anything. The flash settings, bizarrely, didn't work (ie clicking on the settings window didn't do anything) in normal mode, but I could change it in full screen mode! Unticking the hardware acceleration box didn't change anything.

Also tried clearing my cache as per one of the comments there. Again, no joy.

---

### Post by Paddy Landau on 2012-06-05
> **NautiusMaximus said:**
> Unticking the hardware acceleration box didn't change anything.
You may have to log out and in again to register the change. Please try that after unticking the box.

---

### Post by NautiusMaximus on 2012-06-05
> **Paddy Landau said:**
> You may have to log out and in again to register the change. Please try that after unticking the box.

Tried that. Even tried rebooting the whole computer. Still no joy.

---

### Post by sanukcm on 2012-07-01
See my post on page 2 of this thread: [http://ubuntuforums.org/showthread.php?t=2011839&page=2](http://ubuntuforums.org/showthread.php?t=2011839&page=2)

Fixed my flash / chrome problems after upgrading to 12.04.

Hope this helps.

---

