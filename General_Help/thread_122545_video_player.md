---
title: "video player"
date: 2006-01-27
forum: General Help
---

### Post by raul99 on 2006-01-27
I am new to linux and recently installed Ubuntu 5.10. The problem is inablity to 
get an internet video viewer working in firefox. I have tried to install totem and mplayer. When I click on the video link I get: 
"Totem could not play 'fd://0. There was no decoder found to handle the stream. You might need to install the corresponding plugins."
Any suggestions?

---

### Post by super on 2006-01-28
you also need to install the correct codecs for the video file you are trying to open.

[here are instructions on how to install the most commonly used codecs]("http://ubuntuguide.org/#codecs")

post back if you still have problems.

---

### Post by Perfect Storm on 2006-01-28
Just a reminder, the link is to an old version of ubuntu (5.04) and there's thing in there that might not work.

To OP.

```
sudo gedit /etc/apt/sources.list
```

enable universe and multiverse (remove the **#** infront of the lines, except where there's ##.

add also:

[b]## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free[/b]


```
sudo apt-get update
sudo apt-get install gstreamer0.8-plugins gstreamer0.8-lame gstreamer0.8-ffmpeg w32codecs lame sox ffmpeg mjpegtools vorbis-tools libdvdcss2 gstreamer0.8-plugins-multiverse avifile-divx-plugin avifile-mad-plugin avifile-mjpeg-plugin
gst-register-0.8

```

Now download mplayplug-in here: [http://www.ahacic.5gigs.com/ubuntu/mplayerplug-in_3.11-1_i386.deb](http://www.ahacic.5gigs.com/ubuntu/mplayerplug-in_3.11-1_i386.deb)

```
cd /where/you/saved/the/file
sudo dpkg -i mplayerplug-in_3.11-1_i386.deb

```

---

### Post by DiscoKiller on 2006-01-28
may i point out that no matter how hard i tried i could not get everything to work with video files until i came across automatix. seemed to do me a lot of good. all my media players work like a dream and ubuntu looks prettier than ever coz my graphics card works (at last).

sudo wget [http://beerorkid.com/automatix/automatix-ubuntu_4.4-2_i386.deb](http://beerorkid.com/automatix/automatix-ubuntu_4.4-2_i386.deb)
sudo dpkg -i automatix-ubuntu_4.4-2_i386.deb 

think thats it. there are a few problems i have noticed people complaining about automatix for example firefox can go a bit loopy but i`ve had no problems. 

have fun

 DK

---

