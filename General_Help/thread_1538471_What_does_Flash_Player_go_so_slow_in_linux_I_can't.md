---
title: "What does Flash Player go so slow in linux? I can't watch videos."
date: 2010-07-25
forum: General Help
---

### Post by princerameses on 2010-07-25
I have had linux under at least 4 computers, plus a bunch of live CDs.. Plenty of RAM, HD space,  decent video card, yet it goes impossibly slow. And freezes usually.

It worked perfectly fine on windows on the same computer. Why is flash so crappy on Linux? o_O 

It really makes the operating systems not so great...

Right now I'm on puppy 5. I tried to watch a video and failed. -_- and flash games go slow.

Is it like this for everyone? :/

---

### Post by mikewhatever on 2010-07-25
Yes, the Linux version of flash is inferior to that of Windows, but since flash is closed source, and developed by Adobe Inc, you should probably direct these questions at Adobe.
PS: According to Steve Jobs, flash is also far from perfect on OSX.
[http://www.apple.com/hotnews/thoughts-on-flash/](http://www.apple.com/hotnews/thoughts-on-flash/)

---

### Post by Jazzy_Jeff on 2010-07-25
I have never tried flash on puppy so I can't help you there. As for flash working in Ubuntu I have had no issues using it on 32 bit and 64 bit versions. I watch flash videos all the time from hulu.com and also youtube.

---

### Post by cloyd on 2010-07-25
In general, I'll echo what every one else says: Flash just doesn't work well in Linux. However, this helped me.
  	 	 	 	 	 	  [COLOR=#000080]_[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)_[/COLOR]

[COLOR=#000080][/COLOR]
Still, YouTube and other flash sites still work my processor hard and heat up my machine. Sometimes, if the video I want to watch is long (30-50 minutes), start it in Flash, pause it, and do something else. Before closing YouTube or switching to another video, I go to the temp folder and copy the flash video somewhere else. (It will be erased in temp folder when you close youtube or open a new video).  Then I watch it on Totem Movie Player or VLC. Neither works my processor so hard. Good luck. I wish I knew how to tell you to get another player to work with youtube and Hulu, etc.  Getting file in temp does not work with Hulu, but does with youtube.

---

### Post by lovinglinux on 2010-07-25
> **Jazzy_Jeff said:**
> I have never tried flash on puppy so I can't help you there. As for flash working in Ubuntu I have had no issues using it on 32 bit and 64 bit versions. I watch flash videos all the time from hulu.com and also youtube.

It works for me too, although CPU usage is high. That's why I develop an extension that allows to replace the flash object with another video object, so you can watch it with a less CPU intensive plugin. If you wanna try it, get [FlashVideoReplacer]("http://flvideoreplacer-extension.blogspot.com") from my site. Make sure you get version 1.0.3, since it fixes a problem with YouTube changing their code a couple of days ago.

Also make sure you have the proper video driver and clean up your CPU fan. See [Flash Optimization](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html)

BTW, flash was a nightmare when I had a single core P4 CPU.

---

### Post by lovinglinux on 2010-07-25
> **cloyd said:**
> In general, I'll echo what every one else says: Flash just doesn't work well in Linux. However, this helped me.
  	 	 	 	 	 	  [COLOR=#000080]_[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)_[/COLOR]

Also make sure you get the latest version, which is currently 1.0.9. That version is waiting for Mozilla to  review it. You can get it and see the changes between 1.0.5 and 1.0.9 [here](https://addons.mozilla.org/en-US/firefox/addon/161939/versions/).

---

### Post by Vaphell on 2010-07-25
that flash replacer is most impressive but i how do you force it not to wait for full download of the file? That is the case with youtube low and med quality, high tries to play right off the bat.

---

### Post by NFblaze on 2010-07-25
Yea, Flash is pretty lackluster on Linux.

You said you have plenty of RAM... Though, I bet you dont have a quadcore CPU. Ever since I've upgraded to quadcore flash is a helluva lot much better on Linux.

---

### Post by lovinglinux on 2010-07-25
> **Vaphell said:**
> that flash replacer is most impressive but i how do you force it not to wait for full download of the file? That is the case with youtube low and med quality, high tries to play right off the bat.

Depends on the plugin you are using. Some plugins seems to need to buffer the whole video, while others don't. The recommended one is [gecko-mediaplayer](apt:gecko-mediaplayer). It buffers a little then plays normally. You can also change the buffer size in mplayer config file.

I just tested [this video](http://www.youtube.com/watch?v=u7deClndzQw&feature=related) here and it took 11 seconds to buffer.

---

### Post by Vaphell on 2010-07-25
gecko-mediaplayer works better than totem, but there is one more thing. Clips start with flash 50% of the time and require force-reload to get the replacement.

---

### Post by lovinglinux on 2010-07-25
> **Vaphell said:**
> gecko-mediaplayer works better than totem, but there is one more thing. Clips start with flash 50% of the time and require force-reload to get the replacement.

When it does not find a suitable media, then it falls back to flash. Check the extension settings. If you change the YouTube settings it auto reloads.

Anyway, this is the first time I receive a report about forcing the page reload. I will disable NoScript to se if there is any difference.

---

### Post by lovinglinux on 2010-07-25
> **Vaphell said:**
> gecko-mediaplayer works better than totem, but there is one more thing. Clips start with flash 50% of the time and require force-reload to get the replacement.

Weird, because it works flawlessly here.

---

### Post by Vaphell on 2010-07-25
i did the middleclick-open the aquarium clip, close, repeat like 30 times (at different quality settings) and i got replacement 3 times. Apparently there is some race condition. I get the replacement more often or outright always when my cpu is taxed already. First youtube clip usually fails.

---

### Post by princerameses on 2010-07-25
> **lovinglinux said:**
> It works for me too, although CPU usage is high. That's why I develop an extension that allows to replace the flash object with another video object, so you can watch it with a less CPU intensive plugin. If you wanna try it, get [FlashVideoReplacer]("http://flvideoreplacer-extension.blogspot.com") from my site. Make sure you get version 1.0.3, since it fixes a problem with YouTube changing their code a couple of days ago.

Also make sure you have the proper video driver and clean up your CPU fan. See [Flash Optimization](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html)

BTW, flash was a nightmare when I had a single core P4 CPU.

Ok, I'm confused, now what? It just says: "Gxine video player" in white letters, no video. I open Gxine and it freezes/ crashes.

What am I supposed to do with this addon? 

I'm all for downloading videos and watching them on the default video player.

---

### Post by Vaphell on 2010-07-25
try to install gecko-mediaplayer package

---

### Post by lovinglinux on 2010-07-25
> **Vaphell said:**
> try to install gecko-mediaplayer package

Also make sure you have version1.0.3. Visit the pages below to test. It loads automatically, but you can disable on a per site basis, through the extension preferences.

[http://www.youtube.com/watch?v=u7deClndzQw&feature=related](http://www.youtube.com/watch?v=u7deClndzQw&feature=related)
[http://vimeo.com/5606758](http://vimeo.com/5606758)

---

### Post by Vaphell on 2010-07-25
that vimeo clip fails too 50% of the time :)

EDIT: ok, not 50%. more like 25%

---

### Post by linux18 on 2010-07-25
> **NFblaze said:**
> Yea, Flash is pretty lackluster on Linux.

You said you have plenty of RAM... Though, I bet you dont have a quadcore CPU. Ever since I've upgraded to quadcore flash is a helluva lot much better on Linux.
I've got 8 cores and flash is still bad

---

### Post by lovinglinux on 2010-07-25
> **Vaphell said:**
> that vimeo clip fails too 50% of the time :)

EDIT: ok, not 50%. more like 25%

Please try a clean FF profile. There must be something on your current profile messing with it, because I have tested it on several Firefox/Ubuntu versions and it works without issues.

---

### Post by princerameses on 2010-07-25
It's not working.. And yes, I got latest version. I think.

I tried to get gecko and I don't think it worked. It's listed as gnome media player and when I try to open it, nothing happens.

---

### Post by NFblaze on 2010-07-25
> **linux18 said:**
> I've got 8 cores and flash is still bad

Yea, it works for me. It's on par to the usage with Windows now. Though, Im using 32-bit latest version with 2.9GB of RAM.

---

### Post by lovinglinux on 2010-07-25
> **princerameses said:**
> It's not working.. And yes, I got latest version. I think.

I tried to get gecko and I don't think it worked. It's listed as gnome media player and when I try to open it, nothing happens.

Can you post a screenshot?

---

### Post by linux18 on 2010-07-25
just got flash aid, now flash works in firefox and its as smooth as sandpaper which is a huge step up considering how it was before ( youtube was like powerpoint presentation ) I'll clean out my profile, remove old caches, and close all of my virtualbox sessions, then try again.

---

### Post by lovinglinux on 2010-07-25
> **linux18 said:**
> just got flash aid, now flash works in firefox and its as smooth as sandpaper which is a huge step up considering how it was before ( youtube was like powerpoint presentation ) I'll clean out my profile, remove old caches, and close all of my virtualbox sessions, then try again.

Cool :)

---

### Post by linux18 on 2010-07-25
update: flash-aid works great! just had to clean out all of the caches and close my 3 virtualbox sessions. it was like playing E.T. on the atari 2600, then like playing fallout 3, now its like playing rage on a high end pc ( the framerate is so smooooooooooth )

---

### Post by princerameses on 2010-07-25
> **lovinglinux said:**
> Can you post a screenshot?


A screenshot? Of what? This? >

[IMG]http://i25.tinypic.com/14uajxz.png[/IMG]

Also this when I try to use Gxine: 
(am I doing it right? use a FF addon to download video, open xgine, click open and find the file?)

[IMG]http://i25.tinypic.com/5wjlok.png[/IMG]

---

### Post by lovinglinux on 2010-07-25
> **princerameses said:**
> A screenshot? Of what? This? >


Please post large images as attachment.

I was referring to the YouTube video page. What are you trying to do? Are you referring to FlashVideoReplacer or FLASH-AID?

---

### Post by Vaphell on 2010-07-25
i write this using a pristine firefox profile with only replacer installed. Same thing happens though slightly less often - and i have screenshots to prove it! :-)

vimeo clip works somewhat better than youtube

---

### Post by princerameses on 2010-07-25
> **lovinglinux said:**
> Please post large images as attachment.

I was referring to the YouTube video page. What are you trying to do? Are you referring to FlashVideoReplacer or FLASH-AID?


Oh :P

Here.

[IMG]http://i28.tinypic.com/2vdodvc.jpg[/IMG]

And flashvideoreplacer I think.

---

### Post by lovinglinux on 2010-07-25
> **Vaphell said:**
> i write this using a pristine firefox profile with only replacer installed. Same thing happens though slightly less often - and i have screenshots to prove it! :-)

vimeo clip works somewhat better than youtube

Is really weird. What is your download bandwidth?

> **princerameses said:**
> Oh :P

Here.

And flashvideoreplacer I think.

Ok, looks like you don't have the necessary mp4 decoder. Try this:

```
sudo apt-get install ubuntu-restricted-extras
sudo apt-get remove gxineplugin
sudo apt-get install gecko-mediaplayer
```

Then restart Firefox and test again.

---

### Post by princerameses on 2010-07-25
Before I do that, you do realize I'm using Puppy linux and not Ubuntu, right?

---

### Post by Vaphell on 2010-07-25
i got 6M down, 0.5M up

---

### Post by lovinglinux on 2010-07-25
> **princerameses said:**
> Before I do that, you do realize I'm using Puppy linux and not Ubuntu, right?

Actually no. I have spent the night programming, so is hard enough to keep a coherent conversation with both of you at the same time and dealing with two different extensions issues :)


> **Vaphell said:**
> i got 6M down, 0.5M up

I have only 4M down, so that's probably not the issue.

---

### Post by Vaphell on 2010-07-25
is there a way to debug this?

---

### Post by princerameses on 2010-07-25
Ah. ;) Is k. Just thought I should ask before executing that command. 
I can't get gecko then, right? Because I don't have gnome?

---

### Post by lovinglinux on 2010-07-25
> **Vaphell said:**
> is there a way to debug this?

Open Firefox from terminal and open Firefox "Tools >> Error Console".

---

### Post by lovinglinux on 2010-07-25
> **princerameses said:**
> Ah. ;) Is k. Just thought I should ask before executing that command. 
I can't get gecko then, right? Because I don't have gnome?

I never used Puppy, but I use Ubutnu KDE and I can get gecko.

---

### Post by princerameses on 2010-07-25
Oh. Whenever I try to install something with 'gnome' or 'kde' or another specific desktop environment, it never works. :/

Well, I'm going to go. If anyone has any suggestion how to get it working better in puppy, please post, thanks.

---

### Post by lovinglinux on 2010-07-25
> **princerameses said:**
> Oh. Whenever I try to install something with 'gnome' or 'kde' or another specific desktop environment, it never works. :/

Check what packages you need to decode mp4 video and AAC audio.

---

### Post by auroraa9420 on 2010-07-25
peh yea i told my friend today

lol i thougth that it was some stupid youtube HD update :O

---

### Post by Vaphell on 2010-07-25
i launched FF from terminal and it spits a lot of stuff when the replacement is triggered, there is absolutely nothing if i get flash

also i think can reproduce the problem here with odds close to 100%. If i let the clip page to initialize in the background, i get flash 100%. If i switch to the spawned tab fast, during its initialization, most likely (as in ~100%) i get the replacement plugin.

---

### Post by culfunius on 2010-07-25
I don't know if it even makes sense to say this, but in the short time I used firefox, flash stuttered, lagged and drove up CPU. In chrome it's fine and runs as smoothly as it did in windows. 

I don't have enough experience with Ubuntu to stick my neck on the line and lay the blame on firefox - but if I did, I would.

---

### Post by Vaphell on 2010-07-25
chrome has better jscript engine so most probably it has more cpu cycles left to burn on inefficient flash. Flash is a magic black box provided by adobe, all you can do is plug it in, no questions asked, and pray.

---

### Post by mikewhatever on 2010-07-25
> **culfunius said:**
> ...

I don't have enough experience with Ubuntu to stick my neck on the line and lay the blame on firefox - but if I did, I would.

Priceless!:p

---

### Post by princerameses on 2010-07-26
Chrome works just as bad for me.

How do I do the decoding thing?

---

### Post by lovinglinux on 2010-07-26
> **Vaphell said:**
> also i think can reproduce the problem here with odds close to 100%. If i let the clip page to initialize in the background, i get flash 100%. If i switch to the spawned tab fast, during its initialization, most likely (as in ~100%) i get the replacement plugin.

Hmmm, the problem is that the extension captures the page address from the address bar to check if it should activate itself. So if you are not viewing the page it simply ignores it. I guess we figure out the source of the problem. I will look into an alternative method for the next version. Meanwhile, make sure you tick the last option in the Tabs preferences settings of Firefox. I have created a bug report entry, so you can follow it: [http://code.google.com/p/flvideoreplacer/issues/detail?id=7](http://code.google.com/p/flvideoreplacer/issues/detail?id=7)

---

### Post by Vaphell on 2010-07-26
cool :)

problem: buffering. What's appropriate for HD clips, doesn't really fly in case of lowres. I get long buffering time even for low/med clips (probably due to relatively big buffer size set in mplayer) but they should play pretty much right off the bat.
Is it possible to influence buffering times, for example by passing different buffer sizes as an argument to the mplayer plugin for different quality settings, without going to preferences every time?

btw what is mencoder used for? i've seen something like 'could not spawn mencoder process' in firefox output

and minor question, probably for some future release, after the basics are pinned down: is it possible to get info about the list of available resolutions for a given clip? low/med/hi don't offer enough control in some cases where you get 4 of 5 options like 240p, 320p, 480p, 720p

---

### Post by manObject on 2010-07-26
If you install VLC Player (Open Source), you'll be able to play all your .flv files (plus .mp3/.mp4 files) properly (easily better than in Microft Widows). If it is the embedded player in your Firefox browser you are having problems with, ditch the 'official' Adobe gizmo and try one of the free open source plugins that do the same job (listed on mozilla.org).

---

### Post by ratcheer on 2010-07-26
Flash is fine for me on Lucid. If I increase the resolution (say, to 720p), it does crank up my CPU usage, but it still plays well.

Tim

---

### Post by lovinglinux on 2010-07-26
> **Vaphell said:**
> problem: buffering. What's appropriate for HD clips, doesn't really fly in case of lowres. I get long buffering time even for low/med clips (probably due to relatively big buffer size set in mplayer) but they should play pretty much right off the bat.
Is it possible to influence buffering times, for example by passing different buffer sizes as an argument to the mplayer plugin for different quality settings, without going to preferences every time?


Open ~/.mplayer/config and add this:

```

cache=8192
cache-min=20.0
cache-seek-min=50
```

You might need to change the values to your liking.

> **manObject said:**
> If it is the embedded player in your Firefox browser you are having problems with, ditch the 'official' Adobe gizmo and try one of the free open source plugins that do the same job (listed on mozilla.org).

I wouldn't waste my time on that. Lots of people that come to the forums to solve flash issues have those open source alternatives. They don't work on many sites.


> **Vaphell said:**
> btw what is mencoder used for? i've seen something like 'could not spawn mencoder process' in firefox output

Mencoder is the mplayer video encoder. I don't know why you are getting such messages.


> **Vaphell said:**
> and minor question, probably for some future release, after the basics are pinned down: is it possible to get info about the list of available resolutions for a given clip? low/med/hi don't offer enough control in some cases where you get 4 of 5 options like 240p, 320p, 480p, 720p

It is possible, but too complicated, due to the variable nature of available versions. So I have decided to use the HIGH/MEDIUM/LOW approach. The extension will automatically use the best resolution available if you choose HIGH and the lowest if you choose LOW.

---

### Post by Vaphell on 2010-07-27
> Open ~/.mplayer/config and add this:

Code:

cache=8192
cache-min=20.0
cache-seek-min=50

You might need to change the values to your liking.

this totally doesn't work. You set some buffer size in mplayer config but plugin shows entirely different number in right-click > Preferences
Gecko-mediaplayer buffer is defined in gconf under gnome-mplayer > preferences > plugin_cache_size, i don't where to put those other 2 params to have them taken into account. And setting size to 8192 is asking to wait forever.

That evolution and fragmentation of mplayer config over time are a mess, i don't know where to find up-to-date manual to gecko-mediaplayer, i get lots of outdated stuff in google :/


Either way there is a problem with initial buffering - if i pick 240p it will buffer as long as that beefy 720p. When i choose lowres I don't really expect to wait more than 1 second for it to play. For 240p playback should start after first 200kB, for 720p probably 4MB - numbers pulled out of the *** of course.

maybe cache-percent i've seen somewhere would work, but only maybe, depends what it does exactly (and assuming there is a way to put it where plugin can find it)

---

### Post by lovinglinux on 2010-08-12
> **Vaphell said:**
> i launched FF from terminal and it spits a lot of stuff when the replacement is triggered, there is absolutely nothing if i get flash

also i think can reproduce the problem here with odds close to 100%. If i let the clip page to initialize in the background, i get flash 100%. If i switch to the spawned tab fast, during its initialization, most likely (as in ~100%) i get the replacement plugin.

This has been fixed on version 1.0.4, yet to be released.

Bug: [http://code.google.com/p/flvideoreplacer/issues/detail?id=7](http://code.google.com/p/flvideoreplacer/issues/detail?id=7)

---

