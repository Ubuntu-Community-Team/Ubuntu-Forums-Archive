---
title: "Youtube flash player slow and laggy"
date: 2012-04-28
forum: General Help
---

### Post by PhantomTurtle on 2012-04-28
I run the amd64 version of Ubuntu 12.04 and when I play a youtube video in fullscreen it is very slow and laggy(only in fullscreen). The only time this does not happen is if I watch a video that has a 1080p version(I can still watch it at 480p in fullscreen and it would not be laggy). This happens in both Google Chrome and Mozilla Firefox. If a thread already exists for this please direct me to it. Thanks for all your help:)

---

### Post by pqwoerituytrueiwoq on 2012-04-28
what is your hardware?
only issue is with 1080p right
your hardware may just net be able to handle it
thought flash does suck and using your hardware properly (inefficient)
you should try using flash video replacer
[https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/](https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/)
set it to use the standalone player this way you will get full hardware acceleration

---

### Post by PhantomTurtle on 2012-04-28
> **pqwoerituytrueiwoq said:**
> what is your hardware?
only issue is with 1080p right
your hardware may just net be able to handle it
thought flash does suck and using your hardware properly (inefficient)
you should try using flash video replacer
[https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/](https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/)
set it to use the standalone player this way you will get full hardware acceleration

No, no only 1080p videos will work correctly. All the others are slow and laggy(even though that doesn't make sense that is the case). I have attached a screenshot from the flash player that shows how many frames were dropped in a 1 minute video I watched in 480p(fullscreen). Sorry about the misunderstanding. So do you have any other solutions?

---

### Post by pqwoerituytrueiwoq on 2012-04-28
odd that makes as much sence as my compiz benchmark getting 60fps when fading in/out but 4fps in the middle unless it is cause of the codec in use i think the lower quality videos use flv heigher quality uses mp4, give that addon a try it may solve the issue

---

### Post by PhantomTurtle on 2012-04-28
> **pqwoerituytrueiwoq said:**
> odd that makes as much sence as my compiz benchmark getting 60fps when fading in/out but 4fps in the middle unless it is cause of the codec in use i think the lower quality videos use flv heigher quality uses mp4, give that addon a try it may solve the issue

Will do, thank you. I will post the results here. Is there a similar chrome plugin?

EDIT: Wow that works great, Thank you. Is there a chrome plugin?

---

### Post by oslub on 2012-04-28
Hello. I run Lubuntu on an old desktop, and it is getting each time more difficult for me to watch youtube videos or watch online streamings after the latest releases of flash plugin, even if I select the worst quality possible. 

I saw this thread and I installed the flashvideoreplacer, but on the menu, only the preferences and quality are working, the copy url or download won't do any action, this seems some sort of bug, what can I do to fix it? If I don't disable the add-on, instead of the video there is just a black square and with this bug I can't download it. I also tried to select external method and chose GNOME player, but nothing happens.

Also I started a thread about how slow webpages load on my lubuntu, both on Firefox and Chromium, which is I guess mostly because of Flash not running so well on Linux, even though my old desktop is limited in its configurations, on windows I can at least load webpages instantaneously and watch videos in lower quality. Any ideas would be appreciated.

[http://ubuntuforums.org/showthread.php?t=1967018](http://ubuntuforums.org/showthread.php?t=1967018)

---

### Post by PhantomTurtle on 2012-04-28
> **oslub said:**
> Hello. I run Lubuntu on an old desktop, and it is getting each time more difficult for me to watch youtube videos or watch online streamings after the latest releases of flash plugin, even if I select the worst quality possible. 

I saw this thread and I installed the flashvideoreplacer, but on the menu, only the preferences and quality are working, the copy url or download won't do any action, this seems some sort of bug, what can I do to fix it? If I don't disable the add-on, instead of the video there is just a black square and with this bug I can't download it.

Also I started a thread about how slow webpages load on my lubuntu, both on Firefox and Chromium, which is I guess mostly because of Flash not running so well on Linux, even though my old desktop is limited in its configurations, on windows I can at least load webpages instantaneously and watch videos in lower quality. Any ideas would be appreciated.

[http://ubuntuforums.org/showthread.php?t=1967018](http://ubuntuforums.org/showthread.php?t=1967018)

This might just be your computer, if it is too old then it will of course be slow and not suited for watching youtube videos. Also the download function works fine for me, so I'm not sure what the problem is.

---

### Post by oslub on 2012-04-29
Yes, in fact the hardware configurations don't help, but I used to have a better experience watching videos before the latest releases of flash plugin. Here you have a thread addressing this issue and providing some workarounds, including the flashvideoreplacer. 

[http://ubuntuforums.org/showthread.php?t=1953796]("http://ubuntuforums.org/showthread.php?t=1953796")

---

### Post by PhantomTurtle on 2012-04-29
> **oslub said:**
> Yes, in fact the hardware configurations don't help, but I used to have a better experience watching videos before the latest releases of flash plugin. Here you have a thread addressing this issue and providing some workarounds, including the flashvideoreplacer. 

[http://ubuntuforums.org/showthread.php?t=1953796]("http://ubuntuforums.org/showthread.php?t=1953796")

Thanks, I'll try those as well. This problem is only with the Youtube player, it's really weird. Vimeo video's and other video's sites like Crunchyroll work absolutely fine. I hope they fix this because the html5 player isn't the best solution right now.

EDIT: Well that doesn't seem to work either. If anybody has any other solutions then please help me out.

---

### Post by pqwoerituytrueiwoq on 2012-04-30
> **PhantomTurtle said:**
> Will do, thank you. I will post the results here. Is there a similar chrome plugin?

EDIT: Wow that works great, Thank you. Is there a chrome plugin?
there is one but it is not a full featured, at least i think there is [[COLOR=#d40000]**lovinglinux**[/COLOR]]("http://ubuntuforums.org/member.php?u=649167") is the author IIRC he said there was one but he would know where it is since i am not having any luck with google
there is another trick this works with most flash videos you pause them and run this command

```
d="`date`";ln -s `f="$(ls -l /proc/$(pgrep -f flashplayer)/fd | grep deleted)" && f="${f##*:+([0-9]) }" && f="${f%% -*}" && echo /proc/$(pgrep -f flashplayer)/fd/"$f"` /tmp/"movie-$d";**vlc** /tmp/"movie-$d"
```if you prefer totem or smplayer to vlc you can change vlc at the end to what ever player you want to use

---

### Post by uylug on 2012-04-30
Use the HTML5 Youtube Video Player.

So much better than flash.

---

### Post by PhantomTurtle on 2012-04-30
> **pqwoerituytrueiwoq said:**
> there is one but it is not a full featured, at least i think there is [[COLOR=#d40000]**lovinglinux**[/COLOR]]("http://ubuntuforums.org/member.php?u=649167") is the author IIRC he said there was one but he would know where it is since i am not having any luck with google
there is another trick this works with most flash videos you pause them and run this command

```
d="`date`";ln -s `f="$(ls -l /proc/$(pgrep -f flashplayer)/fd | grep deleted)" && f="${f##*:+([0-9]) }" && f="${f%% -*}" && echo /proc/$(pgrep -f flashplayer)/fd/"$f"` /tmp/"movie-$d";**vlc** /tmp/"movie-$d"
```if you prefer totem or smplayer to vlc you can change vlc at the end to what ever player you want to use

That opens VLC, what do I do after that?

> **uylug said:**
> Use the HTML5 Youtube Video Player.

So much better than flash.

I have tried the html5 player it's really good, but there are still a couple of things that don't work, but I don't mind those as much as slow laggy video. That's what I use for now.

---

### Post by pqwoerituytrueiwoq on 2012-04-30
> **PhantomTurtle said:**
> That opens VLC, what do I do after that?
if you are playing flash videos on youtube for example it will open the video in vlc it just works on more sites than flash video replacer  and on off-site embeds

---

