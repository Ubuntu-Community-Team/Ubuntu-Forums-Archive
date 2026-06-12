---
title: "help needed"
date: 2011-05-15
forum: General Help
---

### Post by girishyem1975 on 2011-05-15
help needed>>>

1) i instld ubuntu 11.04 but the message
" it seems that you do not have the hardware requird to run unity 
please choose ubuntu classic..."comes aftr installation..
whts the requird hardware cofiguration to run ubuntu unity???

2) when playing videos in any player ( banshee ,vlc ..) the system restarts..
i can't play videos in ubuntu11.04 .whats the reason?
system restarts when trying to make some changes in player ( ie, 
enlarge windows, forword videos etc..)

all other things are perfect ...

hope your comments wll help me..

---

### Post by Quackers on 2011-05-15
It may be that you need addiational graphics drivers to run unity.
Have you run System > Admin > Additional Drivers?

---

### Post by 3rdalbum on 2011-05-15
What graphics chipset do you have in your computer?

```
lspci
```

should tell you.

If it's anything other than ATI, Nvidia or Intel then you'll probably not be able to run Unity due to a lack of drivers (oh, and anything other than ATI or Nvidia is probably not very good anyway).

I'd say that the video playback problem is linked to the graphics driver, too. If you can't get a better driver for your graphics, then you might want to go into the VLC preferences and change the video output module. Change it from Xvideo to X11, or vice-versa.

---

