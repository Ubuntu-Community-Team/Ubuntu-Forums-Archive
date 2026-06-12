---
title: "Joining XviD Movie Files"
date: 2006-05-13
forum: General Help
---

### Post by unnes on 2006-05-13
I would like to burn an XviD movie to DVD, but my source video is currently in two separate 700MB files. I realize it would be fairly easy to put both videos in as separate videos and have them selectable from the menu, but I would prefer a seamless viewing experience.

Can someone recommend a good tool for joining the two files into one continuous movie, or show me a command line option that will allow this?

The audio is VBR MP3, so I'm not even sure whether such joining is possible without full re-encoding.

---

### Post by Herman on 2006-05-13
CinePaint (movie GIMP) might be a program worth further investigation as to its capabilities or not, to do what you want.
[CinePaint]("http://www.cinepaint.org/") can be found in Synaptic Package Manager under 'graphics', from the universe repository I think.

I have not tried CinePaint myself, but I was researching Ubuntu movie software for my sister-in law to find out which programs she might be able to use for a university project involving restoring old movies if she switches to Ubuntu. She wants to buy a new computer for this, which she has not done yet, so she has yet to try the software out. Probably she'll wait for 'Dapper' to be released.
I know next to nothing about the subject of films and movies myself. I'm sure CinePaint will do quite a lot, hopefully it will do the job you specified.  I hope that link and info will be of some help to you. I would be interested to hear how you get along.  Regards, Herman. :-D

---

### Post by unnes on 2006-05-13
Thanks for your reply Herman, I'll check out CinePaint.

I was actually messing around with AVIDemux, and it seems like it can accomplish what I want. I apparently have to sacrifice the packed bitstream of the original encode, but I can deal with that.

---

### Post by Herman on 2006-05-14
Thanks for your reply too, unnes, I'll pass that information on! (The best I can do is act as a hub here).

---

### Post by MikeNick42 on 2006-05-14
You guys may also want to check out cinelerra.  I don't have much experience with it because it's usually overkill for what I'm doing but it seems fairly capable.  I don't think it's in the breezy repositories, but getting the rpm and using alien to install it isn't too hard.

---

### Post by JoeMetal on 2006-05-14
Under the avifile-utils package, there is a command called avicat.  It litterally adds two avi files together.  I haven't used it, but it might be of some help.

---

### Post by unnes on 2006-05-14
> You guys may also want to check out cinelerra. I don't have much experience with it because it's usually overkill for what I'm doing but it seems fairly capable.

Wow! Cinelerra does seem like overkill, but it supports encoding and decoding of H.264, which is something I've been looking for since I installed Ubuntu onto my desktop. Thanks for the heads up!

---

