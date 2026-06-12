---
title: "Rhymnbox &amp; GStreamer"
date: 2009-11-26
forum: General Help
---

### Post by lovemylady on 2009-11-26
**H***ey*,

I got following problem when I'm trying to open a music file with the already included video player or with the rhymnbox i get the following Error "My installation of Gstream misses a plugin" 

And i can't really get through what is missing

(yes when i opened the first time a mp3 with rhymbox some popup appeared with additional plugins to play mp3 etc.. whatever i updated it and after that i get the above error


To give ya a better idea what I mean check the screenshot..

[IMG]http://www3.pic-upload.de/26.11.09/9w88tp4vpgz.png[/IMG]



**W**ould be happy for every help :popcorn:




Edit: Like you can see with VLC- Media player everything works fine.. but i do not really like it to play music with...^^

---

### Post by raktarok on 2009-11-26
Enable the universe and multiverse repos and try this, though it may drag some things you won't need. But all of these may have been already installed.. 

```
sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse 
```

---

### Post by lovemylady on 2009-11-26
> **raktarok said:**
> Enable the universe and multiverse repos and try this, though it may drag some things you won't need. But all of these may have been already installed.. 

```
sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse 
```

 How do I enable it again?

Or is it enough just to copy your code and put it into my terminal?!

---

### Post by mc4man on 2009-11-26
Close out any players and give this a try in a terminal and see if things improve. (copy and paste the whole deal at once
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly-multiverse

```
If not then try a restart ( if using karmic in particular

Edit: see you already got the lines...

---

### Post by raktarok on 2009-11-26
Go to System > Administration > Software Sources and there you can tick mark all 4 (main, universe, restricted and multiverse.) Then try the code above - it installs all the common gstreamer plugins.

---

### Post by lovemylady on 2009-11-26
> **mc4man said:**
> Close out any players and give this a try in a terminal and see if things improve. (copy and paste the whole deal at once
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly-multiverse

```If not then try a restart ( if using karmic in particular

Edit: see you already got the lines...

Done that now.. but still doesn't seem to work, do i might need to restart?!




*[COLOR=Red]**EDIT: Sorry :rolleyes: ^^ everything works perfect now thanks for your help @ you two ;)**[/COLOR]*

---

