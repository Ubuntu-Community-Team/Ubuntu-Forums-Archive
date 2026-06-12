---
title: "White noise or pink noise?"
date: 2006-02-25
forum: General Help
---

### Post by nwillis on 2006-02-25
No, not [the lame movie]("http://www.imdb.com/title/tt0375210/"), the actual sound.

I've recently gotten very attached to the convenience of the OS X app [Noise]("http://blackholemedia.com/noise/"), a small, unobtrusive white noise/pink noise generator.  Fire it up and it helps keep out distractions.

Is there anything like this for Linux?  I've found some abandoned projects on freshmeat, signal generators and so on, but I don't personally know enough about waveform generation that I can tell (a) if they do what I want and (b) how to do it.

So what about it?  Anybody have any experience with noise generation -- standalone app, looping an audiofile, or otherwise?

N

---

### Post by michaelb on 2006-02-25
Audacity should be able to generate white noise -- I've used it to generate white noise in the past. Save it as an ogg and loop it in XMMS or whatever audio player you prefer.

Here's a wikipedia article on the colors of noise:
[http://en.wikipedia.org/wiki/Colors_of_noise](http://en.wikipedia.org/wiki/Colors_of_noise)

---

### Post by dcstar on 2006-02-25
[QUOTE=nwillis]No, not [the lame movie]("http://www.imdb.com/title/tt0375210/"), the actual sound.

I've recently gotten very attached to the convenience of the OS X app [Noise]("http://blackholemedia.com/noise/"), a small, unobtrusive white noise/pink noise generator.  Fire it up and it helps keep out distractions.

Is there anything like this for Linux?  I've found some abandoned projects on freshmeat, signal generators and so on, but I don't personally know enough about waveform generation that I can tell (a) if they do what I want and (b) how to do it.

So what about it?  Anybody have any experience with noise generation -- standalone app, looping an audiofile, or otherwise?

N[/QUOTE]
What about this:

[http://www.eblong.com/zarf/boodler/](http://www.eblong.com/zarf/boodler/)

---

### Post by nwillis on 2006-02-27
> Audacity should be able to generate white noise -- I've used it to generate white noise in the past. Save it as an ogg and loop it in XMMS or whatever audio player you prefer.

I appreciate your replying, but this is exactly what I want to *avoid* doing.  The beauty of the Noise.app for OSX is that you don't have to do any of this; it's click and go.  You don't have to do it by hand, you don't have to launch a music player app -- and you don't have to tie up your music player app by keeping one file on the playlist -- not to mention setting crossfading to prevent pops.

I should mention for the record that I have done this; prior to posting this question I got the pink noise ogg from Wikipedia's Pink Noise entry and tried looping it.  Real annoying, a lot more work, consumes resources, and xmms starting leaking memory with crossfade on when playing the same song over and over and over again.  But if you're willing to dedicate one music player app to this task, there is no reason to try and make pink noise in Audacity, since the Wikipedia article has a pre-made sample.

But it's still a kludgy solution.
N

---

### Post by nwillis on 2006-02-27
> What about this:

[http://www.eblong.com/zarf/boodler/](http://www.eblong.com/zarf/boodler/)

This is interesting.  It looks like it may take some work to get running, though, there appears to be no real installation procedure.

---

### Post by engla on 2006-02-27
As for nice trivia, I found a funny white noise generator.

Run in term: 
cat /dev/urandom > /dev/dsp

puts a lot of white noise in my speakers at least. Perhaps with some clever perlscripting it would be possible to make pink noise from that.

---

### Post by engla on 2006-02-27
edited: This is a double post. :mrgreen:

---

### Post by sbennettgso on 2006-12-13
Anyone ever gotten Boodler to work?  It seems fascinating to me, but I can't get it working.  Here's the output I get when I follow the installation instructions:

```
scott@scott-laptop:~/boodler$ python configure.py
Configuring Boodler for oss: Open Sound System sound driver
scott@scott-laptop:~/boodler$ make
(cd cboodle; make cboodle.so)
make[1]: Entering directory `/home/scott/boodler/cboodle'
cc -O2  -I/usr/include/python2.4  -Wall -Wmissing-prototypes -Wstrict-prototypes -Wno-unused    -c -o cboodle.o cboodle.c
cboodle.c:8:20: error: Python.h: No such file or directory
In file included from cboodle.c:13:
noteq.h:16: error: expected specifier-qualifier-list before ‘PyObject’
noteq.h:29: error: expected ‘)’ before ‘*’ token
noteq.h:34: error: expected declaration specifiers or ‘...’ before ‘PyObject’
noteq.h:34: error: expected declaration specifiers or ‘...’ before ‘PyObject’
noteq.h:37: error: expected declaration specifiers or ‘...’ before ‘PyObject’
noteq.h:37: error: expected declaration specifiers or ‘...’ before ‘PyObject’
noteq.h:40: error: expected declaration specifiers or ‘...’ before ‘PyObject’
noteq.h:40: error: expected declaration specifiers or ‘...’ before ‘PyObject’
cboodle.c:16: error: expected specifier-qualifier-list before ‘PyObject’
cboodle.c:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
cboodle.c:102: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
cboodle.c:113: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
cboodle.c: In function ‘run_python_agents’:
cboodle.c:141: error: ‘PyObject’ undeclared (first use in this function)
cboodle.c:141: error: (Each undeclared identifier is reported only once
cboodle.c:141: error: for each function it appears in.)
cboodle.c:141: error: ‘arglist’ undeclared (first use in this function)
cboodle.c:142: error: ‘result’ undeclared (first use in this function)
cboodle.c:144: warning: implicit declaration of function ‘Py_BuildValue’
cboodle.c:144: error: ‘run_agents_rock_t’ has no member named ‘generator’
cboodle.c:149: warning: implicit declaration of function ‘PyEval_CallObject’
cboodle.c:149: error: ‘run_agents_rock_t’ has no member named ‘runagents’
cboodle.c:150: warning: implicit declaration of function ‘Py_DECREF’
cboodle.c: At top level:
cboodle.c:161: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
cboodle.c:172: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
cboodle.c:183: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
cboodle.c:195: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
cboodle.c:219: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
cboodle.c:241: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
cboodle.c:263: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
cboodle.c:285: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
cboodle.c:312: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
cboodle.c:364: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
cboodle.c:393: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
cboodle.c:423: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
cboodle.c:453: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
cboodle.c:466: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
cboodle.c:479: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘methods’
cboodle.c: In function ‘initcboodle’:
cboodle.c:502: warning: implicit declaration of function ‘Py_InitModule’
cboodle.c:502: error: ‘methods’ undeclared (first use in this function)
make[1]: *** [cboodle.o] Error 1
make[1]: Leaving directory `/home/scott/boodler/cboodle'
make: *** [makecboodle] Error 2
scott@scott-laptop:~/boodler$
```

Any help would be appreciated.  I'm not much of a programmer, and I'm relatively new to Linux.  I'm willing to try and learn, though.  BTW, I'm running Edgy on an old ThinkPad A22p.

Thanks,
Scott

---

### Post by bodhi.zazen on 2006-12-13
If noise is making color please share what you're smoking ....

[indent]I'll take some of the pink, floyd that is[/indent]

---

### Post by sbennettgso on 2006-12-15
OK, I figured it out.  I needed to install the Python development libraries.

Thanks,
Scott

---

### Post by dcstar on 2006-12-15
> **bodhi.zazen said:**
> If noise is making color please share what you're smoking ....

[indent]I'll take some of the pink, floyd that is[/indent]

In the interests of completeness, the terms "White noise" and "Pink noise" refer to the energy vs frequency characteristics of randomly generated "noise".

When it is "White", the energy increases with frequency (if you see it in a spectrum analyser the energy output rises with frequency) and it sounds very "hissy".

When it is "Pink", the energy vs frequency graph is flat and it sounds a lot more "bassy" to the human ear.

---

### Post by ciscosurfer on 2006-12-15
I'm definitely a fan of "[Brown]("http://upload.wikimedia.org/wikipedia/commons/4/48/Brown_noise.ogg")" noise -- sounds sort of like the ocean.

Big fan of the [50 Hz hum]("http://upload.wikimedia.org/wikipedia/en/3/3f/50Hz.ogg"), btw.  It's much less annoying/distracting than the [60 Hz hum]("http://upload.wikimedia.org/wikipedia/commons/a/ab/Mains_hum_60_Hz.ogg") that those in the Americas are used to.

---

### Post by bodhi.zazen on 2006-12-15
> **dcstar said:**
> In the interests of completeness, the terms "White noise" and "Pink noise" refer to the energy vs frequency characteristics of randomly generated "noise".

When it is "White", the energy increases with frequency (if you see it in a spectrum analyser the energy output rises with frequency) and it sounds very "hissy".

When it is "Pink", the energy vs frequency graph is flat and it sounds a lot more "bassy" to the human ear.

Hey thanks for the information. I am familiar with white noise but other then Pink Floyd never heard of Pink noise.

I must admit I found the title amusing and was not trying to be offensive.

Thank you for the education.

ciscosurfer: Now brown noise too :shock:

Arrrgh enough =;

I'll stay with Floyd \\:D/  Let's just say Ive given myself over to the Dark side 8-[

I understand tinnitus, it happens when I turn the music down :twisted:

---

### Post by sbennettgso on 2006-12-18
> **dcstar said:**
> In the interests of completeness, the terms "White noise" and "Pink noise" refer to the energy vs frequency characteristics of randomly generated "noise".

When it is "White", the energy increases with frequency (if you see it in a spectrum analyser the energy output rises with frequency) and it sounds very "hissy".

When it is "Pink", the energy vs frequency graph is flat and it sounds a lot more "bassy" to the human ear.

I have rarely seen a reference in practice to the energy spectral density, but it's been a long time since I studied this in any real detail.  What I do know is that if you look at white noise on a spectrum analyzer (which generally measures power spectral density, not energy spectral density), it's flat.  For pink noise, the characteristic is 1/f.  These are both under the assumption that the resolution bandwidth is constant vs. frequency.

From what I do remember, if you take a time-limited section of an aperiodic signal (such as white noise) and perform a Fourier transform on it, then the squared magnitude of the Fourier transform is the energy spectral density.  I do know that power is the time derivative of energy, so perhaps that's what leads to the relations dcstar makes above (derivation in the time domain is division by frequency in the frequency domain).  Or are there measurement standards that use increasing resolution bandwidth vs. frequency in audio electronics to account for the response of the human ear (my background is in wireless communications)?

---

### Post by Aliby on 2007-11-01
Look at Baudline
[http://www.baudline.com/](http://www.baudline.com/)

It has a fully integrated signal generator

---

### Post by coldsalmon on 2008-01-07
The program 'speaker-test' generates pink noise.

---

### Post by nwillis on 2008-01-15
> **coldsalmon said:**
> The program 'speaker-test' generates pink noise.

Well that would have been nice to know two years ago when I asked the question.

On the other hand, it is nice to see how many options there are these days....

N

---

### Post by Tasu on 2008-04-07
> **engla said:**
> As for nice trivia, I found a funny white noise generator.

Run in term: 
cat /dev/urandom > /dev/dsp


Hmmm! This indeed generates noise.. but, how could I save for later use? O_O hmmm! say, save it as a wav file... I tried sox and ffmpeg.. but both record nothing.. 
Hmmmm! Yeah! I know.. a bit weird trying to record the noise.. but.. well.. I'm just a lot curious!

---

