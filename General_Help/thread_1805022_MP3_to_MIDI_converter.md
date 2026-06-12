---
title: "MP3 to MIDI converter?"
date: 2011-07-15
forum: General Help
---

### Post by linuxuser12345 on 2011-07-15
Does anyone know of any good .mp3 to .midi converters out there that are free and for Linux?

---

### Post by CatKiller on 2011-07-15
MP3 is a compressed audio format. MIDI is essentially a text format.

You can use some MIDI file as instructions to drive a synth, which will output sound you could encode as MP3, but you aren't going to go the other way.

---

### Post by linuxuser12345 on 2011-07-15
Well, I know there are some mp3 to midi converters for Windows.
Is there a way I can get an MP3 file to open up in a sheet music editing program, like Musescore?

---

### Post by linuxuser12345 on 2011-07-16
Well, I have an audio cable, so why don't I just connect one end of the audio cable to the line-out, and one to the microphone jack? Is there a program out there that can convert incoming sound to the microphone to MIDI?

---

### Post by linuxuser12345 on 2011-07-17
Anyone? :/

---

### Post by sobatsu21 on 2011-07-17
No, that is definitely not going to work. Audio is only ONE WAY! You can take lemons and make lemonade, but you can't take lemonade and expect to make lemons! 

You can use a few linux native apps, though.

---

### Post by linuxuser12345 on 2011-07-17
I can't record through the microphone to make an MIDI? What about something that will open up in Lilypond?

---

### Post by AlphaLexman on 2011-07-17
A MIDI file is like a text file (but not really) for music.

You can't just take 'Stairway to Heaven.mp3' and extract all the notes, chords, and instruments out of it. The MP3 format does not store that kind of data.

See [http://en.wikipedia.org/wiki/MIDI]("http://en.wikipedia.org/wiki/MIDI")

---

### Post by linuxuser12345 on 2011-07-17
Is there any other way I can do convert the audio somehow to open up in Lilypond or MuseScore, or some other program?

---

### Post by AlphaLexman on 2011-07-17
I did find a command line potential option...
```
arecordmidi
```

---

### Post by CatKiller on 2011-07-17
> **AlphaLexman said:**
> I did find a command line potential option...
```
arecordmidi
```

That records MIDI instructions into a MIDI file. Not audio.

What the OP expects to happen just isn't possible. At best, it's recording the output of a guitar tuner. If you've ever used a guitar tuner, you know how rubbish that's going to be.

---

### Post by AlphaLexman on 2011-07-17
> **CatKiller said:**
> What the OP expects to happen just isn't possible.
I know that... But does the OP ??

I simply found arecordmidi via
```
apropos midi
``` 
Without knowing the full structure of the program !!

---

### Post by JC Cheloven on 2011-07-17
This post would have better chances to get more answers in the ubuntustudio subforum. 

As to the original question: the OP is right, the music recognition problem is improving a lot lately (well, the solution of the problem). Poliphonic music is still a chalenge, but monophonic melodies are nowadays accurately recognised by several (win2) programs out there. I've heard that band in a box does a surprisingly good job even with moderate polyphony (among posibly other programs, I don't mean to be exhaustive).

I'm afraid there is not a free/libre program for that (I'm not aware at least). But you can try some of the win2 programs under wine. Look for example [here]("http://www.audiorecording.me/convert-mp3-files-to-midi-files-using-amazingmidi-in-linux-ubuntu-wine.html").

Just a word of caution: don't expect marvels. Music recognition is a very hard problem. Nothing to do with midi to audio conversion, as mentioned in previous posts.
EDIT: also, don't expect to extract a clean score: small tempo innacuracies when playing, or on purpose rubatos, will be interpreted as semidemiquarvers (or so). Expect to do a fair amount of manual editing (with musescore or whatever) before getting a musician-readable score.

---

### Post by teledyn on 2011-10-23
There is, in fact, a very good program for extracting amazingly accurate midi or lilypond scores from any arbitrary mp3: *it is in your brain*, it is called your auditory sense.  Be prepared, however, because learning to use that program effectively can be a lifelong thing :)

That's the ticket: you have to listen to the file, over and over, and guess at its structure until your guess is pretty much spot on with the original, that is how musicians have learned their craft since like forever, so don't shy away from it, it is a good skill to have, I wish my skill at it was better, but then, every musician will say the same.

And if this is a program that *every* musician will say they cannot yet do perfectly, you can bet that no mere windows machine is going to get very far.  However ...

I have a recommendation for not-free but very cheap software that goes a long way towards helping you make better guesses as to what it is you are hearing on the recording, the Transcribe! program from SeventhString Software -- I won't bore you with details here because I've already bored everyone with [details over at my review on my blog]("http://blog.teledyn.com/transcribe-serious-affordable-software-for-tr").

---

### Post by dionysuschild on 2013-04-03
[TABLE]
[TR]
[TD="class: votecell"]     0     down vote         
              [/TD]
                [TD="class: answercell"]     I BELIEVE THIS POST WILL BE HELPFUL   I  wanted to be able to hum, whistle, play ,......etc with whatever form  create a wav file, and convert it to midi in order to use the notation  and intensity for an sound sample...in my instance for use in lmms....so  after 4 hours of searching and tinkering i have found a way to do so..
  *Find a program called TS audio to midi, (for windows) the program isnt free so i found it at my favorite t.....o.rrent site.
  *Install Ts audio to midi with wine (add your serial that you purchased like a good consumer) *Install autotalent [http://tombaran.info/autotalent.html](http://tombaran.info/autotalent.html)  or in fedora use  su -c 'yum install ladspa-autotalent-plugins'. (auto talent is a feree  autotune plugin that can be used wherever, im using it in audacity)the  auto tune is by no means nec. but could help
  *record your track, i use mono in this instance to reduce confusion,  like i stated, im using audacity. at this point you can use autotalent  under effects to smooth it out if you would like.
  *export as wav
  *Import wav into ts audio to midi, convert to midi and save, (this  process will take you looking at the gui to understand but its easy to  comprehend,
  *open any software that imports midi.and import your new midi file. 
  i am using lmms so i imported the midi into the song editor. (make  sure you have a soundfont) found the instrument i wanted in soundfont  player inside lmms and there you go.. the sequence isnt quite perfect of course. but this process can be used  to get a fairly close midi track....then you can just open a piano roll  and edit a little bit....hell yeah.
 
[/TD]
[/TR]
[/TABLE]

---

### Post by mörgæs on 2013-04-03
Hi, thanks for the contribution but please don't copy text from other pages. A link is a better way.

But... the thread is old, and the contents is likely to be obsolete. 1,5 years is a lot in the software world, so closing.

---

