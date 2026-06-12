---
title: "I could use a advice from a more experienced user."
date: 2005-02-22
forum: General Help
---

### Post by New@linux on 2005-02-22
I have had linux for only a few days and i dont know anything so if you can help me say it in a way that i can do it :)

Ok here i go!

1. i have pppoe connection and there is no direct support for it in ubuntu, so i installed rp-pppoe and i got it working, but before i can connect i must disable my networkadapter, there seems to be a problem with ip:s (i have 2 of them one for lan and one for pppoe) so is there any easy way to make my lan and my ppoe connection working at the same time? and how i can get ubuntu to connect with pppoe in start up?

2. How can i get my tv and monitor working separately, so that i could watch a movie from tv while using my computer? with nvtv it seems to be a bit tricky (if possible at all ), i cant get monitor out of 2nd head. 

3. my third problem is with mp3, i have optical out so i can listen sounds trough my stereos, with mplayer and movies sounds works perfectly, but with xmms and mp3 i cant get sound out.. equalizer works so i think it playes them correctly, but silently :) I tried to open mp3 files with mplayer and the problem is same, player seems to play the file but i cant hear the music. And theres coming light out of optical cable during play so it doesnt disable optical port.

I m grateful for any helpfull advices and thank you:)

---

### Post by kassetra on 2005-02-22
[QUOTE=New@linux] 
3. my third problem is with mp3, i have optical out so i can listen sounds trough my stereos, with mplayer and movies sounds works perfectly, but with xmms and mp3 i cant get sound out.. equalizer works so i think it playes them correctly, but silently :) I tried to open mp3 files with mplayer and the problem is same, player seems to play the file but i cant hear the music. And theres coming light out of optical cable during play so it doesnt disable optical port.

I m grateful for any helpfull advices and thank you:)[/QUOTE]

Ok, let's start with the one I can help you with right away:
1. Have you installed the mp3 libraries (I'm assuming you have)
2. Have you checked your volume? (I'm assuming you have done this as well)
3. Have you checked your pcm volume?  (This is the one I'm thinking might be causing the silent sound)

---

### Post by New@linux on 2005-02-23
Thanks for answering kassetra, but problem is only with optical output. Mp3 s are working perfecly from analog out (headphone). 
(i checked pcm volume,  and im not sure about library files being the problem, mp3 library files are only doing the stream decoding? and  my analog output working it takes this option out?)

---

### Post by m4ng0 on 2005-02-23
[QUOTE=New@linux]
...
1. i have pppoe connection and there is no direct support for it in ubuntu
[/QUOTE]

Have you tried:
sudo pppoeconf
?

---

