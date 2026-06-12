---
title: "Help boosting the volume of an album"
date: 2011-11-18
forum: General Help
---

### Post by CaptainMark on 2011-11-18
I have an album which ive ripped to .ogg using banshee but its really quiet, its only this one thats done this, i think because its an old album and wasnt recorded well.  Anyway how do I boost the volume of these track, ive done a bit of googling and didnt really understand about replay gain, i tried easymp3gain which should work for ogg but couldnt get it to boost the volume (its set at 89db and wont change for ogg) I thought using ffmpeg through winff would work but i get the error, vorbis unknown encoder

can anyone help??
Thanks 
mark

---

### Post by elliotn on 2011-11-18
did u try audacity or ardour, in window u can use the likes of cubase, Adobe audition etc so I guess ardour or audacity would but it could be done track by track not whole folder

---

### Post by nothingspecial on 2011-11-18
You could try sox. Make a copy of the songs into one folder to try it out. Then from that folder

```
for f in *.ogg; do sox -S -v 2.0 "$f" "${f/.ogg/}"_louder.ogg; done
```

This will give you some new files named song_louder.ogg


I don't know what the results will be like but if they are any good strip the louder bit from the file names and use them. 

You might need to install libsox-fmt-all to use it with oggs.

---

### Post by CaptainMark on 2011-11-18
i never thought to use audacity good idea, but nothingspecial your idea worked perfectly, thanks

---

### Post by elliotn on 2011-11-18
u welcome

---

### Post by nothingspecial on 2011-11-18
> **CaptainMark said:**
> i never thought to use audacity good idea, but nothingspecial your idea worked perfectly, thanks

No problem :)

---

### Post by andrew.46 on 2011-11-18
SoX also has the ability to calculate the maximum volume increase possible without creating distortion. For example:

```

andrew@skamandros~/media/Bartók_4tets$ **[COLOR="Red"]sox Bartók_4tet_1.ogg --show-progress -n stat[/COLOR]**

Input File     : 'Bartók_4tet_1.ogg'
Channels       : 2
Sample Rate    : 44100
Precision      : 16-bit
Duration       : 00:29:04.40 = 76928040 samples = 130830 CDDA sectors
File Size      : 40.8M
Bit Rate       : 187k
Sample Encoding: Vorbis
Comments       : 
title=String Quartet no.1 op.7 (1908-1909)
artist=Emerson String Quartet
album=Béla Bartók - 6 String Quartets

In:100%  00:29:04.40 [00:00:00.00] Out:76.9M [      |      ] Hd:0.4 Clip:0    
Samples read:         153856080
Length (seconds):   1744.400000
Scaled by:         2147483647.0
Maximum amplitude:     0.948181
Minimum amplitude:    -0.922028
Midline amplitude:     0.013077
Mean    norm:          0.035074
Mean    amplitude:    -0.000958
RMS     amplitude:     0.057689
Maximum delta:         1.405914
Minimum delta:         0.000000
Mean    delta:         0.041347
RMS     delta:         0.067867
Rough   frequency:         8257
**[COLOR="Red"]Volume adjustment:        1.055[/COLOR]**
Done.

```

The volume adjustment can then be added in with the same syntax suggested by nothingspecial:

```

andrew@skamandros~/media/Bartók_4tets$ **[COLOR="Red"]sox -v 1.055 --show-progress Bartók_4tet_1.ogg Bartók_4tet_1_vol.ogg [/COLOR]**

Input File     : 'Bartók_4tet_1.ogg'
Channels       : 2
Sample Rate    : 44100
Precision      : 16-bit
Duration       : 00:29:04.40 = 76928040 samples = 130830 CDDA sectors
File Size      : 40.8M
Bit Rate       : 187k
Sample Encoding: Vorbis
**[COLOR="Red"]Level adjust   : 1.055 (linear gain)[/COLOR]**
Comments       : 
title=String Quartet no.1 op.7 (1908-1909)
artist=Emerson String Quartet
album=Béla Bartók - 6 String Quartets

In:100%  00:29:04.40 [00:00:00.00] Out:76.9M [      |      ] Hd:0.8 Clip:2    
[B][COLOR="Red"]sox WARN dither: dither clipped 1 samples; decrease volume?
sox WARN sox: `Bartók_4tet_1.ogg' balancing clipped 1 samples; decrease volume?[/COLOR][/B]
Done.

```

You can see SoX suggesting that the volume could be a little lower in this example so I would normally drop the vol integer a little lower and re-encode. Not perfect for a folder full of individual files and a *for* loop but still a pretty cool use of SoX :).

---

### Post by blueridgedog on 2011-11-18
It would not be too big of a stretch to write a bash script that would pull the suggested integer from sox and build a file or hash of values (songname/integer) then call sox for each file, passing the correct integer to the command.

Edit:

The sox howto has some ideas:

sox foo.wav -e stat -v 2> vc && sox -v `cat vc` foo.wav foo-maxed.wav

So (just guessing):

for f in *.ogg; do sox "$f" -e stat -v 2> vc && sox -v `cat vc` "$f" "${f/.ogg/}"_louder.ogg; done

---

