---
title: "newbie Q: install"
date: 2010-02-05
forum: General Help
---

### Post by mordret on 2010-02-05
Hi there,
I am new to ubuntu/linux, here my question:
I was looking for a program that would convert sid files to wav files. On the internet I found it:
[http://manpages.ubuntu.com/manpages/karmic/man1/sid2wav.1.html](http://manpages.ubuntu.com/manpages/karmic/man1/sid2wav.1.html)
Now, when I download the sid2wav.1.gz file it only contains a text file sid2wav.1
I have no idea what to do with that or if I did sg completely wrong. Normally I install via apt-get install which is not possible for the apps at hand.
Any hint for a newbie?
thx a lot

---

### Post by Bachstelze on 2010-02-05
What you downloaded there is just a manual page (think of it as the equivalent for Windows's help files). The actual [font=monospace]sid2wav[/font] program lies in the [font=monospace]sidplay-base[/font] package.

---

### Post by mordret on 2010-02-05
Thanks Bachstelze,
super fast reply.. and how embarrassing :) well thanks to your hint I found the package and it works!

---

### Post by fluffman86 on 2010-02-05
In other words, go to Applications > Accessories > Terminal and type:

sudo apt-get install sidplay-base

to install.  You can then type:

man sid2wav

to read about how to use sid2wav.  There's lots of option to enable stereo, etc., but at its most basic level you just type:

sid2wav /path/to/original-sidfile.sid /path/to/converted-output-wavfile.wav

to convert.

edit: glad you got it working. the title said "newbie Q" so I didn't know *how* newbie.  Sorry if I seemed patronizing.

---

### Post by mordret on 2010-02-05
thanks for all your help... I have to admit I fell in love with ubuntu.. so straightforward and well where it is not there you get instant help! great! :)

---

