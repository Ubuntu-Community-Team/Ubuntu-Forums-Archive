---
title: "No idea how to even start up espeak? Where is it?"
date: 2011-10-21
forum: General Help
---

### Post by carrie.kandira on 2011-10-21
That's pretty much it. I have no idea how to get it running. Where exactly is it? I've read somethings that say...
1-choose your  voice Language
 **# espeak --voice**
2- Speak the words specified in command line
 This is the default usage
 
**# espeak --stdout 'words to speak' | aplay** 3-Speak your document
 **# espeak --stdout -t mydocument.txt | aplay** 4-Generate voice file from text document
 **# espeak -t mydocument.txt -w myaudio.wav**

But what in the world does that mean? Do I put that somewhere? Will it open something? Like the espeaker....?
I don't know where to start.
If there is a better program for text to speech I'm open to that as well.

Thank you.

---

### Post by Rodney9 on 2011-10-21
This might help - Gespeaker is a GTK+ frontend for espeak. It allows to play a text in many languages with settings for voice, pitch, volume, speed and word gap. The text played can also be recorded to WAV file. 

Gespeaker is in the Software Centre

A Tutorial thanks to Woli - [http://ubuntuforums.org/showthread.php?t=1813001&highlight=espeak](http://ubuntuforums.org/showthread.php?t=1813001&highlight=espeak)

More information - [http://espeak.sourceforge.net/](http://espeak.sourceforge.net/)

---

### Post by carrie.kandira on 2011-10-21
Thank you so much. Sorry, only had ubuntu for like a month.

---

### Post by papibe on 2011-10-22
espeak is command line application. Open a terminal a write:
```
espeak "I am reading this for you"
```
[Here]("http://www.youtube.com/watch?v=urZzy-zXyfw")'s a very simple video tutorial.

Hope it helps,
Regards.

---

### Post by carrie.kandira on 2011-10-22
Well thank ya kindly.

---

