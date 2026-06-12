---
title: "Listen to music via virtual terminal?"
date: 2010-05-27
forum: General Help
---

### Post by dillandriskell on 2010-05-27
Is it possible? I imagine I'll have to install something, but Google has shed no light for me thus far. And just to clarify, when I say virtual terminal I mean the terminals accessed by CTRL+ALT+(F1-F6). I'm going to be doing a challenge/learning experience where I don't allow myself a graphical interface for a month. This is just to help me learn my way around BASH through adaption. However, if I have to go a month without music I will go insane.
:lolflag:

So, even if this is possible can I listen to music from the internet (youtube, playlist.com, etc.) or just music on my hard drive? And I'm not sure if this thread belongs in Desktop Environments or not, that section seemed to focus on graphical interface. Somebody please correct me if this is in the wrong place.

---

### Post by dino99 on 2010-05-27
open the windows to listen birds  :lol:

---

### Post by polki@mac.com on 2010-05-27
This might be a start.

[http://ubuntuforums.org/showthread.php?t=1014056](http://ubuntuforums.org/showthread.php?t=1014056)

Hope you get some help with the online listening, in that area, I'm incompetence personified :-)

---

### Post by computerx138 on 2010-05-27
VideoLAN (vlc) has a full command line interface, including play x, enqueue x, stop, next etc, etc.

If you run it from a terminal in X, it'll load the full windowed interface. If you Ctrl+Alt+F1 and run "vlc", you get the proper command line interface.

I use it daily as part of my little playlist management script. It's quite good.

You can get VLC from the Ubuntu Software Centre.

---

### Post by dillandriskell on 2010-06-01
> **polki@mac.com said:**
> This might be a start.

[http://ubuntuforums.org/showthread.php?t=1014056](http://ubuntuforums.org/showthread.php?t=1014056)

Hope you get some help with the online listening, in that area, I'm incompetence personified :-)

Thanks! That actually did answer my question. Sorry for the delay by the way.
Looks like I'm going with moc, I tried several others and I liked that one the
best. And as for listening to music on the internet, you can download YouTube
videos using a program called "youtube-dl", then just convert it with ffmpeg
and you're all set.

Thanks for the help!

---

### Post by nothingspecial on 2010-06-01
Did you try cmus?

---

### Post by dillandriskell on 2010-06-01
> **nothingspecial said:**
> Did you try cmus?

Thanks for the suggestion, I actually hadn't. I'm messing with it right now.
It seems like it has a steeper learning curve but it has a lot more potential
over moc. I think I'm going to have to customize the keybindings though,
I'm finding the default rather difficult to remember.

---

### Post by sdennie on 2010-06-01
> **dillandriskell said:**
> Is it possible? I imagine I'll have to install something, but Google has shed no light for me thus far. And just to clarify, when I say virtual terminal I mean the terminals accessed by CTRL+ALT+(F1-F6). I'm going to be doing a challenge/learning experience where I don't allow myself a graphical interface for a month. This is just to help me learn my way around BASH through adaption. However, if I have to go a month without music I will go insane.


This sounds like a fun challenge.  Though not music related, some other things you might find useful in you endeavor would be screen, irssi + bitlbee, mutt, newsbeuter, transmission, and I'm sure you know about the various web browsers (lynx, w3m, etc).  Also, a lot of editors have GUI-like features that you might not learn if you are only using them under X such as multiple tabs, multiple "windows", etc.  Let us know how the experiment goes.

(Sorry if you already knew all of that.  You didn't mention how much research you'd already done.)

---

### Post by tgalati4 on 2010-06-01
sudo apt-get install moc
mocp

---

### Post by nothingspecial on 2010-06-02
> **dillandriskell said:**
> Thanks for the suggestion, I actually hadn't. I'm messing with it right now.
It seems like it has a steeper learning curve but it has a lot more potential
over moc. I think I'm going to have to customize the keybindings though,
I'm finding the default rather difficult to remember.

When I`m learning to use a new cli app I find it useful to use something that will split the terminal in 2 (or 3, 4 .......). Like screen, or dvtm.

```
sudo apt-get install dvtm byobu
```

byobu is ubuntu`s modified version of screen

```
byobu
```

```
dvtm
```

Then press Ctrl+G then C to split the screen. Repeat this a couple of times so you have 4 "windows".

Then press Ctrl+G then G to give yourself a nice grid shape.

(Ctrl+G is dvtm`s escape key - it tells the console that the next key you press is an instruction for dvtm)

Navigate between the windows using Ctrl+G then J (or K to go the other way)

In one "window" run cmus, in the one next to it run man cmus, in another run man dvtm and in the other run man screen.

Once you`ve got all that going, press F2 which will create a new screen session, you can see all the ones you have running on the bottom "panel". Navigate between them using F3 and F4. You can close the one you are currently veiwing by pressing Ctrl+A then K (Ctrl+A is screen escape key ........)

Being able to read the instructions for the app you are trying to learn on the same console is invaluable, I think.

Have fun.

---

### Post by luke2760 on 2010-06-19
In a similar vein, anyone know why audio cuts out when you switch to a virtual terminal? I like to work out of Emacs in a VT from time to time as it blocks out distractions, but for some reason audio stops. It seems like this happened at some point in the past year or so... 

I know it hasn't always done this.

---

### Post by polki@mac.com on 2010-06-19
Maybe you should upgrade from 7.10? It's 3 years old...

---

