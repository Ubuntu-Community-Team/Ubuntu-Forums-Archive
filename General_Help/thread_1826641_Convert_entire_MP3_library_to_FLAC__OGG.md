---
title: "Convert entire MP3 library to FLAC / OGG?"
date: 2011-08-16
forum: General Help
---

### Post by 8_Bit on 2011-08-16
What's the easiest way to convert ALL mp3's in a library folder into a non-proprietary format like  FLAC or OGG format?

One that can search recursively and save the converted files in the same folders as the originals.

---

### Post by hhh on 2011-08-16
Converting mp3 to flac doesn't make much sense, since mp3 is lossy and flac is lossless, but you can do conversions easily with pacpl (Perl Audio Converter), available in the Ubuntu repos.

After installing pacpl...```
sudo apt-get install pacpl
```... switch to the directory you want to convert (you'll need to take spaces out of directory names for that)... ```
cd Music
```
and run the following, or substitute the formats for something else (last one is what you are converting, first is the format you want to convert to...```
pacpl -t ogg -r *.mp3
```

This is what I use to convert flac to mp3 and set the bitrate at 192kbps...
```
pacpl -t mp3 --bitrate 192 -r *.flac
```

BTW, I recommend installing lame (mp3 encoder) and removing twolame.

---

### Post by 8_Bit on 2011-08-17
Thanks! I'll try your suggestion.
 
I know that it doesn't make sense, but on a computer I'm working with, the proprietary MPEG codecs do not work for certain reasons, so I have to convert the MP3s  to a free format just to get them to play. It's not for professional archival / music collection purposes, so it doesn't matter.

---

### Post by shantiq on 2011-08-17
Another possible route


ok yes to flac no sense as lossless and mp3 lossy

but to ogg perfectly sound idea

here is a small script to do this   simply cd to where all the folders you want to convert are and enter the whole lot at once


```
for i in */
do
  cd "$i"
  for f in *.mp3; do ffmpeg -i "$f" -acodec libvorbis  -ab 320k "${f%.mp3}.ogg"; done 
  cd ..   
done
```


**PS** change 320k to what your personal requirements are


**PS2**   if you want the same but to remove original file then use this **[COLOR="DarkRed"]carefully of course[/COLOR]**


```
for i in */
do
  cd "$i"
  for f in *.mp3; do ffmpeg -i "$f" -acodec libvorbis  -ab 320k "${f%.mp3}.ogg"; done  **&& rm *.mp3**
  cd ..   
done
```


**This script can also be used for most bulk audio and video conversion using ffmpeg**

=======================================================

You can also use sound**k**onverter or sound**c**onverter if you prefer a gui program

---

### Post by coffeecat on 2011-08-17
> **shantiq said:**
> 
ok yes to flac no sense as lossless and mp3 lossy

but to ogg perfectly sound idea

I'd disagree and say the other way round. If you convert mp3 (which has already lost some definition) to ogg, you'll lose even more because ogg is lossy. It's the same as with repeatedly saving jpegs - you lose a bit each time.

Convert mp3 -> flac and you won't get back what was lost in the original mp3 coding, but you won't lose any more. Yes, it doesn't make much sense in terms of file size, but in retaining as much audio quality as you can it makes perfect sense. If I was in the OP's situation, I would choose mp3 -> flac every time.

---

### Post by shantiq on 2011-08-17
well coffeecat interesting take but only really good if you are doing just a few files otherwise the size issue might become a real problem       depends if the guy has enough memory space

otherwise same as before


```
for i in */
do
  cd "$i"
  for f in *.mp3; do ffmpeg -i "$f" "${f%.mp3}.**flac**"; done 
  cd ..   
done
```


or again **soundkonverter or soundconverter** if you prefer a gui program

---

