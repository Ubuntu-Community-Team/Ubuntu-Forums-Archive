---
title: "Batch convert mp3 to m4a using Soundkonverter"
date: 2011-10-04
forum: General Help
---

### Post by rmcellig on 2011-10-04
I am trying to figure out how to convert some mp3 files to m4a 128 bit format using Soundkonverter and can't see an option to do this. Is this possible using Soundkonverter?

---

### Post by dniMretsaM on 2011-10-04
soundKonverter can easily do this.


[LIST]
[*]When the settings dialog appears after you add your files, click on the Detailed tab.
[*]Click on the drop down list labeled Output format: and select acc.
[*]Changing the plug-in (drop down menu labeled Use Plugin[NOPARSE]:)[/NOPARSE] is optional. The default is FAAC and will do just fine.
[*]Now click on the Mode: menu and select Bitrate then drag the slider to 128 kbps (or you can click on the arrows over to the right or just type 128 in the text box).
[/LIST]


Those are the settings you need for the converting to M4A. Enjoy. However, I must say that you should use Ogg Vorbis instead.

---

### Post by rmcellig on 2011-10-04
For some reason the encoding is failing. Under use plugin, I only have ffmpeg.

---

### Post by HermanAB on 2011-10-04
Read up on find and sox.

---

### Post by dniMretsaM on 2011-10-04
> **rmcellig said:**
> For some reason the encoding is failing. Under use plugin, I only have ffmpeg.

Install the restricted extras package for the *buntu you're using (they each have a separate one):

Ubuntu:
```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```Kubuntu:
```
sudo apt-get update
sudo apt-get install kubuntu-restricted-extras
```Lubuntu:
```
sudo apt-get update
sudo apt-get install lubuntu-restricted-extras
```Xubuntu:
```
sudo apt-get update
sudo apt-get install xubuntu-restricted-extras
```That should add the option for FAAC.

EDIT: If you don't want to install all the components of the restricted extras package, you can install just the ACC encoder:
```
sudo apt-get update
sudo apt-get install libfaac
```

---

### Post by rmcellig on 2011-10-04
Great! Thanks! That's what I was looking for. I will try that out. Does this mean that I will also be able to use Soundconverter as well to convert to m4a format? I also have that app installed as well. 

The reason I use m4 a format is because I use iTunes for my radio show at the University I do my show at and m4a files take up less space on my portable HD than mp3 files do.

Randy

---

### Post by rmcellig on 2011-10-05
That worked perfectly. Thanks!! I hope that someday we won't have to always add extra files to get something working and that it will just work. :)

---

### Post by dniMretsaM on 2011-10-05
> **rmcellig said:**
> That worked perfectly. Thanks!! I hope that someday we won't have to always add extra files to get something working and that it will just work. :)

Including those files in could cause legal problems. Otherwise Canonical would include them and it would 'just work.' Anyway, glad you got it to work!

---

### Post by rmcellig on 2011-10-05
Now I understand. Thanks again!!

---

