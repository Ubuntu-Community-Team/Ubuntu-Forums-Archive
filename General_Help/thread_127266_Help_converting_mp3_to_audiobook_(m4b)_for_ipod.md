---
title: "Help converting mp3 to audiobook (m4b) for ipod"
date: 2006-02-08
forum: General Help
---

### Post by hal pacino on 2006-02-08
I have a Cree language CD that I ripped to mp3. I would like to be able to play it as an audiobook on my ipod video (5th gen). I downloaded a script that should do this. I'm using:
madplay 0.15.2 (beta)
faac 1.24
Here is the output of my conversion:
```
Transcoding 01 - Greetings - Salutations.mp3
RUNNING: /usr/bin/madplay -o wave:- "test/01 - Greetings - Salutations.mp3" | /usr/bin/faac -w -o "test/01 - Greetings - Salutations.m4b" --obj-type LC --artist "Eastcree.org" --title "Greetings / Salutations" --genre "" --album "Cree Converstation Crie" --track "01/21" --comment 'Transcoded from MP3'  -
MPEG Audio Decoder 0.15.2 (beta) - Copyright (C) 2000-2004 Robert Leslie et al.
          Title: Greetings / Salutations
         Artist: Eastcree.org
          Album: Cree Converstation Crie
          Track: 01/21
           Year: 2002
Freeware Advanced Audio Coder
FAAC 1.24

Quantization quality: 100
Bandwidth: 16000 Hz
Object type: Low Complexity(MPEG-4) + TNS + M/S
File format: MPEG-4 File Format (MP4)
Encoding - to test/01 - Greetings - Salutations.m4b
   frame          | bitrate | elapsed/estim | play/CPU | ETA
 7800/1048577 (  0%)|   91.7  |   16.0/2145.6 |   11.35x | 2129.7 6971 frames decoded (0:03:02.0), +0.2 dB peak amplitude, 2 clipped samples
 7844/1048577 (  0%)|   91.8  |   16.1/2145.8 |   11.35x | 2129.7 
```

I load it up to my ipod in gtkpod. When I select it in audiobooks for playback it goes directly back to the menu. In short, my ipod won't play it, but bmp or xmms will (if I rename it with a m4a extension; they don't seem to like m4b).

I'm using the mp4 wrapper with LC settings (but I've also tried aac mpeg-2, which gtkpod cannot even seem to recognize).

What gives? Any suggestions?

Thanks in advance for any help.

---

### Post by supenguin on 2006-02-08
Maybe I'm missing something, but what's wrong with setting the genre to "Books & Spoken" and just putting the mp3's on your ipod?

---

### Post by am_pcguy on 2006-02-09
There is nothing wrong with encoding to MP3 and playing the files, but if you encode in the audiobook format you will get a bookmarking feature.

---

### Post by hal pacino on 2006-02-09
Which brings me to my original question: How do I encode to an audiobook that my ipod will actually read?

---

### Post by hal pacino on 2006-02-12
Any thoughts? Anyone?

---

### Post by Edward The Bonobo on 2006-02-17
>>Maybe I'm missing something, but what's wrong with setting the genre to "Books & Spoken" and just putting the mp3's on your ipod?

Because then you can't vary the output speed or skip to the next chapter.  And it's damned inconvenient always having to start the book at the begining again every time you go back to it.  Or else listen to the whole thing in a single sitting.

I'd be interested in that Cree book, by the way.  I collect language textbooks.  Yes...I'm aware that it's a strange hobby.

---

### Post by hal pacino on 2006-02-17
If you can help me find a way to make a working m4b file, I'll hook you up.

---

### Post by ChrisQ on 2006-06-03
gtk-pod won't recognize it because whoever wrote gtkpod didn't write it to check for aac support at run time and so it has to be compiled in. in the ubuntu version of gtkpod it isn't compiled in. you'll have to grab the marillat debian version and force install it to get it to work.

---

### Post by sinaen on 2006-08-30
someone here on the forum has written a script that does the job youre asking for.

but i dont know where.. ill se if i find it ok?

[http://www.ubuntuforums.org/showthread.php?t=180073&highlight=audiobook+support](http://www.ubuntuforums.org/showthread.php?t=180073&highlight=audiobook+support)
here it is :p

---

### Post by Motoma on 2006-09-23
I did this using ffmpeg.

First, encode the audio using AAC:
$ ffmpeg -i greeting_essare_and_avere.mp3 -acodec aac greetings_essare_and_avare.m4a

Then, rename the file with an m4b extension:
$ mv greetings_essare_and_avare.m4a greetings_essare_and_avare.m4b

Hope this helps,
Motoma

---

### Post by ChrisQ on 2006-09-23
I did this with two programs. The first is mp3wrap to join a bunch of shorter mp3s together into about 2 hour mp3s.

mp3wrap output.mp3 input*

Then use something like this:
madplay -m -o wave:- WOT4-Shadow\ Rising-01to03_MP3WRAP.mp3 | faac -w --no-midside -b 32  --artist "Robert Jordan" --genre Audiobook --title rjbookfour01to03 -o 01to03bookfour.m4b -

madplay -m -o wave: - converts the mp3 to wav and the faac stuff converts that to aac.. you can look at the man page for faac and madplay to figure otu what the switches do, or just leave them the way they are and change the rjbook stuff and artist stuff to what you want. It'll work great with an ipod.

---

