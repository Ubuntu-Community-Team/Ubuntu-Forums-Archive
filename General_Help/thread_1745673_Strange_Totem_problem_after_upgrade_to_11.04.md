---
title: "Strange Totem problem after upgrade to 11.04"
date: 2011-05-01
forum: General Help
---

### Post by BoPe86 on 2011-05-01
Hi! I have just upgraded my Ubuntu, but there's a strange problem when i try to play any mp3 file using Totem - Totam can't seek the song, you know - i can't play it from some random position. Mp3 song is acting like...well internet stream!

When i play a movie using Totem everything is fine, when i play a mp3 file (any mp3 file) using VLC everything is fine but Totem + mp3 = problem. Can anyone help me?

Totem version is 2.32.0

Tnx!

---

### Post by BoPe86 on 2011-05-01
HA! This problem is solved! While waiting for answer i did some digging and found:[this]("https://bugs.launchpad.net/ubuntu/+source/totem/+bug/750290")

It's a problem with Gstreamer, look at the last post ;)

---

### Post by alexsmith on 2011-05-11
For the impatient, the link above takes you to this (which solved my problem too):

```
sudo apt-get remove gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly
sudo apt-get install gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-fluendo-plugins-mp3-partner

```

BTW, I'm running Ubuntu 11.04 - the Natty Narwhal.

Thanks a lot!

---

### Post by jdorenbush on 2011-05-13
> **alexsmith said:**
> For the impatient, the link above takes you to this (which solved my problem too):

```
sudo apt-get remove gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly
sudo apt-get install gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-fluendo-plugins-mp3-partner

```

BTW, I'm running Ubuntu 11.04 - the Natty Narwhal.

Thanks a lot!

This fix worked for me. Thanks

---

### Post by fig_wright on 2011-05-29
Sweet, worked for me too. What a wierd problem.

---

### Post by aextance on 2011-05-31
I also had the same problem, but using those terminal commands wouldn't install gstreamer0.10-fluendo-plugins-mp3-partner. I looked up fluendo in synaptic and installed the plugin that I found there, and now I can seek in my MP3s. A major relief, as this is one of the most important tools I use in Ubuntu for my work! Thanks BoPe86 and alexsmith for the info.

---

### Post by geek11 on 2011-08-18
> sudo apt-get remove gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly sudo apt-get install gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-fluendo-plugins-mp3-partner
the fix worked very well 
thanks a lot :)

---

