---
title: "stream with mplayer or vlc."
date: 2010-10-25
forum: General Help
---

### Post by Drenriza on 2010-10-25
I have an old set-top-unit, that i would like to stream a intro-trailer.

The unit has a single VGA interface, that i would like to stream the intro-trailer out of, connected to a VGA screen.

How is this possible to do from a command line, with no GUI. The unit has VERY limited resources, for this job. So less demanding = better.

Kind Regards

---

### Post by Drenriza on 2010-10-27
No one?

---

### Post by SeijiSensei on 2010-10-27
I can't really tell what you're trying to accomplish from your description, but you can play a video from the command line with mplayer just by using "mplayer /path/to/video.file".  Where the video will appear without X running, I don't know.  Try "man mplayer" and look at the various -vo alternatives.  "mplayer -vo help" will provide a list of supported outputs.  It's pretty extensive!  The "vesa" driver might be a possibility.

---

### Post by Drenriza on 2010-10-28
So what your saying is that with

mplayer /path/to/file
I start the movie and then i need to do an -vo to direct the stream out the interface i want to use?

---

### Post by Drenriza on 2010-11-01
No one? :(

---

### Post by SeijiSensei on 2010-11-01
You're going to have to commit to reading some documentation and experimenting.

Try "mplayer -vo vesa /path/to/mediafile" and see if it appears on the device attached to the VGA port. I've never used mplayer without X-Windows, and I doubt many other people here have either.

I don't know if vesa is the right choice in this situation.  As I say, read some documentation; [http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#video](http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#video) is a good place to start.

---

