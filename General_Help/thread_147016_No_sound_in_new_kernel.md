---
title: "No sound in new kernel"
date: 2006-03-19
forum: General Help
---

### Post by GregaS on 2006-03-19
I have just compiled new kernel (2.6.14) with this tutorial: [http://www.ubuntuforums.org/showthread.php?t=84174](http://www.ubuntuforums.org/showthread.php?t=84174) but now I don't have sound anymore. If I try to play MP3, amarok starts and it looks like music is playing but I can't hear any sound. What should I do?

---

### Post by gingermark on 2006-03-19
What sound card do you have?

---

### Post by GregaS on 2006-03-19
It's some cheap 4.1 card. I don't know exactlly.

---

### Post by incubus on 2006-03-19
Can you check
$ lspci

incubus

---

### Post by GregaS on 2006-03-19
C-Media Electronics Inc CM8738 (rev 10)

---

### Post by GregaS on 2006-03-20
Anyone? I would really like to use 2.6.14 kernel because it is much faster than the current 2.6.12.

---

### Post by imranj on 2006-03-20
try this in console

amixer or alsamixer

and check for wave bar and increase it, then sound should come ok.

report back how it went?

---

### Post by rattking on 2006-03-20
did you include the C-Media 8738 driver when you configured your kernel? 
or try loading the module? if it was built
sudo modprobe snd-cmipci

---

### Post by GregaS on 2006-03-21
imranj master volume is at 100%.
rattking: command sudo modprobe snd-cmipci doesn't work. Where in that tutorial should I include C-Media 8738 driver? I've made everything just like in tutorial.

---

### Post by rattking on 2006-03-21
the driver would be in 
make menuconfig
Device Drivers ---> Sound ---> Advanced Linux Sound Architecture  ---> PCI devices  --->  < > C-Media 8738, 8338 
make sure its M (module) or * (built it)
module is probably safest
if it was not enabled then enable it <M> and rebuild your kernel as in the how-to

---

### Post by GregaS on 2006-03-21
Now i'm very confused :???:  When do I have to do "make menuconfig" ?

---

### Post by rattking on 2006-03-21
or make xconfig
whatever you did when you compiled that kernel the first time
just make sure the driver is enabled in your custom kernel..

---

### Post by GregaS on 2006-03-21
This is strange:

[[img]http://www2.shrani.si/thumbs/trans1350685.png[/img]](http://www2.shrani.si/files/trans1350685.png)


EDIT: I recompiled kernel again with that settings and sound still isn't working.

---

### Post by GregaS on 2006-03-23
Help? :(

---

### Post by GregaS on 2006-04-01
Can anyone tell me how do I remove this new kernel because I don't need it?

---

