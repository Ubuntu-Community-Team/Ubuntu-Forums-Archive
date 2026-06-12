---
title: "Playing .AMV Video Files"
date: 2010-06-03
forum: General Help
---

### Post by dewey_daniels on 2010-06-03
plain and simple how do I watch my old .amv videos. Whenever I try I get this error. > Could not display "/home/derek/Videos/shrek 3 (Ipod).amv".
There is no application installed for RIFF audio files


Problem is being the newbie I am, I have no clue whats so ever how to get around the error. I installed the medibuntu though terminal sense that was restricted codec I thought but nothing.

---

### Post by dewey_daniels on 2010-06-03
bump :(

---

### Post by dewey_daniels on 2010-06-03
Bump and I'll keep doing it untill someone can answer :(

---

### Post by 3rdalbum on 2010-06-04
Firstly, in future I'd suggest not encoding to AMV format. I hadn't heard of the format before so it's pretty obscure, and it's proprietary as well. If the company behind AMV went under, you'd eventually lose the ability to work with these files which is NOT what you want!

Secondly, AMV should be supported by FFMPEG, which means that VLC Media Player should be able to play them. If VLC won't play them, try just using the ffplay command on the command-line:

```
ffplay <drag file onto terminal>
```

It's possible that FFMPEG won't support these files forever; the format has been reverse-engineered so that FFMPEG can play the file. As it's an obscure format, they might accidentally break support for it and very few people would notice.

---

### Post by willyconkz on 2010-12-27
Bumping because it still needs an answer that is something other than the usual negativity. I tried as suggested, not working. The file format is a well known one found on many, many mp3/4 players around the world.

---

### Post by no2498 on 2010-12-27
im not sure if this will help or not but it loads a few more codes for ff
type smplayer in a terminal it tells you how to install it
try it in smplayer
hope it helps

---

### Post by willyconkz on 2010-12-27
No, didn't work, but thanks for being helpful anyway!

---

### Post by willyconkz on 2010-12-27
It seems the loading of smplayer updated something VLC needed, anyway, .amv works now in VLC so thanks mate.

---

### Post by no2498 on 2010-12-27
glad it helped you 
mark the post as solved so it can help others too

---

### Post by willyconkz on 2010-12-27
I am not OP but ok!

---

### Post by no2498 on 2010-12-29
you use the  	Thread Tools to mark it solved
top of the page

---

### Post by willyconkz on 2010-12-29
> **no2498 said:**
> you use the      Thread Tools to mark it solved
top of the page

only works for original poster, which I am not! Maybe a mod could do it, thread tools doesn't give me that option That I can find, sorry.

---

