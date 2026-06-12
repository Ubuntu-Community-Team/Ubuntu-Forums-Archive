---
title: "Converting a video for mobile phone"
date: 2010-08-13
forum: General Help
---

### Post by thameera on 2010-08-13
What is a good app to convert videos in Ubuntu? 

I usually watch documentaries, movies etc in my mobile phone and need an app to convert AVIs etc with a low file size and about 320x240 resolution. 
Used WinFF but it doesn't seem good enough :-k

---

### Post by sydbat on 2010-08-13
> **thameera said:**
> What is a good app to convert videos in Ubuntu? 

I usually watch documentaries, movies etc in my mobile phone and need an app to convert AVIs etc with a low file size and about 320x240 resolution. 
Used WinFF but it doesn't seem good enough :-kKdenlive.

---

### Post by lykeion on 2010-08-13
I use mencoder from the command-line to convert videos to 320x240 XviD video MP3 audio (to play in my mp3 player Creative Zen 4GB).

I guess this should work for mobile phone as well, but maybe you should check the specifics of your mobile phone video support on its homepage.

1. Install mencoder```
sudo apt-get install mencoder
```
2. Convert a video like this (note I use 4 threads since I have a quad-core cpu)```
mencoder input.avi -o output.avi -lavdopts threads=4 -vf scale=320:240 -oac mp3lame -ovc xvid -xvidencopts bitrate=-1
```If this works for you, I also have a zenity script for this if you're interested.

---

### Post by thameera on 2010-08-13
Thanks for the answers, guys.

@sydbat: I tried kdenlive but couldn't file a good profile to convert to mobile.

@lykeion: Tried mencoder. The code you've mentioned creates a file that is 500+ MB large. How can I change that to create an MP4 file with about, say, 200MB file? Thanks!

---

### Post by lykeion on 2010-08-13
You can set the filesize you want in kilobytes in order to make mencoder calculate the bitrate for you. 
This can be done by setting a "negative" bitrate, bitrate=-204800 will give you a movie file with a size of 200MB.```
mencoder input.avi -o output.avi -lavdopts threads=4 -vf scale=320:240 -oac mp3lame -ovc xvid -xvidencopts bitrate=-204800
```For mp4 encoding I found this link:
[http://www.xiaoka.com/blog/2008/03/29/encode-mp4-files-for-nokia-n95-with-mencoder/](http://www.xiaoka.com/blog/2008/03/29/encode-mp4-files-for-nokia-n95-with-mencoder/)

---

### Post by thameera on 2010-08-13
Thanks, but still I'm facing problems. Perhaps its because my source file is an MKV one. Thanks anyway, I'll try to fix it somehow or other :)

---

### Post by sydbat on 2010-08-13
> **thameera said:**
> Thanks for the answers, guys.

@sydbat: I tried kdenlive but couldn't file a good profile to convert to mobile.

You're welcome. :)

I think you have to use the lowest mp4 setting to make a small file.

And maybe there are some additional codec thingys (technical term) you might need to add.

---

### Post by birdmanuk on 2010-08-14
Handbrake :-)

---

