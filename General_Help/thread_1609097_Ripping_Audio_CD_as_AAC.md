---
title: "Ripping Audio CD as AAC"
date: 2010-10-29
forum: General Help
---

### Post by sarin_cv on 2010-10-29
I tried sound juicer for this purpose but I don't know how to set the bitrate in that. By default it rips at 128k I guess but I need to rip at 320 kbps. I also downloaded neroAacEnc and tried to use it with k3b by adding an entry in external encoding tools with command  neroAacEnc -if %f -of %n. Please tell me any application which can rip at higher bit rates.

---

### Post by cmcx_linux on 2010-10-29
For k3b you don't add nero, you add codec libraries such as libflaac. These are the greyly legal status extras that you can add to k3b.
[http://k3b.plainblack.com/requirements](http://k3b.plainblack.com/requirements)
I suggest opening your terminal, install aptitude and start aptitude search flaac or lame or whatever they suggest as requirements.

I order to "see" encrypted DVDs on linux, you need libcss2 which is not found in the default bunch. I suggest adding medibuntu to your repo list and install the stuff from there.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
[http://packages.medibuntu.org/](http://packages.medibuntu.org/)

Oh, and wasn't aac lossless? Why would it have a bitrate? You might be making mp3s by mistake. I also suggest to try ogg. Is opened, free, well supported and has a high compression/quality rate.
Have a happy and enriching media experience.

---

### Post by sarin_cv on 2010-10-29
AAC is lossy.... it's FLAC which is lossless... I have already installed libfaac and faac... but k3b  is not showing these options...

---

### Post by cascade9 on 2010-10-30
> **cmcx_linux said:**
> Oh, and wasn't aac lossless? Why would it have a bitrate? You might be making mp3s by mistake. I also suggest to try ogg. Is opened, free, well supported and has a high compression/quality rate.

Nah, AAC isnt lossless......you've probably got confused with ALAC (apple lossless audio codec), which uses the same .m4a extension. 

BTW, all the lossless media flies do have a bitrate.  

UI'm not surwe that anyonwe who is thinking about AAC would go wioth .ogg vorbis, but I'm basing that on most people wanting aac have an ipod. I cant think of any good rason to use aac if you dont have an apple player, and even with one, I'd rather use mp3 anyway.

---

### Post by sarin_cv on 2010-10-30
But I've heard that AAC is better than mp3 in terms of quality...also my sony ericsson phone supports aac... so decided to test the quality.....

---

### Post by cascade9 on 2010-10-30
Your far more likely to be limited by the DAC (digital analog converter) or DSP (digital signal processing) than by codec quality differences.

---

