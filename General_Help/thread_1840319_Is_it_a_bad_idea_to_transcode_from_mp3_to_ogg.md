---
title: "Is it a bad idea to transcode from mp3 to ogg?"
date: 2011-09-07
forum: General Help
---

### Post by ninjaaron on 2011-09-07
I want to convert some of my music to a lower bit-rate so that I can fit more on my pmp.

I know they say that converting from lossy to lossy is bad or something, but I'm already converting to a lower quality. I want to use ogg because it's free and I hear that it has better compression.

Is transcoding from mp3 to ogg any worse than going from mp3 to mp3?

PS- you can move this to multimedia if you want.  I just expect to get answers quicker here.

---

### Post by raja.genupula on 2011-09-07
no man , i think you can go .

---

### Post by ninjaaron on 2011-09-07
Ok.  I'll give it a shot.

I always find that the quality of the music depends much more on the speakers and headphones than the bit-rate of the source (unless it's an audio book at 21Kbs or something).  Maybe you need audiophile-grade equipment to hear the difference, or maybe I'm just deaf.

---

### Post by b0b138 on 2011-09-07
For the most part yes, its a bad idea.  It will sound worse going from lossy to lossy rather than lossless to lossy.  Also, you won't see that much of a file size difference and the sound will be awful.

---

### Post by bodhi.zazen on 2011-09-07
> **b0b138 said:**
> For the most part yes, its a bad idea.  It will sound worse going from lossy to lossy rather than lossless to lossy.  Also, you won't see that much of a file size difference and the sound will be awful.

Depends on the tool you use to convert and what parameters you use.

---

### Post by nothingspecial on 2011-09-07
Aslong as you keep the original files then no harm done.

---

### Post by Slim Odds on 2011-09-07
> **bodhi.zazen said:**
> Depends on the tool you use to convert and what parameters you use.

I completely agree. Most tools have settings for the quality of the conversion (and I'm not talking about bit rate). So the conversion will take longer, but you'll get the best possible quality at the selected bit rate.

---

### Post by aura7 on 2011-09-07
Try to convert the original songs directly to ogg format with lower bitrate... mp3 has already degraded the songs and hence I think the above mentioned method will give you better quality.

---

### Post by IWantFroyo on 2011-09-07
```
ffmpeg2theora -a 10 file.mp3 -o file.flac --novideo
```This should give you perfect sound quality. If you want lower, you can change from 10 to a lower number.

I don't precisely remember if this is the command, but it should work.

---

### Post by ninjaaron on 2011-09-07
Eh, screw it.  All my CD's are on another continent (fo' rlz).  I just want to fit way more songs on my mp3 player.

Most of the songs I'm converting are @320Kbs or high quality VBR.  I'm converting them all to ogg @64Kbs :P (keeping the originals, don't worry).

Seriously though, I'm a/b-ing them with the headphones I normally use with the player (Klipsch Image S4), and I really don't hear a significant difference.  Not sure if this means the headphones are shite (the reviews of which would indicate otherwise), or I'm just deaf, which I suppose is possible, but I *am* a musician, so I normally 'hear things.'

If it sounds good to me, I guess it sounds good enough, since I'm the one who's got to listen to it.

---

### Post by ninjaaron on 2011-09-07
> **IWantFroyo said:**
> ```
ffmpeg2theora -a 10 file.mp3 -o file.flac --novideo
```This should give you perfect sound quality. If you want lower, you can change from 10 to a lower number.

I don't precisely remember if this is the command, but it should work.

with ffmpeg, it's this:
```
ffmpeg -i file.mp3 -acodec flac -aq 10 file.flac
```
probably the same in ffmpeg2theora except without that nonsense about specifying the codec (I actually don't even know if you need it for flac, but it's good to have it, just in case. Actually, if you convert to a .ogg container, ffmpeg actually uses the flac codec by default, so the quality is great, but it's not compressed much.  If you want an actual lossy compressed file, you have to use the libvorbis codec).

---

### Post by ninjaaron on 2011-09-07
lulz.  It's through 754 MB of the original files, and the ogg's are taking 219MB.

And I can't even hear the difference.:P

I almost feel embarrassed.  Either I'm totally deaf or the emperor has no clothes.:lolflag:

edit:
ok, I read about what some of the artifacts of ogg are supposed to sound like, and I can actually hear them.  They just don't bother me at all.  It doesn't sound any worse to me, just a little different, like there is a tiny touch of reverb.

Anyway, thread solved, I guess.

---

### Post by ninjaaron on 2011-09-08
ok, for really reals, I think I was listening to the wrong songs.  I was listening to songs with a lot going on before to see if the details got muddled.

What I'm noticing is that the artifacts are much more obvious in songs with simple arrangements, and especially with certain frequencies and timbers.  Sorry I ever doubted you guys. :p

Still, they don't bother me too much (yet) if I don't concentrate on them, and I've gotten 3.5GB down to 902MB.

I may try to do it once again, but this time, just convert the high-bitrate mp3's to 128Kbs ogg, and leave the lighter mp3's where they are.

---

### Post by bodhi.zazen on 2011-09-08
You have to toy with the various settings to strike a balance between file size and acceptable audio performance.

3.5 Gb -> 1 Gb is a substantial space savings.

---

### Post by ninjaaron on 2011-09-08
Yeah, I did it again, except this time converting to 128Kbs, and leaving any mp3's &#8804; 160Kbs where they were. Now it's at 1.7GB from 3.5GB.  Not too shaby, and the sound quality is better.  I checked the places where I was getting noticeable artifacts before, and they seem to be all but gone.

---

### Post by Pithikos on 2011-09-08
> **IWantFroyo said:**
> ```
ffmpeg2theora -a 10 file.mp3 -o file.flac --novideo
```This should give you perfect sound quality. If you want lower, you can change from 10 to a lower number.

I don't precisely remember if this is the command, but it should work.

Isn't this converting the mp3s into flacs? Not many mp3 players that support that format.

---

### Post by hhh on 2011-10-22
re: sampling rates, I find very little difference once you get to 192kbps and above, and that is going to be in the high ends. Going down to 128 is only slightly noticeable to me using good headphones, anything lower is pretty noticeable to me. It all depends on how brittle the cilia in your ear are, if you're older and have listened to excessive loudness, you won't hear much difference as yo' hairs ain't got no mo' flex, yo.

With speakers, 128kbps is fine for most speakers/listening rooms as the speaker distortion and ambient noise of your air conditioning and so on will mask the slight quality difference. If you have an audiophile system and a dedicated listening room, you're probably not listening to lossless formats anyway.

---

