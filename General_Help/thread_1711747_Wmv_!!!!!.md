---
title: "Wmv !!!!!"
date: 2011-03-21
forum: General Help
---

### Post by elliotbeken on 2011-03-21
Hi all i have looked hard into finding a way to play WMV in kubuntu but with no success.

i have tried to install windoes media player using wine - did not work
i have tried using vlc for windowds with wine - did not work 
i have restricted extras install - still does not work

i have kubuntu 10.10 64-bit

how can i make this work if there is a way 

thanks

---

### Post by synapsys on 2011-03-21
It seems like there is support for wmv's in the restricted-extras package. Use this command to install from a terminal window:

```
sudo apt-get install kubuntu-restricted-extras
```

Check this out for more info
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by deeZee on 2011-03-21
Have you tried the w32codecs package?

[https://help.ubuntu.com/community/Medibuntu#Playing%20Non-Native%20Media%20Formats](https://help.ubuntu.com/community/Medibuntu#Playing%20Non-Native%20Media%20Formats)

Scroll down the page a bit to "With Individual Packages."

---

### Post by elliotbeken on 2011-03-21
nope this still does not work it plays the sounds but on video i have tried vlc and dragon player

---

### Post by elliotbeken on 2011-03-21
sorry deeZee how do i install these ?

sudo apt-get install w32codecs

---

### Post by deeZee on 2011-03-21
Copy and paste the following commands in terminal:

```
wget -c http://packages.medibuntu.org/pool/non-free/w/w64codecs/w64codecs_20071007-0medibuntu1_amd64.deb

```

```
sudo dpkg -i w64codecs_20071007-0medibuntu1_amd64.deb

```

The first command will download the package; the second will install.

---

### Post by SeijiSensei on 2011-03-21
Try [smplayer]("http://smplayer.sourceforge.net/"); it's in the repositories.

---

### Post by elliotbeken on 2011-03-21
nope this still doesn't work, maybe its just the WMV files i am trying to play !

thanks for all the input i will try another WMV video

---

### Post by andrew.46 on 2011-03-22
> **elliotbeken said:**
> nope this still doesn't work, maybe its just the WMV files i am trying to play

Can you give a link to the troublesome video?

---

### Post by elliotbeken on 2011-03-22
its a CBT nugget video on the cisco series.

its a large video !

---

### Post by andrew.46 on 2011-03-22
Even so..... can you share the link if it is legal etc?

Andrew

---

### Post by YfoMp5QBh2 on 2011-03-22
WMP should install in Wine shouldn't it? You could run a virtual computer using VirtualBox and install it in there.
 
I personally don't like WMV/WMA so usually convert it. I'd suggest (if the file isnt humongous!) you change it to a different file container (you could probably get the file size down to something more bitsize then)

---

### Post by TeoBigusGeekus on 2011-03-22
```
ffmpeg -i /path/video.wmv
```
Can you post us the output of this command?

---

### Post by 3rdalbum on 2011-03-22
Some WMV versions aren't yet playable on Linux, from my knowledge. However, VLC for Ubuntu and the W32codecs or W64codecs packages from Medibuntu will be able to play 99% of all videos you'll come across.

---

