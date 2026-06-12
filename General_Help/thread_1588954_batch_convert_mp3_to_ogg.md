---
title: "batch convert mp3 to ogg"
date: 2010-10-05
forum: General Help
---

### Post by sandyd on 2010-10-05
Is there some way of recursively batch converting mp3s into oggs while keeping the same directory structure?

---

### Post by scouser73 on 2010-10-05
> **sandyd said:**
> Is there some way of recursively batch converting mp3s into oggs while keeping the same directory structure?

I've used Sound Converter to batch convert, it can be found in the Ubuntu Software Centre.

---

### Post by papibe on 2010-10-06
Or you can go old school:
```
#!/bin/bash
for file in * 
do
    if [ -d "$file" ]
    then
        cd "$file"
        /home/youruser/Music/thisprogram.sh
        cd ..
    elif [ ${file##*.}  = "mp3" ]
    then
        ffmpeg -i "$file" "${file%.mp3}.ogg"
    fi
done
```

where /home/youruser/Music/ is the path to where the music is, and thisprogram.sh is shell script containing the code above.

Good Luck!

P.D.: you may need to install ffmpeg:
```
$ sudo apt-get instal ffmpeg
```

---

### Post by andrew.46 on 2010-10-13
Hi papibe,

If you have MPlayer installed you can also match the bitrate of the input mp3 to the bitrate of the output ogg by adding the following to your loop:

```
ffmpeg -i "$file" [B][COLOR="Red"]-ab $(mplayer -frames 0 -identify "$file" 2>/dev/null \
   | grep -m 1 'ID_AUDIO_BITRATE' | cut -d '=' -f 2)[/COLOR][/B] "${file%.mp3}.ogg"
```

Just a little embellishment :).

Andrew

---

### Post by mc4man on 2010-10-13
Just as a side note - I believe normally if you wish to use ffmpeg to encode to ogg then you'd need to specify -acodec libvorbis or it will (or attempt to) convert to flac in an ogg container.

Is it 'reacting' differently within the posted script (and embellishment
(haven't had a chance to try

---

### Post by size_XXM on 2010-10-14
One package: dir2ogg :)
> Description: audio file converter into ogg-vorbis format dir2ogg converts MP3, M4A, WMA, FLAC, WAV files and Audio CDs to the open-source OGG format.

 It is a Python script that simply binds together the various decoders and oggenc making it easier for the user to convert his/her music files. It also supports ID3 tags.
Homepage: [http://jak-linux.org/projects/dir2ogg/](http://jak-linux.org/projects/dir2ogg/) Stumbled upon this while searching for mp32ogg replacement :)

---

### Post by cascade9 on 2010-10-14
Its do-able, but you do know that a lossy-> lossy conversion (like mp3->ogg vorbis) will just make things sound worse, right? 

> **mc4man said:**
> Just as a side note - I believe normally if you wish to use ffmpeg to encode to ogg then you'd need to specify -acodec libvorbis or it will (or attempt to) convert to flac in an ogg container.

Is it 'reacting' differently within the posted script (and embellishment
(haven't had a chance to try

It does? Thats just....odd. I've never seen any point to flacs in an .ogg container.

---

### Post by papibe on 2010-10-14
> **andrew.46 said:**
> ...
```
ffmpeg -i "$file" [B][COLOR="Red"]-ab $(mplayer -frames 0 -identify "$file" 2>/dev/null \
   | grep -m 1 'ID_AUDIO_BITRATE' | cut -d '=' -f 2)[/COLOR][/B] "${file%.mp3}.ogg"
```...

WOW! super nice, thanks.

---

### Post by andrew.46 on 2010-10-14
Hi papibe,

> **papibe said:**
> WOW! super nice, thanks.

It is a little clumsy but I created this one as part of a script to strip audio from flv files for my wife :). Nice if there was a neat FFmpeg option that would do this, but FFmpeg always has its focus on video :(.

Andrew

---

