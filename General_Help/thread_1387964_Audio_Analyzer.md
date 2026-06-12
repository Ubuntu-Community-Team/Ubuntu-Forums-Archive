---
title: "Audio Analyzer"
date: 2010-01-22
forum: General Help
---

### Post by Burky on 2010-01-22
On windows I used Foobar to tell me rather or not a mp3 was CBR or VBR(V0, V1, V2, etc.) or whatever the format the audio file was. On Ubuntu I can't find anything like this? Rhythmbox will only tell me if it's an mp3 and the bitrate, which does help if the mp3 is CBR, but it doesn't for VBR. Any ideas guys?

NOTE: I realised this is in the wrong section after I hit post. IDK how to delete a post, so I'll just leave it.

---

### Post by JiuJitsu500 on 2010-01-22
Audacity is a wonderful program for all sorts of audio tweaks, conversions, recordings (internal and external), editing, etc... I used it to make .wav files into .ogg to get new system sounds (HAL 9000 from 2001: A Space Odyssey lets me know the systems ready, and welcomes me when I log on, and tells me goodbye when i log off, etc lol)

sudo apt-get install audacity

Hope you like

---

### Post by Burky on 2010-01-22
I'm sorry. I'm just not quite sure how Audacity can show me rather or not  VBR MP3 is either v0, v1, v2, v3, or v4?

---

### Post by JiuJitsu500 on 2010-01-22
Hmmm.... wel maybe audacity isn't that advanced, it is a very powerful tool though and I figured maybe it could see beyond just the format... (I've only used to convert... sorry :( )

Sonic visualizer is much more comprehensive, maybe [this]("http://linux.softpedia.com/get/Multimedia/Audio/Sonic-Visualiser-12405.shtml") is closer to what you're looking for?

---

### Post by Burky on 2010-01-22
No, sorry.

I'm looking for something more like this [IMG]http://mediainfo.massanti.com/images/screenshot.png[/IMG]

or

[IMG]http://www1.picfront.org/picture/zD5AALIc/img/FoobarProperties.JPG[/IMG]

---

### Post by JiuJitsu500 on 2010-01-22
Damn... I'm sorry man I'm out of options.... I haven't used anything else :(

Maybe this bump will get more attention though from someone who knows much more than me....

---

### Post by Burky on 2010-01-22
Thanks though

---

### Post by DerranTal on 2010-02-26
The following command works for me in bash to get average bitrates on all mp3 files in the current directory:

```
mp3info -xFra *.mp3 | grep Audio
```You will need the mp3info package. The program will also produce some complaints before the audio info if the files don't have ID3v1 tags (I don't consider this a problem). If you want a simpler command to enter under bash, you can add something like this to ~/.bashrc

```
alias bitrates="mp3info -xFra *.mp3 | grep Audio"
```I hope this helps.

---

