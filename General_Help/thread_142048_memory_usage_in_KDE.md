---
title: "memory usage in KDE"
date: 2006-03-09
forum: General Help
---

### Post by m.musashi on 2006-03-09
I found KInfoCenter yesterday and was surprised to see my physical memory usage at around 65% (35% free) with no apps running. True, I had some things running but closed them. Today, I boot up and check I'm at 35% usage with nothing (except info center) running. 20% is for disk Cache. What is that? I have a swap partition too (100% free). Is this normal usage? Why was so much still in use yesterday even after closing apps?

---

### Post by aysiu on 2006-03-09
Does it affect performance noticeably? That is, can you actually feel things moving more slowly?

---

### Post by retsaw on 2006-03-09
Was the memory usage you are quoting including the cache?  You should really ignore the cache for the purpose of how much memory is being used.

The disk cache is basically a copy of as many of the most recent disk reads you have memory for.  The linux kernel caches very aggresively as long as you have free memory which speeds things up if you need to read the same data again, after all what is the point of having lots of RAM if you don't use it.  This cache will be freed if there is any applications actually need the memory otherwise it will stay there.  All it really is, is the linux kernel making the best use of the RAM you have available.

---

### Post by m.musashi on 2006-03-09
[QUOTE=aysiu]Does it affect performance noticeably? That is, can you actually feel things moving more slowly?[/QUOTE]
Not really, but then again it never felt over fast to begin with. I have to say I don't get all the comments about how much faster linux is than XP. If anything, it feels slower but I've only used gnome and kde. Am I doing something wrong?

---

### Post by m.musashi on 2006-03-09
[QUOTE=retsaw]Was the memory usage you are quoting including the cache?  You should really ignore the cache for the purpose of how much memory is being used.

The disk cache is basically a copy of as many of the most recent disk reads you have memory for.  The linux kernel caches very aggresively as long as you have free memory which speeds things up if you need to read the same data again, after all what is the point of having lots of RAM if you don't use it.  This cache will be freed if there is any applications actually need the memory otherwise it will stay there.  All it really is, is the linux kernel making the best use of the RAM you have available.[/QUOTE]
It was in reference to free physical memory which included the disk cache. I just opened Oo.o and closed it. The disk cash jumped and then didn't empty but I still have 57% free. I can see the point of keeping things cached but Oo.o doesn't open that much faster the second time around. Of course, as you say, if you have free memory might as well use it.

---

### Post by aysiu on 2006-03-09
[QUOTE=m.musashi]Not really, but then again it never felt over fast to begin with. I have to say I don't get all the comments about how much faster linux is than XP. If anything, it feels slower but I've only used gnome and kde. Am I doing something wrong?[/QUOTE] I don't think it makes sense to say Linux "is" slower or faster. It really all depends on what you have running. XFCE and IceWM will always be faster than Windows. KDE and Gnome *can* be, depending on what services you have running and how many visual effects you have.

---

### Post by m.musashi on 2006-03-09
[QUOTE=aysiu]I don't think it makes sense to say Linux "is" slower or faster. It really all depends on what you have running. XFCE and IceWM will always be faster than Windows. KDE and Gnome *can* be, depending on what services you have running and how many visual effects you have.[/QUOTE]
Well, I'm usually a one app a time person. I might have a simple solitaire type game going while doing something in the background (writing a CD/DVD or installing something). I don't usually work on an office document, while burning DVDs, with a photo open for editing, as I download some large file. I might do a bit if I'm taking something from one place and using it in another. Otherwise it's just one at a time (might have firefox open though).

I'm not complaining or anything. It's isn't overly slow. Just doesn't seem faster as per my work habits.

---

### Post by ComplexNumber on 2006-03-09
i often found that KDE was a huge resource hog when not running any applications.

---

### Post by aysiu on 2006-03-09
Here's what I did to speed up KDE: KMenu > System > Konsole ```
sudo apt-get update
sudo apt-get install kpersonalizer
``` Alt-F2 ```
kpersonalizer
``` For effects, choose to remove all effects except desktop background and image previews.

---

