---
title: "Audio CD Extractor Doesn't Work"
date: 2010-01-19
forum: General Help
---

### Post by Bradj47 on 2010-01-19
I'm trying to extract files off of an audio CD using the program that came with Ubuntu. In the preferences I set the format to FLAC but when it's done and I open up the file manager, all the files are mp3. When I try to play the file with Songbird it tells me it can't read the codec. What's going on? I've extracted the music off of CDs before.

---

### Post by ron999 on 2010-01-19
Have you got flac installed?
```
sudo apt-get install flac
```

---

### Post by Bradj47 on 2010-01-19
> **ron999 said:**
> Have you got flac installed?
```
sudo apt-get install flac
```

yep: 

```

brad@rockstar:~$ sudo apt-get install flac
[sudo] password for brad: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flac is already the newest version.
flac set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
brad@rockstar:~$ 

```

---

### Post by RedRat on 2010-01-19
> **Bradj47 said:**
> I'm trying to extract files off of an audio CD using the program that came with Ubuntu. In the preferences I set the format to FLAC but when it's done and I open up the file manager, all the files are mp3. When I try to play the file with Songbird it tells me it can't read the codec. What's going on? I've extracted the music off of CDs before.
It would really help if you could be a bit more clear on exactly what program you were using. Some of these programs do not rip to FLAC only mp3.

---

### Post by Bradj47 on 2010-01-19
> **RedRat said:**
> It would really help if you could be a bit more clear on exactly what program you were using. Some of these programs do not rip to FLAC only mp3.

It's the one that comes with Ubuntu. It's called... Sound Juicer.

---

### Post by ron999 on 2010-01-19
Yes,
With sound-juicer go into edit > preferences
Select cd quality lossless flac
Then 'edit profiles'
Select flac then edit.
Where it says **gstreamer pipeline** my entry is:-
> audio/x-raw-int,rate=44100,channels=2 ! flacenc name=enc


Check if yours is the same.

---

### Post by Bradj47 on 2010-01-19
> **ron999 said:**
> Yes,
With sound-juicer go into edit > preferences
Select cd quality lossless flac
Then 'edit profiles'
Select flac then edit.
Where it says **gstreamer pipeline** my entry is:-


Check if yours is the same.

Yep, mines the same.

---

