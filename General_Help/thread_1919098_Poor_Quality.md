---
title: "Poor Quality"
date: 2012-02-02
forum: General Help
---

### Post by drtusharks on 2012-02-02
I am a Newbie to Ubuntu
Getting very poor video quality
Tried VLC, Banshee players
Using 
Lenovo Y430, 
Core2duo 2Gb Ram, 
NVIDIA 1Gb Graphics Card
LED Screen

Please Help regarding this or i would be forced to revert to Win Vista(urgh..)

---

### Post by Linux Dutchman on 2012-02-02
Take a look here: [https://sites.google.com/site/tipsandtricksforubuntu/multimedia/how-to-add-multimedia](https://sites.google.com/site/tipsandtricksforubuntu/multimedia/how-to-add-multimedia). It helpt me a lot to get multimedia up and running!

---

### Post by drmrgd on 2012-02-02
Have you added the Ubuntu Restricted Extras repository in the Software Center and installed the video codecs from there?  That may be what you're missing.

---

### Post by drtusharks on 2012-02-02
Will try now
Thanx

---

### Post by drtusharks on 2012-02-02
The quality is bit improved but still not upto the mark yet
I am watching HD videos and they appear like 3Gp mobile videos. But atleast there is color correction now.

---

### Post by WasMeHere on 2012-02-02
> **drtusharks said:**
> The quality is bit improved but still not upto the mark yet
I am watching HD videos and they appear like 3Gp mobile videos. But atleast there is color correction now.

Have a look at the following thread (where I was able to improve my video rendering)
[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showthread.php?t=1850462_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1850462")

---

### Post by drtusharks on 2012-02-02
I did this there is somewhat improvement. But There are still
 just too many pixels in the HD videos.

---

### Post by WasMeHere on 2012-02-02
> **drtusharks said:**
> I did this there is somewhat improvement. But There are still
 just too many pixels in the HD videos.

What about vdpau running mplayer from the command line?
```
alias mplayervdpau='mplayer -vo vdpau -vc ffh264vdpau'
```

---

### Post by drtusharks on 2012-02-02
can you please explain how to do this

---

### Post by WasMeHere on 2012-02-02
Have you ever used the 'terminal' also called 'command line interface'?

What version and flavour of Ubuntu are you running? 'Vanilla' Ubuntu 11.10 with Unity desktop environment, Kubuntu, Xubuntu or Lubuntu? Or an older version, Ubuntu 10.04 LTS?

In most versions, you press the three keys ***ctrl + alt + t*** to get a terminal windows on your desktop. Then you can type commands using your keyboard and press the ***Enter*** key to activate that command. If your video file is encoded with h.264, you can run vdpau (using the nvidia chip to decode the video) with the following command.
```
mplayer -vo vdpau -vc ffh264vdpau videofile.mp4
```
If you add the following line
```
alias mplayervdpau='mplayer -vo vdpau -vc ffh264vdpau'
```
at the end of your .bashrc file in your home directory, in the future you will be able to run such video files with the command

```
mplayervdpau videofile.mp4
```

You add that line with the editor gedit```
gedit ~/.bashrc
``` (copy and paste)

---

### Post by drtusharks on 2012-02-02
> **Olle Wiklund said:**
> Have you ever used the 'terminal' also called 'command line interface'?

What version and flavour of Ubuntu are you running? 'Vanilla' Ubuntu 11.10 with Unity desktop environment, Kubuntu, Xubuntu or Lubuntu? Or an older version, Ubuntu 10.04 LTS?

In most versions, you press the three keys ***ctrl + alt + t*** to get a terminal windows on your desktop. Then you can type commands using your keyboard and press the ***Enter*** key to activate that command. If your video file is encoded with h.264, you can run vdpau (using the nvidia chip to decode the video) with the following command.
```
mplayer -vo vdpau -vc ffh264vdpau videofile.mp4
```
If you add the following line
```
alias mplayervdpau='mplayer -vo vdpau -vc ffh264vdpau'
```
at the end of your .bashrc file in your home directory, in the future you will be able to run such video files with the command

```
mplayervdpau videofile.mp4
```

You add that line with the editor gedit```
gedit ~/.bashrc
``` (copy and paste)
was on ubuntu 11.10 when i started this thread. there was a update message so i just updated to ubuntu 12.04. But that didnt improve the video quality. Will try what you said in a while.

---

### Post by MG&amp;TL on 2012-02-02
Wait, please don't do that...

12.04 is VERY unstable, it will probably bork video-playing full stop, rather than make it better.

---

### Post by WasMeHere on 2012-02-03
> **MG&TL said:**
> Wait, please don't do that...

12.04 is VERY unstable, it will probably bork video-playing full stop, rather than make it better.
+1

I'd rather say go the other way, trying the present official version and ***older*** versions and/or other flavours: Kubuntu, Xubuntu or Lubuntu. Or try for example Linux Mint 11, which is based on Ubuntu. It is 'only' the user interface and the selection of installed programs, that differs from Ubuntu.

---

### Post by 3rdalbum on 2012-02-03
Why not try first things first: What graphics card do you have, and what driver are you using? If you've got an Nvidia card or a newer ATI card and have not activated the proprietary driver, then that's going to be the first step for you.

---

### Post by drtusharks on 2012-02-03
i did install 12.04. I was unaware that its still in alpha stage. But the video in which peoples skin looked purple coloured - some sort of color inversion thing was now ok. Only problem now is the pixellated video quality, although better that previous but less than windows vista. You still think i should install other versions of ubuntu?

---

### Post by Quarkrad on 2012-02-03
12.04 is not officially available until April 2012 as a stable release - at the moment it is being developed/tweaked/tested prior to being a stable release.  As such all sorts of things could/will/maybe change at any time.  You may well get your video set up, with help, and then a change could render it all back to square one - it not working.   You would be better off with either 11.04 or 11.10 that are formally supported and stable rather then 12.04 which it more of a future release.  See **[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Ubuntu_12.04_LTS_.28Precise_Pangolin.29](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Ubuntu_12.04_LTS_.28Precise_Pangolin.29)**  Unless of course you are part of the Testing team/group for 12.04 (apologies if you are) - but then your question would be in another section of this forum.

---

### Post by 3rdalbum on 2012-02-03
> **drtusharks said:**
> But the video in which peoples skin looked purple coloured - some sort of color inversion thing was now ok.

It would have been really helpful if you'd described this straight away rather than just saying "Poor quality". The "purple coloured" thing is a known problem that crops up in Nvidia graphics drivers from time to time, and it's easily worked around.

We could have had this thread wrapped up in five minutes, sadly.

Your screen resolution is correct? You're using the proprietary graphics drivers still? You're using VLC Media Player? What is the video output module that's enabled in the settings, and does it help to change it to X11, XVideo or VDPAU?

Please check all these things and then get back to me.

---

### Post by drtusharks on 2012-02-03
I have a Nvidia GeForce 9300M GS 256MB Graphics card.
Here is a screenshot of the video playing in VLC
I have not altered any setting from the VLC player.
I have NVIDIA graphics accelerator installed as additional driver in Ubuntu

---

