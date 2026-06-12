---
title: "help writing first script in vim"
date: 2011-03-08
forum: General Help
---

### Post by btf18 on 2011-03-08
[FONT=Verdana]Hey there,

Im just learning scripting now in the text editor vim. I downloaded vim and seem to have it going fine, it looks a bit like the terminal, well i guess it takes over the terminal when i type vim and press enter. So i typed my first script as:
[/FONT][FONT=Verdana]#!/bin/bash
# My first script

echo "Hello World!"

[/FONT][LEFT][FONT=Verdana]Now apparently the next step is to save it. If someone could please tell me how to save it that would be much appreciated, and then i can continue the "writing my first script" tutorial :)

Thank[/FONT]s
[/LEFT]

---

### Post by wojox on 2011-03-08
Hit the Esc key then :wq!

---

### Post by WorMzy on 2011-03-08
If you're just starting out using vim, then I recommend that you run through vimtutor at least once.

Just open a terminal and run
```
vimtutor
```

---

### Post by amysmith28 on 2011-03-08
I am sorry I can't help you, because I am a newbies,too.

---

### Post by 1clue on 2011-03-08
I strongly recommend going ALL THE WAY THROUGH the tutorials, and then continue on through the rest of the documentation.  People tend to learn so much and then stop learning.

For example, :x = :wq

Or rather, :x = save and quit.  :w = write (save) and :q = quit.

After awhile, if you use vim the way I do, your bottleneck will be the speed at which you can type.  Learn the shortest way to get something done and then USE it.

I'm a professional software developer.  I stopped using vim as my primary editor only a few years ago.  Eclipse came out and finally the intellisense made the pain of an IDE worthwhile.  I now switch back and forth fairly often, and also use TextMate on the Mac.

---

### Post by btf18 on 2011-03-08
Thanks all! So 1Clue, do you mean you recommend going all the way through the 'vimtutor' tutorial from the terminal, or the tutorial i have started on the linuxcommand.org website?

---

### Post by 1clue on 2011-03-08
Either.  Both.

I didn't start out with vim.  I started with vi on commercial UNIX, before vim ever started.  Been at it that long.

I strongly recommend that you go through whatever official documentation is currently recommended, and then go buy a book on regular expressions and learn them forward, backward and sideways.  It may look like gobbledygook, but your ability to understand regular expressions will multiply the usefulness of absolutely any UN*X system, and especially any type of app like vim.

---

### Post by btf18 on 2011-03-08
hmm, sounds like wise advice to me! It might even help with scripting in non-unix systems? Better general understanding and all that and proabably a lot of the same code is used on windows etc? I know just from going through my friends mac that a lot of the command line is the same as linux

---

### Post by 1clue on 2011-03-08
Vim is available for just about anything.  I use it on a Mac, and I've installed it on Windows.

Even more so, regular expressions (regex) are widely used through programming in all sorts of languages.  Unfortunately the syntax differs with a dozen or more dialects, so you need to pay attention.

I currently use groovy and java programming, and regex is alive and well in both of those.  Most UN*X scripting languages use regex.  A DOS command line uses regex when you type *.txt.  SQL uses them, and I imagine any other language you might choose too.

---

### Post by btf18 on 2011-03-08
Got it. regex is very widely used in programming, and imperative to learn for programmers. i've indeed used it in command line already. I would imagine they will be taught in my ICT diploma, however i wish to get ahead of my course content, as a great big earthquake struck 9 minutes before my first class on the second day of my diploma and i havent heard when course will start back yet. Im in christchurch, NZ. you've probably seen it on the news xP Anyways thanks for the advice!

---

### Post by 1clue on 2011-03-08
Wow.  Peace man.

Don't get much in the way of earthquakes over here, it's more in the nature of tornadoes.  I'd be totally lost in an earthquake.

Good luck.

---

### Post by btf18 on 2011-03-12
Thanks. Japan just got it worse, theyre on the border of the same tectonic plate as us, the pacific plate, so the whole plates moving id say. Vim tutor is torture, It says its 25 mins but its 4 hours of learning how to delete and enter text and move the cursor. I'm 61% through it, looking forward to getting it over and done with so i can learn the actual scripting.

---

### Post by danbuter on 2011-03-12
Spending extra time now learning vim will save you lots and lots of time later. Vim will be around as long as Linux and BSD are, so taking a week or two to really, really learn it will benefit you the rest of your life, if you're going into the computer field.

---

