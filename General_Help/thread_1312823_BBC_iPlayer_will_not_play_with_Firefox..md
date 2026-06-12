---
title: "BBC iPlayer will not play with Firefox."
date: 2009-11-03
forum: General Help
---

### Post by Scunnered on 2009-11-03
Having installed :

1. Mozilla-mplayer
2. Flashplugin-nonfree
3. Ubuntu restricted extras

I find that I can't view the iPlayer.  This worked a treat when using 9.04 and strangely enough using Opera 10 it will work.

Is anyone having a similar problem and can offer a solution to the problem.

It is most strange that I can listen to radio in 9.10 but not the iPlayer. I can view other UK TV channels view on demand.

---

### Post by sreilly on 2009-11-03
Hi,

Have you tried installing Adobe AIR?
I've just loaded 9.10 on my Acer One and installed the BBC Desktop straight off.

Failing that you could always try get_iplayer and download the progs first.

Steve

---

### Post by scouser73 on 2009-11-03
BBC iPlayer works without Adobe Air, the only time that you will need Adobe Air is if you download any programmes from the BBC iPlayer.

---

### Post by sreilly on 2009-11-03
Yep, ... and on my wee Acer Aspire One the iPlayer runs a lot jerkier than streaming through FF

---

### Post by starfunker on 2009-11-03
> **Scunnered said:**
> Having installed :

1. Mozilla-mplayer
2. Flashplugin-nonfree
3. Ubuntu restricted extras

I find that I can't view the iPlayer.  This worked a treat when using 9.04 and strangely enough using Opera 10 it will work.

Is anyone having a similar problem and can offer a solution to the problem.

It is most strange that I can listen to radio in 9.10 but not the iPlayer. I can view other UK TV channels view on demand.

Yep, I cannot use iplayer either, yet I can use 4od and youtube.  I'm also in Scotland.  Coincidence? :P

---

### Post by Scunnered on 2009-11-04
My thanks to you all for your replies.

It would appear that FF is not properly performing and needs looked at. I will keep looking for the required improvement but will still work with Opera.

I downloaded from [http://ftp.opera.com/pub/opera/linux/](http://ftp.opera.com/pub/opera/linux/) version 1010b1/ the 86_64 version opera_10.10.4672.gcc4.qt4_amd64.deb and without any messing about this worked straight away.  

If you know how I may wake up Mozilla to this problem please advise and I will follow through on this.  I am unsure what the best way for reporting this as it comes pre-packaged in Karmic. Is this a Ubuntu or Mozilla bug report situation?

Again my thanks

---

### Post by starfunker on 2009-11-04
I just pulled epiphany from the software centre.  iplayer works fine with it.  Epiphany is a pretty basic, though fast, web-browser.

---

### Post by alicemoon on 2009-11-04
I have been having similar problems on a 64 bit system - iplayer was working in Jaunty but would not run following the upgrade to karmic - when I downloaded the desktop iplayer I could view downloaded programmes but could not run any  streaming in firefox. I tried epiphany - it did not work however I can view no problem in Opera - I have no idea if this is a problem with the flash plugin or firefox itself.

---

### Post by gredawarha on 2009-11-05
Hello all

Not sure if this helps but I am running 9.10 64 bit.  My BBC iplayer was working fine until I activated advanced desktop effects then it would not work.

Tured them off and the iplayer worked fine.

Hope this information is of use

---

### Post by Scunnered on 2009-11-05
**gredawarha**

I had a look at your solution and by applying None in the visual effects it worked for me. I can now listen to radio and view TV.

My sincere thanks for your kind assistance.

---

### Post by Efaill on 2009-11-05
Turning off the effects fixed the non playing iplayer to for me on my laptop.

---

### Post by Scunnered on 2009-11-06
Strange goings on still.  I can now access the iPlayer properly but this morning when I clicked on to listen to Radio 4 at 07:30 I was told that the programme was not available at this time.

I immediately accessed Opera and listened to the programme.  Now at 08:40 I am listening on FF.   What a shambles. 

I had posted on a FF forum my original problem but await a response. Will add this to the pot when I do get one.

Will keep everyone posted

---

### Post by gredawarha on 2009-11-06
Your welcome, glad to help

---

### Post by jaycee23 on 2009-11-07
Had exactly same problem with FF 3.5.4

Opera works fine but not really used it much before.

Also turning off effects works.

Did think I had done something to my iPlayer installation and did it all over again.

Should have looked for this thread instead - would have saved some time!

:lolflag:

Thanks for the solution(s)

---

### Post by alicemoon on 2009-11-08
turning off effects made iplayer work in firefox for me as well -

---

### Post by Scunnered on 2009-11-08
I still await any reply from FF but looking at the posts we can now use iPlayer OK.
Up till yesterday I still could not listen to live radio.

However I dont know what is now going on but I can now listen to live radio & TV.

I think that I will now mark this as solved and again thank everyone for their contributions

---

### Post by mantid on 2009-11-09
I note that, using Ubuntu/9.10 (karmic) x86_64, I did not need to turn off all desktop effects.
Using CompizConfig settings manager I could simply untick the Video Playback option under Utilities and Flash worked once again under Firefox 3.5.4.

---

### Post by GavCity on 2009-11-17
Switching off the video playback option did not work for me but turning off effects did.

I did a bit more reading around though and came across [this post on the compiz list]("http://www.mail-archive.com/compiz@lists.launchpad.net/msg03479.html") which recommends the following remedy [from launchpad]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407/comments/163").

'           I forgot where I found this workaround, it worked on Karmic 64bits:
 Open terminal and enter:
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
 then add: "export GDK_NATIVE_WINDOWS=1" before the last line of text'

It works nicely here without having to disable effects.

---

### Post by Scunnered on 2009-11-18
**GavCity**

Thanks vm for your reply.  Your timimg was perfect or so I thought as I had just posted BBC iPlayer will not play with Firefox since update to 3.5.5.

As your post looked to be in the timescale of my post I followed this only to find that it would not work. Both live Radio & the iPlayer is possible but TV on iPlayer is no good.

I will refer to this link of yours on the 3.5.5 post and see if it gets me anywhere>

Again many thanks for your assistance.

---

### Post by GavCity on 2009-11-18
Cheers Scunnered. It is still all working for me with Firefox 3.5.5 on Karmic 64bit though.

---

### Post by Scunnered on 2009-11-19
**GavCity**

Like you I am using 64 bit and followi8ng your post I selected the normal effects and tried again.

Still no improvement.  I am giving up on FF and working with Opera as I am fed up with having to faff about to get something that worked perfectly to work again.

Again thanks for your post and if you know any good prayers say one for me.

---

