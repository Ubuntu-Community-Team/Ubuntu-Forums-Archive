---
title: "Playing MP3s transfered from windows"
date: 2006-05-30
forum: General Help
---

### Post by evandec on 2006-05-30
I have loaded all of my MP3s from my old windows hard disk and am trying to load them into any mp3 player. I have tried amarok, banshee and rythmbox and none of them will play my MP3s. 

Amarok refuses to load them, saying there not aproriate files, Banshee just wont play them and Rythmbox says there not streaming media. 

Whats up?

---

### Post by aysiu on 2006-05-30
Have you read this?
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by AirRaven on 2006-05-30
[QUOTE=evandec]I have loaded all of my MP3s from my old windows hard disk and am trying to load them into any mp3 player. I have tried amarok, banshee and rythmbox and none of them will play my MP3s. 

Amarok refuses to load them, saying there not aproriate files, Banshee just wont play them and Rythmbox says there not streaming media. 

Whats up?[/QUOTE]
Open up Synaptic and install the "w32codecs" package- it adds support for most of the formats that you may be used to in Windows, like MP3. 

I think it's in the Universe section.

---

### Post by evandec on 2006-05-30
[QUOTE=AirRaven]Open up Synaptic and install the "w32codecs" package- it adds support for most of the formats that you may be used to in Windows, like MP3. 

I think it's in the Universe section.[/QUOTE]

[QUOTE=patrick295767]When you type : 
```
sudo bash 
network-admin
```
  
Do you see your wireless card ? 'cos It can be also a matter of enabling...
Don't know more.[/QUOTE]


Thanks for the help. That was the problem. I guess I am so used to windows I am not even sure to look in ubuntu or where to look online for help.

Thanks for the constant help for a newbie.

---

