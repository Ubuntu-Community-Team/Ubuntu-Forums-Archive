---
title: "rip cd to 1 mp3 file"
date: 2011-11-20
forum: General Help
---

### Post by qwertyjjj on 2011-11-20
I can't seem to find the settings for ripping to mp3 in Sound Juicer, it only seems to have the obscure .ogg filetype.
How can I rip a CD with split tracks (no gaps) into 1 mp3 file with no gaps between songs so that it runs seamlessly?
Thanks

---

### Post by An Sanct on 2011-11-20
For the mp3 support, you need to have the "restricted extras", as it is one of the *non-free* formats.

To making a single mp3 file out of the whole disc, use another tool, if sound juicer does not have this option... I know I have seen this option in K3B, but I had problems with mp3 support (on my vanilla Ubuntu 10.10)

---

### Post by bryncoles on 2011-11-20
You might need to install LAME (Lame Aint an MP3 Encoder) to get MP3 support.  Open a terminal and type ```
sudo apt-get install lame
```

---

### Post by qwertyjjj on 2011-11-20
> **An Sanct said:**
> For the mp3 support, you need to have the "restricted extras", as it is one of the *non-free* formats.

To making a single mp3 file out of the whole disc, use another tool, if sound juicer does not have this option... I know I have seen this option in K3B, but I had problems with mp3 support (on my vanilla Ubuntu 10.10)

restricted extras?

---

### Post by bryncoles on 2011-11-20
Open Ubuntu software centre, and type in 'restricted extras' into the search bar.  It'll enable flash support, mp3 support and a few other things.  Just make sure you pick the right batch of restricted extras -- Ubuntu for Ubuntu, Xubuntu for... well, you get it!

---

### Post by An Sanct on 2011-11-20
> **bryncoles said:**
> Open Ubuntu software centre, and type in 'restricted extras' into the search bar.  It'll enable flash support, mp3 support and a few other things.  Just make sure you pick the right batch of restricted extras -- Ubuntu for Ubuntu, Xubuntu for... well, you get it!

Yes, thank you :)

The term "[restricted extras]("http://en.wikipedia.org/wiki/Ubuntu-restricted-extras")" means all the stuff, that was not installed, because you have to *agree* to the terms and conditions and is not under the GNU license. Like mp3, the MicroSoft fonts package, DVD auditing stuff, Audio editing stuff, Flash, .... etc

PS. It's one of the first 10 packages I install just after I install a fresh Ubuntu.

---

### Post by An Sanct on 2011-11-20
> **bryncoles said:**
> You might need to install LAME (Lame Aint an MP3 Encoder) to get MP3 support.  Open a terminal and type ```
sudo apt-get install lame
```
Thank you!

I installed LAME and ran K3B, mp3 support was added successfully!!!!

---

### Post by bryncoles on 2011-11-21
Victory is ours!

;-)

Now, if the problem is resolved, could you use the thread tools to mark as solved?

---

### Post by andrew.46 on 2011-11-21
> **qwertyjjj said:**
> I can't seem to find the settings for ripping to mp3 in Sound Juicer, it only seems to have the obscure .ogg filetype.

I see you have worked out your problem which is great :). Just a quick note though to defend the 'obscure .ogg filetype' which is not particularly obscure and produces great sound quality. Try it and you might very well be surprised!

---

### Post by An Sanct on 2011-11-21
> **andrew.46 said:**
> I see you have worked out your problem which is great :). Just a quick note though to defend the 'obscure .ogg filetype' which is not particularly obscure and produces great sound quality. Try it and you might very well be surprised!
I would also like to defend the ogg vorbis format :)

Would anybody tell me if there are any "mp3 players", that support this format? I personally have not seen one yet, that is why I still use mp3...

---

### Post by andrew.46 on 2011-11-21
> **An Sanct said:**
> Would anybody tell me if there are any "mp3 players", that support this format? I personally have not seen one yet, that is why I still use mp3...

I have a relatively aged device, by modern standards, an iRiver X20 which plays ogg audio. In fact I bought it for this reason! I imagine that more modern devices should also play ogg, I have heard good things about the newer Cowon players. BTW if anybody is interested in the iRiver X20 I have a page that shows how to encode video for this device:

Encoding Video for the iRiver X20
[http://www.andrews-corner.org/iRiverX20.html](http://www.andrews-corner.org/iRiverX20.html)

---

### Post by John Peschken on 2011-12-03
On the OGG Format ... my Android phone supports it, but my Honda Civic's CD player does not.  That makes me sad,

---

