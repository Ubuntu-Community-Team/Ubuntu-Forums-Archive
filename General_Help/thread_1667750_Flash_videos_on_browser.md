---
title: "Flash videos on browser"
date: 2011-01-15
forum: General Help
---

### Post by Mortesins93 on 2011-01-15
Hello,
I have an old computer with a 500MHz Pentium III processor, 256MB of RAM, and a MGA G400/G450 graphics card. Is there anyway I can watch youtube videos without them being choppy? I read various threads but I did not understand if there are minimum specifications to watch a flash video properly on a browser. In other words, is there anything I can install to watch youtube videos or do I have to change my graphics card?
I used to have U-lite with the Ubuntu 8.04 kernel, it worked fine expect for youtube videos. Right now I am running Puppy linux on a hard install because my Lubuntu installation crashed. Soon, I want to try reinstalling Lubuntu with the alternate CD, but if there is no way I can watch youtube videos with what I have there is no point in trying since Puppy linux is working fine expect for flash videos.
By the way I attached my hardware info file.
Hope you can help me.
Thanks

---

### Post by TeoBigusGeekus on 2011-01-15
What I'd do if I were you:
Go to youtube, select a video to watch and press play. As soon as it starts to load, press pause.
Let it load completely, without actually playing it. Then off to your /tmp folder; the video is there and you can watch it with vlc, totem, or anything your like, without having flash blowing up your motherboard.
It's a bit of a fuss, but certainly cheaper than buying a new graphics card.

PS: Delete it aftewards, as it's illegal to keep it...

---

### Post by Mortesins93 on 2011-01-15
Thanks, I'll try it again because if i remember correctly I tried it and the videos were still choppy even though with the same player I could watch other videos properly. Could it be a problem with the media player related to flash videos only?

---

### Post by Mortesins93 on 2011-01-15
Thanks, I'll try it again because if i remember correctly I tried it and the videos were still choppy even though with the same player I could watch other videos properly. Could it be a problem with the media player related to flash videos only?

---

### Post by Mortesins93 on 2011-01-15
Thanks, I'll try it again because if i remember correctly I tried it and the videos were still choppy even though with the same player I could watch other videos properly. Could it be a problem with the media player related to flash videos only?

---

### Post by Mortesins93 on 2011-01-15
Thanks, I'll try it again because if i remember correctly I tried it and the videos were still choppy even though with the same player I could watch other videos properly. Could it be a problem with the media player related to flash videos only? I'll try loading it and then watching the file on another computer where I know flash videos work.

---

### Post by TeoBigusGeekus on 2011-01-15
Try with different players, vlc, totem, mplayer, etc. and see which one gives you the best result.

---

### Post by lovinglinux on 2011-01-15
Get [FlashVideoReplacer](https://addons.mozilla.org/en-US/firefox/addon/161869/) extension to watch YouTube, Vimeo and Metacafe with a different plugin.

The extension automatically replaces embedded flash videos with mp4 or flv videos, allowing to watch flash streaming content with a less CPU intensive plugin like gecko-mediaplayer.

It also allows to automatically launch the video with a standalone player, so you don't need to look into the tmp or cache folder.

---

### Post by lovinglinux on 2011-01-15
Duplicate

---

### Post by lovinglinux on 2011-01-15
Duplicate

---

### Post by lovinglinux on 2011-01-15
Duplicate

---

### Post by lovinglinux on 2011-01-15
Duplicate

---

### Post by Mortesins93 on 2011-01-16
Ok thanks, I'll try that again, you probably won't remember but you suggested me the same thing when I had U-lite but it did not work. Anyways I want to try it again, so it works on any linux distro with Firefox? Because right now I have puppy linux installed.

---

### Post by Bazzi313 on 2011-01-16
> **Mortesins93 said:**
> Hello,
I have an old computer with a 500MHz Pentium III processor, 256MB of RAM, and a MGA G400/G450 graphics card. Is there anyway I can watch youtube videos without them being choppy? I read various threads but I did not understand if there are minimum specifications to watch a flash video properly on a browser. In other words, is there anything I can install to watch youtube videos or do I have to change my graphics card?
I used to have U-lite with the Ubuntu 8.04 kernel, it worked fine expect for youtube videos. Right now I am running Puppy linux on a hard install because my Lubuntu installation crashed. Soon, I want to try reinstalling Lubuntu with the alternate CD, but if there is no way I can watch youtube videos with what I have there is no point in trying since Puppy linux is working fine expect for flash videos.
By the way I attached my hardware info file.
Hope you can help me.
Thanks
Try a program called speedbit, it speeds up viddeo buffering

---

### Post by lovinglinux on 2011-01-16
> **Mortesins93 said:**
> Ok thanks, I'll try that again, you probably won't remember but you suggested me the same thing when I had U-lite but it did not work. Anyways I want to try it again, so it works on any linux distro with Firefox? Because right now I have puppy linux installed.

Indeed I don't remember :oops:

The current version is a complete rewrite, with many new features, so it might work for you now.

It works on any OS with Firefox. However you need a compatible plugin that can play mp4 and flv, like gecko-mediaplayer or a standalone player like smplayer or gnome-mplayer.

---

### Post by Mortesins93 on 2011-01-21
So I installed it, it works great, thank you. It is choppy once a while but I can't complain. Great add-on.

---

### Post by lovinglinux on 2011-01-22
> **Mortesins93 said:**
> So I installed it, it works great, thank you. It is choppy once a while but I can't complain. Great add-on.

You are welcome.

New version will be released soon, with support for Ustream and Blip.tv.

---

