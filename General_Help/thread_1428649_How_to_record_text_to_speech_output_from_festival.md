---
title: "How to record text to speech output from festival"
date: 2010-03-13
forum: General Help
---

### Post by flesher on 2010-03-13
How can I record text to speech output from festival to an audio file like mp3 or ogg?

My guess would be to pipe it to a command line recorder; anyone have any ideas how to do this?

Thanks

---

### Post by Fitch on 2010-03-17
I too wanted to do the same thing with Festival.  (i'm ex Edinburgh Uni staff, so really wanted this to work!)

Thing is, Intrepid upwards comes with espeak pre-bundled - quite impressive.

Anyway, on a command line, type :

sudo espeak -f fred.txt -w fred.wav

assuming you've called the text file Fred that is...

Then you can use a wav to mp3 converter as per normal e.g Autolame
available at: 
[http://www.cgarbs.de/stuff.en.html](http://www.cgarbs.de/stuff.en.html)

---

