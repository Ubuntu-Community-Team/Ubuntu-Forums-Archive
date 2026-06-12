---
title: "Terminal Player?"
date: 2009-09-18
forum: General Help
---

### Post by rocket16 on 2009-09-18
Hello to everybody here. I was wondering, is there a way we can play videos using MPlayer in Terminal without using XWindow Output? I mean, suppose we are in a Virtual Console. Then, if we use the Command mplayer /path/to/file.extension, the Video will not be displayed, but the audio will be heard. But can we somehow display the Video in the terminal itself?

---

### Post by Partyboi2 on 2009-09-18
You should be able to use something like
```
mplayer -vo caca  /path/to/file.mpg
```

---

### Post by rocket16 on 2009-09-18
Thanks but that doesn't any visual output. That displays only the numbers on the Screenshots.

---

### Post by andrew.46 on 2009-09-18
Hi rocket,

> **rocket16 said:**
> Hello to everybody here. I was wondering, is there a way we can play videos using MPlayer in Terminal without using XWindow Output?

I suspect you are referring to playback via a framebuffer device which I will admit I have never been able to get running :(. Some info from the gentoo world here:

Mplayer on Framebuffer
[http://en.gentoo-wiki.com/wiki/Mplayer_on_Framebuffer](http://en.gentoo-wiki.com/wiki/Mplayer_on_Framebuffer)

If you can get it working it would be nice to see the details, I have tried several times!

Andrew

---

### Post by rocket16 on 2009-09-18
Thanks Andrew. I think it will help me alot.

---

### Post by Partyboi2 on 2009-09-18
delete

---

### Post by andrew.46 on 2009-09-18
Hi rocket,

> **rocket16 said:**
> Thanks Andrew. I think it will help me alot.

Well I hope so, it still burns a little that I cannot get it running myself :). BTW if you were interested in investigating the aa and caca output that my colleague Partyboi mentioned have a look at tip no. 6 in the following guide:

Top 10 Tricks and Tips for the svn MPlayer
[http://ubuntuforums.org/showthread.php?t=1154431](http://ubuntuforums.org/showthread.php?t=1154431)

where there is a little detail.

Andrew

---

### Post by mc4man on 2009-09-18
Using a -vo  of svga would always work, though never knew what the difference was (other than using a virtual terminal
ex
> svgalib: allocated virtual console #9]

I remember trying to read this about directfb because I've always seen it in some configures (actually couldnt read at all, copied the page out to text file.

Gave up about 1/2 way thru, didn't see to what end it was heading

[http://blog.mageprojects.com/2009/05/12/get-directfb-12-running-on-ubuntu-904-with-multi-app-support/](http://blog.mageprojects.com/2009/05/12/get-directfb-12-running-on-ubuntu-904-with-multi-app-support/)

---

### Post by andrew.46 on 2009-09-18
Hi mc4man,

> **mc4man said:**
> I remember trying to read this about directfb because I've always seen it in some configures (actually couldnt read at all, copied the page out to text file.

Gave up about 1/2 way thru, didn't see to what end it was heading

[http://blog.mageprojects.com/2009/05/12/get-directfb-12-running-on-ubuntu-904-with-multi-app-support/](http://blog.mageprojects.com/2009/05/12/get-directfb-12-running-on-ubuntu-904-with-multi-app-support/)

It all looks a little too hard, I will admit to being a commandline enthusiast but in 95% of the time I have X running.... And to add to the list of my shortcomings I could not get *-vo svga* running either :).

Andrew

---

### Post by mc4man on 2009-09-18
> could not get -vo svga running either

Whether it's the right thing to do or not, did you use sudo?

---

### Post by andrew.46 on 2009-09-18
Hi mc4man,

> **mc4man said:**
> Whether it's the right thing to do or not, did you use sudo?

Oops, you have caught me between Ubuntu installations so I have been using Slackware thus I tried both as ordinary user and also as full root account, with the understanding that this is discouraged under Ubuntu. Hmmmm..... I shall experiment...

**Edit:** Well partial success with svga. Only as root and only some videos with some messages about centering the image. I need to reload an Ubuntu system tonight....

Andrew

---

