---
title: "1080p films are lagging."
date: 2010-01-31
forum: General Help
---

### Post by KanineN on 2010-01-31
Hello!

When I try to watch a 1080p trailer that I downloaded the film is lagging. It randomly lags for about a second or so and then go back to normal. And sometimes the picture disappears and then comes back. I have a AMD Dual Core Processor 5050e and I am running 64-bits. My graphic card is NVIDIA Geforce 8300 with the latest driver.

---

### Post by Vaphell on 2010-01-31
what do you use to watch 1080p stuff?
If i am not mistaken there is no hardware acceleration by default so decoding is done by the CPU alone. Reportedly with some nvidia cards you can accelerate decoding, read about mplayer compiled with VDPAU support, though i am not sure if your nvidia qualifies.

---

### Post by KanineN on 2010-02-01
> **Vaphell said:**
> what do you use to watch 1080p stuff?
If i am not mistaken there is no hardware acceleration by default so decoding is done by the CPU alone. Reportedly with some nvidia cards you can accelerate decoding, read about mplayer compiled with VDPAU support, though i am not sure if your nvidia qualifies.

Why should I not watch 1080p clips? 


I have follwed [this]("http://ubuntuforums.org/showthread.php?t=1037625") guide but I still don't get it to work. The audio is out of sync and I miss the option to fast forward and so on.


EDIT: I have also downloaded [https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)
 
But the poster said "The trick is to make sure you have only this ppa enabled that has mplayer. Trust me, it works if setup right. "

How do I do that?

---

### Post by KanineN on 2010-02-06
bump, Am I screwed or can anyone help me with this?

---

### Post by stoneage on 2010-02-06
I can watch and stream 1080p trailers with a 1.86 dual core and 2 GB RAM. I just tested with the Simpsons Movie and the Bourne Ultimatum, both as mp4. 

I can't tell you why it doesn't run on your system, but it can be done without difficulty using movie player, sm player, vlc.

Which video player are you using?

---

### Post by KanineN on 2010-02-10
I am using VLC and mplayer with VPDAU but I don&#836;t know if it is working correct.

---

### Post by stoneage on 2010-02-10
Have you installed 'ubuntu-restricted-extras' and 'non-free-codecs'?

---

### Post by KanineN on 2010-02-11
> **stoneage said:**
> Have you installed 'ubuntu-restricted-extras' and 'non-free-codecs'?

Yes I have medibuntu repository

---

