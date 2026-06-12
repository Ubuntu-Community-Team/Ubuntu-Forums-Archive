---
title: "Realplayer Firefox and smi.cgi troubles!"
date: 2009-08-28
forum: General Help
---

### Post by d_yat on 2009-08-28
Ok. So here is the problem:
My dad like listening to music from the website "www.sinhalajukebox.org".
This website uses realplayer's SMIL format thingy. Anyway, so we click to listen to a song, and it realplayer complains that it doesn't know what to do with a "cgi" file. Which is very true, it's a smi file.
So after some playing around, and comparing it to my parent's windows laptop, I noticed something. On windows it saves the file as "smi.cgi.smi" before realplayer gets hold of it, and plays it just fine. On Xubuntu's firefox it is saved as "smi.cgi". (see opening_file2.jpg)
__A rubbish Solution__
So on Xubuntu I tried saving the file with the extra ".smi" at the end. and what do you know, Realplayer can play it!
______________________
Try it yourselves.
[http://www.sinhalajukebox.org/cgi-bin/songs.cgi?action=ShowTracks&artist=A001&compose=0](http://www.sinhalajukebox.org/cgi-bin/songs.cgi?action=ShowTracks&artist=A001&compose=0)
Try that webpage, and select a random song (don't click on the play button, that just doesn't work anywhere). It won't work or unless you save it with the ".smi" at the end.

I thought this was intriguing, so tried it in safemode. Same thing.
Tried on my laptop- OpenGeu: same problem. Windows- Works correctly
Tried on my desktop- Ubuntu: same problem. Windows- Works correctly (and uses Media player classic instead)

___My Question____
What the hell?!?! From this information, I'm going to say the problem is firefox in linux.
1. Why won't it deal with the file properly?
2. Any ideas for me to try to make firefox open it properly.
3. Yes, I do have suitable codecs (proved as it can play it), etc, and yes I have tried reinstalling, and other players. AND yes I know, #3 isn't a question!

Any help will be greatly appreciated!

I've attached screenshots of parents desktop with Xubuntu (Left) against laptop with Windows (right) to help explain. The first shows that in both cases it asks how to open "smi.cgi", but then when saved (picture 2), they have different names.

---

### Post by d_yat on 2009-08-31
*bumping stick* = BUMP

---

