---
title: "Just a Question."
date: 2010-05-03
forum: General Help
---

### Post by TheStoneCold on 2010-05-03
Hello guys, just me with two questions.
I recently moved from Windows to Ubuntu 9.10 and I have encountered a problem.
I have no sound anymore, it isn't my speakers because i tested them on my laptop, when I booted back into my old Windows partition I had sound, so it can't be my sound card.
Please help me...:(

---

### Post by spiky001 on 2010-05-03
Hi I take it is not muted? have you run the updates as well?

---

### Post by dino99 on 2010-05-03
install paprefs and gnome-alsamixer

check into :system prefs sound if your driver is recognized

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by TheStoneCold on 2010-05-03
No, my sound is not muted, I just did that test on Dino99's link and here it is.
[http://www.alsa-project.org/db/?f=8d083090b266ea7193e15edbf61138f452808c40](http://www.alsa-project.org/db/?f=8d083090b266ea7193e15edbf61138f452808c40)

---

### Post by TheStoneCold on 2010-05-03
> **dino99 said:**
> install paprefs and gnome-alsamixer

How do I do that?

---

### Post by dino99 on 2010-05-03
> **TheStoneCold said:**
> How do I do that?
into console :

sudo apt-get install paprefs
sudo apt-get install gnome-alsamixer
 (then goto apps - sound - gnome-alsamixer and tweak settings)

or goto synaptic: system - admin - synaptic and select these packages

---

### Post by TheStoneCold on 2010-05-03
Got them both now, do I need to restart?
Also you wrote sudo apt-get install gnom**r**-alsamixer

---

### Post by TheStoneCold on 2010-05-03
Pictures...
[IMG]http://i42.tinypic.com/v7fjig.png[/IMG]
[IMG]http://i39.tinypic.com/nlr96f.png[/IMG]
[IMG]http://i40.tinypic.com/9a7l0g.png[/IMG]
[IMG]http://i43.tinypic.com/21owz0h.png[/IMG]

---

### Post by TheStoneCold on 2010-05-03
Help please? Anyone? :(

---

### Post by rcayea on 2010-05-03
I;m not sure why your output tab is showing only a dummy listing. I am wondering why isn't your sound card listed?

On my system I always, when i fresh install, have to go to output tab and select my sound card (which isn't onboard sound).

---

### Post by TheStoneCold on 2010-05-03
Maybe I need a linux version of my sound card drivers?

---

### Post by rcayea on 2010-05-03
this command should tell you the sound card you are trying to use:

cat /proc/asound/card0/codec#* | grep Codec

Then you can find the drivers easier.

---

### Post by TheStoneCold on 2010-05-03
matt@matt-desktop:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC888

---

### Post by pcura on 2010-05-03
Try different mirrors to download 9.10.........probably its a bad copy that you got.

---

### Post by TheStoneCold on 2010-05-03
I got my disk from ubuntu wesbite...
I don't see how it is a bad copy,  they made the disk for me all I did was request it and wait 5 weeks.

---

### Post by pcura on 2010-05-03
i got kubuntu from their servers too but still its bad.........i'm just giving a suggestion.

---

### Post by TheStoneCold on 2010-05-03
Working now.
/Thread.

---

