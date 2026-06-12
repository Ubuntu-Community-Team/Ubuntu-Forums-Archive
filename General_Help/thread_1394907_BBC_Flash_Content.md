---
title: "BBC Flash Content"
date: 2010-01-31
forum: General Help
---

### Post by thephant0m on 2010-01-31
Hi all
I am using 9.10, fully updated as of the time of writing. Is anyone else having issues watching flash video content on BBC websites (this includes video on news.bbc.co.uk as well as programs on the iPlayer site).
 
The video window loads normally in the web page and a static image can be seen with the play button, however when I click on the play button nothing happens at all - the play button stays visible and the video does not play.
 
Flash content on all other sites works fine.
 
I have done various things in an attempt to resolve - like installing Adobe Air, as well as the standalone iPlayer application - still doesn't work.
 
Any ideas?
 
Thanks.

---

### Post by HomoGleek on 2010-01-31
> **thephant0m said:**
> Hi all
I am using 9.10, fully updated as of the time of writing. Is anyone else having issues watching flash video content on BBC websites (this includes video on news.bbc.co.uk as well as programs on the iPlayer site).
 
The video window loads normally in the web page and a static image can be seen with the play button, however when I click on the play button nothing happens at all - the play button stays visible and the video does not play.
 
Flash content on all other sites works fine.
 
I have done various things in an attempt to resolve - like installing Adobe Air, as well as the standalone iPlayer application - still doesn't work.
 
Any ideas?
 
Thanks.
iPlayer works for me, using Adobe Flash 10, Chrome and Karmic

---

### Post by Swagman on 2010-01-31
Justed tested it, mate.

No probs in Ubuntu i386 on 9:10

[**ScreenGrab**](http://www.upload3r.com/serve/310110/1264939595.png)

---

### Post by thephant0m on 2010-01-31
It's incredibly frustrating. It appears NOT to be an issue with player the content itself - it seems to be the controls on the BBC flash players that is the issue (i.e. the play/pause/skip buttons).

Certain BBC news web pages contain flash video footage that will start playing automatically when you click the story (i.e. from the 'most watched/listened' to links) - and this plays fine. However if I try to pause/skip that content, the buttons do not work, they just click and... nothing.

Hence on iPlayer content, which does not play automatically as soon you visit the page, I cannot get the video to start playing.

This is one area in Ubuntu that has given me headaches from day one... Flash content. I realise it's not the Project's fault, it's most likely Adobe or the BBC, but it makes the web experience on Ubuntu less than ideal.

---

### Post by Swagman on 2010-01-31
Ok.. I just paused & skipped ahead.

Mate.. It works ok.

Are you using 64 bit or 32 ?

Oh.. nVidia or aTi ?  I'm using a nVidia GTX 8800

---

### Post by thephant0m on 2010-01-31
I'm using 64-bit, ATI Radeon 4570.
 
I've tried uninstalling and installing the flashplayer-nonfree (and associated) packages, no luck. I have even installed the 64-bit Alpha flash plugin from Adobe, no luck. I've tried on Firefox and Chrome. It's just the BBC that's the issue!
 
I've resorted to using get-iplayer to stream content, which is an excellent utility in itself, but it's command line driven. I'm no stranger to the command line, nor have any hostility towards it - I've been working professionally on *NIX for 10 years now, but it's not the most elegant, flexible or usable solution for the non-technical members of my family for whom a the web based player is the only option.

---

### Post by cagey5 on 2010-01-31
I have similar problems with Jaunty. I upgraded to Karmic in the hope it would be resolved but no difference plus other problems promptedf me back to Jaunty.

With me the problem is the video content plays without problem 80% of the time then occasionally it seems to stall during the transfer of data stage and never actually play. Firefox then locks up and I have to force quit.

Normally a re-boot gets it working again, but sometimes I have to boot 2 or 3 times before it works, which I find very strange.

Bottom line, I'm interested in finding a solution for this too.

AMD 64

---

### Post by philinux on 2010-01-31
> **thephant0m said:**
> I'm using 64-bit, ATI Radeon 4570.
 
I've tried uninstalling and installing the flashplayer-nonfree (and associated) packages, no luck. I have even installed the 64-bit Alpha flash plugin from Adobe, no luck. I've tried on Firefox and Chrome. It's just the BBC that's the issue!
 
I've resorted to using get-iplayer to stream content, which is an excellent utility in itself, but it's command line driven. I'm no stranger to the command line, nor have any hostility towards it - I've been working professionally on *NIX for 10 years now, but it's not the most elegant, flexible or usable solution for the non-technical members of my family for whom a the web based player is the only option.

How did you install the 64 bit player, did you purge all other flash first.

I purged all flash from the system.
Check with
```
sudo updatedb
locate libflashplayer.so

```

Grabbed to 64 bit plugin from here.
[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz)
Extracted the libflashplayer.so to my desktop and then moved it to..
~/.mozilla/plugins

You have to create the plugins folder first.
Restart Firefox.

---

### Post by keithy on 2010-01-31
Try disabling compiz. works for me!

---

### Post by coldraven on 2010-01-31
I'm using 9.10 64bit with Flash 10.0.42.34 64bit and the BBC iPlayer works fine about 99% of the time. As I'm on a slow DSL I have to pause quite often, sometimes it crashes Firefox 3.5.7.

Also Compiz runs fine as well, spinny cubes and all :)

---

### Post by JoeWheeler on 2010-01-31
You could try clearing your internet cach. I had no end of problems with iPlayer at one point but then saw this suggestion on the iplayer website

Presuming you're using firefox go to tools > clear recent history > details  > check cache(and uncheck everything else!) > change last hour to everything> press clear

It seems a bit of a simple solution but it helped me!

---

### Post by HomoGleek on 2010-02-01
> **thephant0m said:**
> I'm using 64-bit, ATI Radeon 4570.
 
I've tried uninstalling and installing the flashplayer-nonfree (and associated) packages, no luck. I have even installed the 64-bit Alpha flash plugin from Adobe, no luck. I've tried on Firefox and Chrome. It's just the BBC that's the issue!
 
I've resorted to using get-iplayer to stream content, which is an excellent utility in itself, but it's command line driven. I'm no stranger to the command line, nor have any hostility towards it - I've been working professionally on *NIX for 10 years now, but it's not the most elegant, flexible or usable solution for the non-technical members of my family for whom a the web based player is the only option.
Have you seen [http://linuxcentre.net/getiplayer/get_iplayer-pvr-manager?](http://linuxcentre.net/getiplayer/get_iplayer-pvr-manager?)

---

### Post by thephant0m on 2010-02-01
JoeWheeler - thanks, bizarrely clearing the cache in Firefox allowed the flash video to play from iplayer, which wasn't working before, but the controls (pause/skip) still do not function. It's inexplicable to me at the moment.

However I am messing around with get_iplayer more and it's working really great for me - I love the power behind the plethora of options. And for the others I will use HomoGleek's excellent recommendation of Web PVR, which looks good - thanks for that.

---

