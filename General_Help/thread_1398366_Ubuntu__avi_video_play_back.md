---
title: "Ubuntu  avi video play back"
date: 2010-02-04
forum: General Help
---

### Post by TheMixtureMedia on 2010-02-04
Hi there I am running Ubuntu 10.04 with all updates. Here is my problem and it was happening in 9.10 as well. I can not watch avi videos I get the sound but no picture. I have tried mplayer, vlc and dragon. If I reset the computer it comes back untill I change the file to another avi file. Can someone help with this please.

Thanks

---

### Post by Leppie on 2010-02-04
try installing the windows codecs:
```
sudo apt-get install w32codecs
```

or if you have a x64 system, like me:
```
sudo apt-get install w64codecs
```

---

### Post by TheMixtureMedia on 2010-02-04
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w64codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w64codecs has no installation candidate

thats what it tells me anythoughts

---

### Post by Leppie on 2010-02-04
did you add the medibuntu repo?
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

---

### Post by TheMixtureMedia on 2010-02-04
I did what you said to do and that installed but when I tried watching a movie it would not show the picture but you could hear the sound.

---

### Post by doas777 on 2010-02-04
ok, the answer if it is a codec problem, is to add the medibuntu repos and install the ubuntu-restricted-extras package. 
I suspect however that your issue may be a vid card driver problem, rather than codec, as usually a file won't play without the appropriate codecs. 

what kind of vidcard do you have and hvae you installed a 3d capable driver for it?

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Leppie on 2010-02-04
> **TheMixtureMedia said:**
> I did what you said to do and that installed but when I tried watching a movie it would not show the picture but you could hear the sound.
so you also installed the w64codecs?

---

### Post by TheMixtureMedia on 2010-02-05
I have a nvidia 8500gt with the latest drivers that are downloaded and I have install the win 64 drivers and I am doing a big update right now so I will let you know oh and I have the ubuntu rest files installed.

---

### Post by doas777 on 2010-02-05
if it still fails after adding mediubuntu and the w64codecs, try running this line

```
sudo apt-get install ubuntu-restricted-extras smplayer vlc
```

that will install a wide range of codecs, sun java, adobe flash, and a couple more robust media players. 

Totem is the most well rounded media player, but has some trouble with some codecs and resolutions.

VLC will play most any kind of file, but has issues with quality on some files(poor dithering, jumpiness, poor audio).

mplayer is the best backend media player, but the user interface sucks. smplayer is a better frontend on top of mplayer, but is still a bit clunky and can do weird things when used with a older version of mplayer.

---

### Post by TheMixtureMedia on 2010-02-05
Well I did what you told me to to do and tried smplayer after the install and still same issue sound but no picture.

---

### Post by doas777 on 2010-02-05
try a differant file. the one you are using may be damaged. also try it in vlc once just to make sure.
is it a 1080i file? if so what kind of cpu do you have?

---

### Post by HiImTye on 2010-02-05
post the output of
```
aptitude search restricted-extras
```

---

### Post by Cabs21 on 2010-02-05
did you install a cairo dock or any kind.  I had this same problem with VLC when I installed cairo dock.  I recently did a reinstall and did not install cairo dock and still have a fully functioning VLC.  When i did have cairo dock installed I went into VLC and opened the options or preferences menu.  Then opened the video tap on the left and under output there is a list of output types.  Change it to openGL or GNOME or something that you think will work then restart VLC and try another avi file.  IF it does not work try a different format.  If your desperate you can watch it in ASCII format which is funny to watch.  Good luck.

---

### Post by Cabs21 on 2010-02-05
Click [here]("http://ubuntuforums.org/showthread.php?t=1391888") for similar thread

---

### Post by andrew.46 on 2010-02-05
Hi TheMixtureMedia,

> **TheMixtureMedia said:**
> I can not watch avi videos I get the sound but no picture. I have tried mplayer, vlc and dragon.

Can you try playing the problem file from the commandline with the following syntax:

```
mplayer -v **[COLOR="Blue"]problem_file.avi[/COLOR]**
```

and of course replace '*problem_file.avi*' with the actual name of your file. Post the actual command and full terminal output here and there should be enough hints in this output to diagnose the problem.

All the best,

Andrew

---

