---
title: "ripping seems so complicated"
date: 2010-08-07
forum: General Help
---

### Post by CROLMAC on 2010-08-07
Hi dear people of ubuntu. I'm sorry for such a trivial problem to propose, but the only thing I really have a big problem with is to convert cd files to mp3, so I can listen to them in my 5800. And I haven't even tried to convert films to see them on the same aforementioned phone, but I intend to try my worst... I am using the rythmbox, as they instruct in umpteen tutorials (preferences-music-cd quality ogg-edit-mp3). 
  I can rip the cd fine, but never to mp3. It always gets ripped to ogg and my 5800 can't read this, visibly. It can read wav but the files are very big, and I like to have a lot of music to take with me. Anything I missed? surely yes, but this seems to be such a simple problem that I can't find anyone who had it.
   I have found someone who talked about "soundjuicer" or something, and be warned, I am very clutzy and weary of doing things with the command line. 
  Oh, and btw, I have a eeepc 900, and am using lucid lynx.
   I thank so much whomever could help me, given my limitations. and take care y'all.

---

### Post by darolu on 2010-08-07
Hey I assume your phone is a Nokia 5800 right? Anyways, Rhythmbox can do it, it's quite simple, go to Edit - Preferences and then hit the 'Music' tab, then change the final option to MP3. If you don't have the option you may need to [install the ubuntu-restricted-extras package]("https://help.ubuntu.com/community/RestrictedFormats") so you get all restrictive formats support. I'm including a screenshot with the rhythmbox option you need, it's in Spanish but you should be able to get it.

The program you mentioned "sound-juicer" can be installed from Synaptic or the terminal:
```
sudo apt-get install sound-juicer
```

To convert video files you can use ffmpeg (command line) or programs like AcidRip; you need to rip/transform to mp4, I think the Nokia 5800 supports h.264 codec too.

---

### Post by CROLMAC on 2010-08-07
thanks for the really speedy reply, but I have already done the mp3 as last choice part( have to open the edit window after the ogg format choice.. maybe the ogg format is wrong, just before I open the edit window?)and I always end up with ogg, not mp3. Maybe I'm not doing my choices right? should I go to edit first without choosing the ogg ? will try it.take care, if it doesn't work I'll be back in a jiff

---

### Post by cchhrriiss121212 on 2010-08-07
Sound juicer is a very easy program to use and does not involve any terminal usage, and its also good at tagging, I recommend it. You really do need to install that restricted extras package as well, it can be found in the software centre.

---

### Post by CROLMAC on 2010-08-07
I just tried that but I must have screwed my system with my attempts to download and remove things, and I can't update, download programs and my software center has dissapeared. synaptic doesn't work and I just went to do what you told me and the message is 'can't find file', so either I find another solution( for my update and such) or reinstall...? a bit of a clutz I'm afraid, sorry and thanks

---

### Post by nothingspecial on 2010-08-07
Can you post the errors you are getting please?

To convert your videos to mp4 in one go (this will take a while), assuming they are in avi format

Drag them into your Videos folder

Then open a terminal and (just copy and paste all this stuff)

```
cd ~/Videos
```
```

gedit avitomp4.sh
```

When the window opens up copy and paste the next bit into it then click save and close it
```

#!/bin/bash

#convert avi to mp4
for f in *.avi 
    do 
    ffmpeg -i "$f" -acodec libfaac -ab 128kb -vcodec mpeg4 -b 1200kb -mbd 2 \
    -flags +4mv -trellis 2  -cmp 2 -subcmp 2 -s 320x180 -metadata title="${f%.avi}.mp4" \
    "${f%.avi}.mp4"

done;
```

Back in your terminal
```

chmod +x avitomp4.sh
./avitomp4
```

Go out, get a pizza, have a beer, and when you come back all your videos will have an mp4 version.

:popcorn:

---

### Post by CROLMAC on 2010-08-08
thank you all so much for this info, and especially for the quote at the end of your reply, i suspected as much. I'm going on a trip and just for fun I want to put a movie on my nokia 5800, just because i can, if you see what I mean. take care

---

