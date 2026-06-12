---
title: "Playing movies in firefox"
date: 2006-06-11
forum: General Help
---

### Post by Pilsner on 2006-06-11
Hello all.
My problem is that I cant watch movies in firefox.

I can watch but the sound lagg (works half second and then next half second) and the video is the same. Movie pausing and starting when playing.

I can download the movie and see perfect sound and video.

But not directly in firefox with the mplayer plugin

What do I do?

I have the "old" ubuntu 5.10

I have searched for this issue with keywords as "mplayer plugin firefox" "firefox movie plugin" and etc.

---

### Post by kaamos on 2006-06-11
Hello!

The mplayer plug-in in breezy is quite an old version. [This](http://www.ahacic.5gigs.com/ubuntu/mplayerplug-in_3.11-1_i386.deb) version does a much better job in my experience.

Just download the file and in a terminal:
```
sudo dpkg -i mplayerplug-in_3.11-1_i386.deb
```

About the versions:
- breezy default: 3.09 (I think..)
- the breezy deb linked above: 3.11
- dapper: 3.17

---

### Post by Pilsner on 2006-06-19
Today I have installed 6.06 (dapper?)
And it works good playing movies in firefox.

I have also ran the automatix script

---

