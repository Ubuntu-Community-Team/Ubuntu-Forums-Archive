---
title: "Video is all blue"
date: 2006-04-08
forum: General Help
---

### Post by Mortuis on 2006-04-08
For some strange reason today, all my video's are showing up with a blue screen.  Embedded video on webpages (ran with MPlayer) as well as video I try to run in VLC Players and Totem.  The only time I can get video to work is by running it in MPlayer from my hard drive, and then I can't resize the video.

Videos from google video and youtube seem to work, but I think they convert their movies to flash or something.

The only thing I can think of doing between when it worked correctly and this blue stuff was installing Diablo II on Wine and setting the sound driver in winecfg to ALSA, I doubt that has anything to do with it but I can't think of changing anything else.

---

### Post by encompass on 2006-04-08
I would play with what drive mplayer is trying to use for the video... at the least the is the xv or x11 or somehting to that effect that is a software based option to make the image show up.  Hope that helps... I had a very similar error with totem-gstreamer and moving to totem-xine fixed it all up.  Hope that help.
Yeah, rightclick and goto prefferences and slecte video select x11 or xv  try those... but besure to restart mplay before you try.

---

### Post by takayuki on 2006-04-10
i've got the same blue screen after a month of playing back video with no problems.    i recently got video playing in firefox via mplayer...

anybody got a fix for this?

thanks for any assistance.

---

### Post by takayuki on 2006-04-10
i've got a fix, sort of... (this worked for me...)


1.  go to System > Preferences > MultiMedia Systems Selector, then click the Video tab, then change the Default Sink Output to Custom, then close the window.

2.  now try playing a video in totem or vlc.  if it works, great.  if it doesn't, repeat step one and try SDL or another option.

hope this helps.  thanks to encompass for pointing me in the right direction.

takayuki

---

### Post by uderman on 2007-10-22
Hello.

I was having the same problem. Take a look at this link:

[https://answers.launchpad.net/ubuntu/+source/totem/+question/7373](https://answers.launchpad.net/ubuntu/+source/totem/+question/7373)

Felipe Uderman

---

