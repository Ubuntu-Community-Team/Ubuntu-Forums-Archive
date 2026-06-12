---
title: "Rip subtitles from OGM/MKV"
date: 2006-03-19
forum: General Help
---

### Post by AlternativeS on 2006-03-19
Can somebody please tell me how I can extract the subtitles from an OGM or Matroska file?  I've checked everywhere, and still can't find an answer.  I want to start burning my Anime to DVDs, and Avidemux only supports external subtitles.  Any help is greatly appreciated.

---

### Post by Trisa on 2006-03-21
For the Matroska files:

Click on this link below and copy and paste the URLs in your sources.list file:
[http://www.bunkus.org/videotools/mkvtoolnix/downloads.html#ubuntu]("http://www.bunkus.org/videotools/mkvtoolnix/downloads.html#ubuntu")

Then:
```
sudo apt-get update
sudo apt-get install mkvtoolnix-mb
``` 
Next: go to your command terminal and type in mkvinfo -g.

Click on File --> Open and open your mkv file. A list should come up. Look for the track that contains the subtitles. For example:

> (MKVInfo) | + A track at 4676
(MKVInfo) |  + **Track number: 4 at 4679**
(MKVInfo) |  + Track UID: 4236937090 at 4682
(MKVInfo) |  + **Track type: subtitles at 4689**
(MKVInfo) |  + Default flag: 1 at 4692
(MKVInfo) |  + Forced flag: 0 at 4695
(MKVInfo) |  + Lacing flag: 0 at 4699
(MKVInfo) |  + MinCache: 0 at 4702
(MKVInfo) |  + Timecode scale: 1.000000 at 4706
(MKVInfo) |  + Max BlockAddition ID: 0 at 4714
(MKVInfo) |  + Codec ID: S_TEXT/SSA at 4718
(MKVInfo) |  + CodecPrivate, length 1328 at 4730
(MKVInfo) |  + Language: eng at 6062
(MKVInfo) |  + **Name: English SSA Subtitles + Karaoke at 6069** 
To rip the subtitles, quit the program and go back to the terminal. Type in something like this:
```
mkvextract tracks AIRMOVIE.mkv 4:subs.ssa

``` 
The number four is the track number where the subtitles are stored. Depending on the file, the number will be different. In my example, the subtitles are in SSA format.

I don't have experience with OGM files, so someone else will have to help you with that.

---

### Post by george_apan on 2006-03-21
And for ogm files you could just mux them to mkv first and then extract the subtitles. Be aware that all that Trisa posted above work only for text subtitles (srt and ssa/***) and not vobsubs. I don't think there is a way to extract vobsubs yet.

edit: Ha! That's funny! Forum believes that _a s s_ is a bad word! It's a subtitle format silly! :D

---

### Post by lcg on 2006-03-21
[QUOTE=george_apan]edit: Ha! That's funny! Forum believes that _a s s_ is a bad word! It's a subtitle format silly! :D[/QUOTE]
And I had always thought it was a body part. Boy, was I wrong. ;)

Lars

---

### Post by AlternativeS on 2006-03-21
Ooohh, thanks ya'll.  Now I'm gonna try it

---

### Post by mc-rpg on 2008-02-17
Install ogmtools. This will install ogmdemux.

In the console on the directory of the file:
ogmdemux -na -nv file.ogm

This will extract just the subtitle.

---

