---
title: "Volume difference from Ubuntu"
date: 2011-04-26
forum: General Help
---

### Post by Rayray333 on 2011-04-26
Just wondering if anyone else experienced this. I have been using Ubuntu for half a year now and I love it. I just installed Kubuntu Desktop to try it out and I found that I can't get near as high volume with it than I do with Ubuntu. Ubuntu is even waaaay louder than the Windows that used to be on here.

So why is there a change in the max of volume? I am a huge music person and that is the only thing holding me back from getting rid of gnome. I like how fresh and clean KDE is. Any suggestions or info?

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

---

### Post by Drone4four on 2011-04-26
Try using alsamixer at the command line and adjust all the settings to the max:
```
sudo alsamixer
```

---

### Post by Rayray333 on 2011-04-26
Yah I did that, Master and PCM is all the way up with the same results.

---

