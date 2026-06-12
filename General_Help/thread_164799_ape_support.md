---
title: "ape support"
date: 2006-04-23
forum: General Help
---

### Post by Syco54645 on 2006-04-23
i was wondering how i could add ape support in linux.  i realize that the license that the person made is terrible, but that doesnt change the fact that i have alot of beatles bootlegs in ape that i cannot listen to.  i am looking for quod libet support, but any player will be fine.

thanks

-Syco54645

---

### Post by adamkane on 2006-04-23
I was not able to play .ape in amaroK, so I converted .ape to .ogg with audio-convert. See Post 61 here:
[http://www.ubuntuforums.org/showthread.php?t=82806]("http://www.ubuntuforums.org/showthread.php?t=82806")

You may be able to play .ape with mplayer, if you install the latest version of ffmpeg:
[http://issaris.be/breezy/ffmpeg_0.20060410T134157_i386.deb]("http://issaris.be/breezy/ffmpeg_0.20060410T134157_i386.deb")
 
Takis repository:
 deb [http://issaris.be/breezy]("http://issaris.be/breezy") ./

I didn't go into detail, so just post any questions, you may have.

EDIT:
Due to unstability of the server that previously hosted the repository, Takis has moved the Ubuntu Breezy repository. The new line to add to your /etc/apt/sources.list would be:
 deb [http://alpha.uhasselt.be/takis.issaris/breezy/]("http://alpha.uhasselt.be/takis.issaris/breezy/") ./

---

### Post by hugmenot on 2006-04-23
[QUOTE=Syco54645]i was wondering how i could add ape support in linux.  i realize that the license that the person made is terrible, but that doesnt change the fact that i have alot of beatles bootlegs in ape that i cannot listen to.  i am looking for quod libet support, but any player will be fine.[/QUOTE]

Convert them to FLAC instead if you want to remain lossless and gain universal playback support across all players in Linux.

Ape is dead.

---

### Post by adamkane on 2006-04-23
audio-convert gives you the option to convert to near-lossless .mp3 or .ogg, although I just use standard settings settings myself. 

Just a suggestion. The flac suggestion is good too.

---

### Post by hugmenot on 2006-04-24
The conversion to FLAC would be trivially easy with the lossless audio toolbox &#8220;shntool&#8221;. Unfortunatly the Monkey's audio codec program MAC doesn't allow deconding to stdout and has to be patched first. One more reason why the ape format sucks.

---

### Post by Syco54645 on 2006-04-24
i was thinking about converting to flac, but see in the online bootleg trading world this is frowned upon if i ever intend to distribute the recordings again.  i got mac console to compile for linux and it appears to be working well.

at any rate thanks for the replies

-Syco54645

---

