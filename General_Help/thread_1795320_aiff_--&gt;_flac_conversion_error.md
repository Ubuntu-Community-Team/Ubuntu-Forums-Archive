---
title: "aiff --&gt; flac conversion error"
date: 2011-07-02
forum: General Help
---

### Post by jamesisin on 2011-07-02
I received some music from a guy wanting me to write a review of his album.  He sent aiff files.  I want to convert them into flac for consistency.  Normally I would just run this:

```
flac *aiff
```

One of the files give me an error:

```
02 Good Times.AIF: ERROR: block size is 128; must be 0
```

I have tried changing the file extension and also running flac using the other extension, but either way I get the same error.

What's up with this file?  It plays fine (Totem).  How can I convert it?

---

### Post by jamesisin on 2011-07-02
Any ideas?

---

### Post by jamesisin on 2011-07-05
Hello?

---

### Post by jamesisin on 2011-07-07
Anybody?

---

### Post by mc4man on 2011-07-07
Maybe try running it through ffmpeg, could  either try an acodec copy or expand to wav

ffmpeg -i '/path/to/02 Good Times.AIF' -acodec copy  'whatever.aif'

---

### Post by andrew.46 on 2011-07-07
Looks like the error comes from this:

[http://flac.sourceforge.net/format.html#blocking](http://flac.sourceforge.net/format.html#blocking)

but I am a little at a loss as to how to get around this. I note several flac options to manipulate this though. Can you post the troublesome aiff file somewhere so I can play with it?

---

### Post by jamesisin on 2011-07-13
mc4man - After running the file through your command I now get this error instead:

```
02 – Good Times.aiff: ERROR: SSND chunk size inconsistent with sample frame count
```

andrew.46 - Maybe?  How would I know?  Doesn't seem likely because I'm pretty sure the block size should *not* be zero.

(I'll have to get permission from the artist to loan you the file, but at that point I'll probably just ask him for a different file.)

Thanks to both of you.

---

### Post by jamesisin on 2011-07-13
Well, SoundConverter managed to convert the original file into FLAC without any troubles (bragged even that it did it in 8 seconds).  Go figure.  Anyone know what command line utility SoundConverter runs?

---

### Post by jamesisin on 2011-07-25
Anyone know what command line utility SoundConverter runs?

---

### Post by westie457 on 2011-07-25
> **jamesisin said:**
> Anyone know what command line utility SoundConverter runs?

Not sure what you are looking for. Suggest you look at the ```
man soundconverter
```

---

### Post by jamesisin on 2011-07-25
I'll bet you say that to all the boys...

(There is no man entry for soundconverter.)

---

### Post by westie457 on 2011-07-25
> **jamesisin said:**
> I'll bet you say that to all the boys...

(There is no man entry for soundconverter.)

I beg to differ with you here. Look at the screenshot

---

### Post by jamesisin on 2011-07-25
No begging required.  I'm all for spirited debate between friends.

If you want to see a screen shot from my terminal, I could post that.  I'm hoping you'll just take my word that this is from my terminal:

```
$ man soundconverter
No manual entry for soundconverter
```

Crazy, wot?

Regardless, your screen shot shows clearly enough there is not much information about any commands which SC might be running to do its magic.

What I'm wondering is (if SC is a GUI which just runs command line applications or scripts) what is SC using to make its conversions?

(Although I would now also like to know why I don't have a man page for SC?!)

---

### Post by jamesisin on 2011-07-25
Ok, I figured out why I don't have a man page on this machine.  You'll love it.  I don't have SC on this box.  Hehe.

But seriously, anyone know if/what commands SC runs when it performs conversions?

---

### Post by westie457 on 2011-07-25
Do not have a clue what goes on in the background. Have no idea how to read a computer language script let alone write one. To me it looks like a lot of symbols letters and numbers thrown into a bucket, pulled out at random and then thrown onto a screen. A bit like my typing on a bad day.

About the man pages try reinstalling soundconverter ```
sudo apt-get install soundconverter
```

On a side-note, could you take a wander over to this [site]("http://www.theobn.co.uk/") and check out a band. Give an honest appraisal. It won't cost you anything and you won't get spammed.

---

### Post by westie457 on 2011-07-25
> **jamesisin said:**
> Ok, I figured out why I don't have a man page on this machine.  You'll love it.  I don't have SC on this box.  Hehe.

But seriously, anyone know if/what commands SC runs when it performs conversions?

Firstly have had mental dyslexia, only cure for that (which is temporary) bash head on desk.

Maybe this link will help you. [http://bazaar.launchpad.net/~vcs-imports/soundconverter/trunk/view/head:/soundconverter/gstreamer.py](http://bazaar.launchpad.net/~vcs-imports/soundconverter/trunk/view/head:/soundconverter/gstreamer.py)

You might have to sign into launchpad first.

---

### Post by jamesisin on 2011-07-25
Ah, Python.  A language I don't know.  There are many.

Looks like it's more complicated than I was hoping.  Maybe not so simple to extract the command line elements necessary to slap out a line of code and convert something.  Looks like I'll be sticking with SC itself.

Thanks.

---

