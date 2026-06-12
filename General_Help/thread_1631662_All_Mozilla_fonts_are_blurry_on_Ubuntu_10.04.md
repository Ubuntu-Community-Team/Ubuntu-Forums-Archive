---
title: "All Mozilla fonts are blurry on Ubuntu 10.04"
date: 2010-11-26
forum: General Help
---

### Post by kriukov on 2010-11-26
I have a new laptop where I had to install Ubuntu 10.04 (8.04 wouldn't boot). All Mozilla software that I use every day (Firefox, Thunderbird, Sunbird) has blurry fonts in 10.04, as opposed to 8.04 where all the fonts are clear. I remember that on 8.04, Thunderbird 2 has the same blurry fonts if I use the package from Mozilla's website, but the fonts are clean if I use the Thunderbird 2 from the repository. The fonts in the content rendering (mail, web pages) are also blurred in a similar fashion in 10.04. I attach here the menus from Firefox 4.0 beta 1 on 8.04 and 10.04. It can be seen on large zoom that the fonts are not only blurry, but slightly smaller in width.

---

### Post by lovinglinux on 2010-11-26
See the last item on [this list]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html").

---

### Post by Enigmapond on 2010-11-27
> **lovinglinux said:**
> See the last item on [this list]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html").

 I don't really have too much of a problem with the fonts in FF. I also don't have this file in my home directory. Should I create it?  Just curious..  Also I should note I'm testing the 4.0 and there's not a lot of problems there as well...I actually like the Tabs in it better..:)

---

### Post by kriukov on 2010-11-27
> **lovinglinux said:**
> See the last item on [this list]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html").

I've already seen and done this, but it didn't help.

---

### Post by kriukov on 2010-11-28
Noticed that this situation has already been discussed:

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/512561](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/512561)

Still found no solution to this...

---

### Post by kriukov on 2010-11-28
Solved. I enabled "Subpixel smoothing (LCDs)" and rebooted. If I just use "Best shapes" as before, Mozilla programs show the same ugly fonts.

---

