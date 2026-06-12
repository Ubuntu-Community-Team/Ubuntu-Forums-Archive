---
title: "Firefox not saving preferences"
date: 2009-07-30
forum: General Help
---

### Post by strungoutfan78 on 2009-07-30
Hi. Thought I would share a little incident I recently had.  Ever since installing Jaunty I've had issues with firefox not saving my preferences.  My home page would always revert to the Ubuntu start page as well as my rocker-gestures being disabled every time i started firefox.  Very annoying.  Simple solution.  Seems to be a file permission problem, so all I did was:

1.Go to my home directory

2.```
sudo chmod 0755 -R .firefox
```

Couldn't be easier and I hope maybe I help someone else out with this similar problem.:D

---

### Post by lovinglinux on 2009-07-30
For future reference...

See **Solution** [*[COLOR="Red"]**FOT001**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT001).

---

### Post by strungoutfan78 on 2009-07-31
Ummmm... thanks alot for the info.  I made sure to take a good look around to try and find any posts related to this topic with no luck.  I never get good results when I do searches in these forums.  Again, thank you.  Very informative.  I might give that flash tweak a try as well.

---

### Post by lovinglinux on 2009-07-31
> **strungoutfan78 said:**
> Ummmm... thanks alot for the info.  I made sure to take a good look around to try and find any posts related to this topic with no luck.  I never get good results when I do searches in these forums.  Again, thank you.  Very informative.  I might give that flash tweak a try as well.

[http://ubuntuforums.org/showthread.php?t=1219042](http://ubuntuforums.org/showthread.php?t=1219042)

---

### Post by strungoutfan78 on 2009-08-01
Wow.  Thanks a million.  I've installed both plugins and given them a brief test run and I like them both very much.  Why is it that an internal forum search yields such poor results though?

---

### Post by lovinglinux on 2009-08-01
> **strungoutfan78 said:**
> Wow.  Thanks a million.  I've installed both plugins and given them a brief test run and I like them both very much.  Why is it that an internal forum search yields such poor results though?

The internal search feature sucks. I don't know why. I use the Firefox search plugin from my signature.

---

