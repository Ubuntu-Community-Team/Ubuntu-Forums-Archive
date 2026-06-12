---
title: "My MP3 woes."
date: 2006-03-11
forum: General Help
---

### Post by Darkness3477 on 2006-03-11
Hi, I've been using Ubuntu on and off for a couple of months now, and I've finally taken the plunge and given up using Windows. So far it's gone great, well, great apart from one thing. 
I borrowed my dads MP3 player (Well, zen media player, as it holds anything) and used it as a removable disk and put all my music, some ebooks and a few mpg's onto it and switched them over from my computer with WIndows on it, to this one -My Linux box. 
The problem is something that I'm sure will be quite simple. I've opened up the folder containing all my songs on the computer, right clicked and clicked the option to open it up in [Music Player]. A little wizard came up, asked me to put in pathway where my songs were, I did it. Then, I got an error message called 'Error loading files into Library' and then it looked through all ther songs (Some 300) and told me this 'This file is not an audio streme -- file:///home/Desktop/ My music/song name.mp3' this is also happening with the MPG's. I then opened one of the film clips in totem movie player and it said t could not play the film clip because there were no decoders attached, and that I should get the corresponding plug in.

Well, I've no idea what and how I should get a plugin. So, A little help as to how I can listen to my music, as I've over 300 songs and I don't want to have to get them all again.

Thanks, 

--Michael.

---

### Post by Darkness3477 on 2006-03-11
Can anyone help, or is this in the wrong forum?

---

### Post by SavageBeginner on 2006-03-11
Check out this:  [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by Kevinator on 2006-03-11
I'm unclear on precisely what the problem is. Did you successfully copy the files onto your Ubuntu system or not? Is the issue accessing the files on the MP3 player device, using your music player (which one is it, anyway?), or locating codecs? Do other MP3s play?

Assuming the problem is codecs, please read these pages:

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)
[http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)

---

### Post by Darkness3477 on 2006-03-12
The problem is that I have got alot of mp3's on my other computer, and I switched them over to the one I'm currently on, which has just been installed recently and that they won't play.

---

### Post by nanotube on 2006-03-12
ubuntu does not come with mp3 decoder by default. you have to install a bunch of media codecs separately.
read [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats), like the earlier post said.. or even better enable the seveas repository, and install package "w32codecs". follow the link in my sig to my howto, it has sections on repositories, and making media files play on ubuntu. check it out.

---

### Post by powder on 2006-03-12
Your solution is don't use totem.  Totem sucks. :)

---

