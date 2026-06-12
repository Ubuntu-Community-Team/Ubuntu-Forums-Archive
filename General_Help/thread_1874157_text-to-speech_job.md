---
title: "text-to-speech job"
date: 2011-11-02
forum: General Help
---

### Post by hyfanious on 2011-11-02
:) hi
I need a solution for this:
having some sentences that have been saved in a text file, I need a novel method to do a text-to-speech job, of course automatically, that save for each sentence a saved sound file (like ogg or amr or ...) related to that specific sentence and do it automatically for all of them,
tnx in advance

---

### Post by gunksta on 2011-11-02
Not sure why this is an awkward question, but here's one thought.

[http://techbase.kde.org/Development/Tutorials/Text-To-Speech](http://techbase.kde.org/Development/Tutorials/Text-To-Speech)

Two notes:
[LIST=1]
[*]I have never used this. Dunno how well it works.
[*]This is a KDE app, it will drag in quite a few deps if installed on a straight Ubuntu system. This isn't really an issue for most users with today's hard-drives. Just don't freak out when this thing installs a bunch of stuff.
[/LIST]

---

### Post by hyfanious on 2011-11-03
thanks for ur helping

1. I used "awkward" related to SAVING part :D (just kidding)
I do NOT need a just text-to-speech program,
I demand a text-to-saved,SPEECH,recorded,FILE ;)

let me explain whole problem
I use "mnemosyne", the sentences that have been entered has no speech files, being about 1500 sentence, it's too annoying to record an audio file for each of them, so I am looking for a program that can do this instead of me, so it may help if u can suggest me ,also, a program that can read out of the "question part of mnemosyne"

tnx :)

---

### Post by hyfanious on 2011-11-04
bump

---

### Post by lisati on 2011-11-04
The espeak command might be of some help.

---

### Post by hyfanious on 2011-11-04
yeappp tnx aloottttttttt
espeak "text" -w /path/name.wav

---

### Post by Ronniety on 2011-11-04
I'm trying to ask the doctor a question about... an awkward subject, and I don't know how to bring it up

I would like to show you my sites of 
      [Moncler Coat](http://www.bestmonclercoats.com/)   &#65281;

---

### Post by mörgæs on 2011-11-04
Changed the title to a more descriptive one.

---

### Post by hyfanious on 2011-11-04
yeap tnx :D
I've never thought it could be so simple as what it is ;)

---

### Post by coldraven on 2011-11-04
Please show us your finished automated script.
I presume it would be something like


#! /bin/bash
for linein "textfile"
do espeak "text" -w /path/name.wav
fi

But as you can see my bash skills are very poor :(

---

