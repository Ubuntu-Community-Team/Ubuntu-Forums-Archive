---
title: "Burning music to CD"
date: 2011-08-22
forum: General Help
---

### Post by Dr. Awesome on 2011-08-22
This has been a pestering of mine for a long time now, I've tried writing music files such as .mp3, .wma, and .wav and play them in my car, but none of them work, and when I put the CD in my computer again, none of the music files are there!:mad:

I've used Brasero and K3B to burn them, as well as the default program that just opens up the cd folder, asks you to copy the files and then gives an option to burn them, and I've looked at past threads but none of them seem to have the same problem as me (or else the suggestions don't help at all). Any help please?

---

### Post by kmsalex on 2011-08-22
[http://www.ubuntu-unleashed.com/2008/10/howto-burn-audio-cds-from-mp3-in-ubuntu.html](http://www.ubuntu-unleashed.com/2008/10/howto-burn-audio-cds-from-mp3-in-ubuntu.html)

I like to call it.... Google :popcorn:

---

### Post by Dr. Awesome on 2011-08-23
> **kmsalex said:**
> [http://www.ubuntu-unleashed.com/2008/10/howto-burn-audio-cds-from-mp3-in-ubuntu.html](http://www.ubuntu-unleashed.com/2008/10/howto-burn-audio-cds-from-mp3-in-ubuntu.html)

I like to call it.... Google :popcorn:

Witty ;) But that still doesn't work.

---

### Post by thatguruguy on 2011-08-23
Have you considered the possibility that it may be a hardware problem?

---

### Post by howefield on 2011-08-23
Thread moved to the "*General Help*" forum.

---

### Post by RansomStark on 2011-08-23
I sse gnomebaker to create audio discs that work in normal stereos. The default brasero burner stopped working for me a while ago.

```
sudo apt-get install gnomebaker
```

This guide will show you how it works.

[https://help.ubuntu.com/community/GnomeBaker](https://help.ubuntu.com/community/GnomeBaker)

---

### Post by haqking on 2011-08-23
[http://ubuntuforums.org/showthread.php?t=218165](http://ubuntuforums.org/showthread.php?t=218165)

and in k3b you need  libk3b6-extracodecs which is in synaptic.

or

sudo apt-get install likk3b6-extracodecs

---

### Post by HolgerB on 2011-08-23
Dear Dr. Awesome,

unfortunately your question is **not** awesome !
:lolflag:

> 
This has been a pestering of mine for a long time now, I've tried writing music files such as .mp3, .wma, and .wav and play them in my car,
 but none of them work, and when I put the CD in my computer again, none of the music files are there!

Be more specific....

How do you want to burn your music files to CD ?
What is the target format of your CD ?

Examples: For burning the plain compressed music files (MP3 / WMA / Ogg) to a CD, simply use a data CD as target with a file system your playback device supports.
For conversion of MP3 files on the fly and burning an audio CD things are looking different. Brasero always worked fine for me doing this. For certain compressed formats you might need to convert them to CDA-compatible wave files prior burning them.

Also what means: When you put the CD in your computer again, there are no files there ?
Are you able to produce readable CD / DVD anyhow ?

You see...your questions are not very clear here.

HTH,
Holger

---

### Post by elliotn on 2011-08-23
I have the same problem with CD burning too, am sure it ain't a hardware problem as when I burned on windows using Nero it worked, I will try gnonebaker

---

### Post by Dr. Awesome on 2011-08-23
> **RansomStark said:**
> I sse gnomebaker to create audio discs that work in normal stereos. The default brasero burner stopped working for me a while ago.

```
sudo apt-get install gnomebaker
```

This guide will show you how it works.

[https://help.ubuntu.com/community/GnomeBaker](https://help.ubuntu.com/community/GnomeBaker)

Same problems as the other writers, unfortunately :/ It said it completed it but when I put the CD back in just to check, it was blank. Is there an option I'm supposed to check-off, such as BurnFree? I did click Audio CD, and the options were Eject Disk, BurnFree and Dummy Write.

---

### Post by Dr. Awesome on 2011-08-23
> **HolgerB said:**
> Dear Dr. Awesome,

unfortunately your question is **not** awesome !
:lolflag:



Be more specific....

How do you want to burn your music files to CD ?
What is the target format of your CD ?

Examples: For burning the plain compressed music files (MP3 / WMA / Ogg) to a CD, simply use a data CD as target with a file system your playback device supports.
For conversion of MP3 files on the fly and burning an audio CD things are looking different. Brasero always worked fine for me doing this. For certain compressed formats you might need to convert them to CDA-compatible wave files prior burning them.

Also what means: When you put the CD in your computer again, there are no files there ?
Are you able to produce readable CD / DVD anyhow ?

You see...your questions are not very clear here.

HTH,
Holger

Sorry if my questions aren't clear for you, I'm sort of a newbie when it comes to advanced computer talk. 

I am unable to produce readable CDs (if I'm understanding this correctly), and I just want some music files that I had on my phone in mp3 and wma formats to be burned onto a CD that can be played in car stereos and such. I've been trying with audio formats (because that seemed obvious to me) but since they aren't working I'm currently going with Data CD format (again if that's what you're talking about with the target format :/).

I know it's not a problem with my computer, although it may be Ubuntu; I have written music files AND data files to CDs before on Windows, and that worked just fine.

---

### Post by oldos2er on 2011-08-23
In the past I've used gnomebaker to create audio CDs, using dao and burning speed at 1x. I've got a couple older CD players around that are kind of fussy about the CDs they accept.

You should be able to do this with k3b too.

---

### Post by HolgerB on 2011-08-24
> **Dr. Awesome said:**
> Sorry if my questions aren't clear for you, I'm sort of a newbie when it comes to advanced computer talk. 
No problem. It is just not easy to help if you do not clearly describe the problem in the first place.


> **Dr. Awesome said:**
>   
I know it's not a problem with my computer, although it may be Ubuntu; I have written music files AND data files to CDs before on Windows, and that worked just fine.
I do not know what the others think but to me burned CD's which are empty afterwards do sound like a problem with your computer, the medias, Ubuntu or the way you burn a DVD / CD.

I used various derivates of Debian plus Archlinux and never had any issues burning data DVD/CD medias.
At least for standard Joilet / UDF / ISO filesystems.

---

