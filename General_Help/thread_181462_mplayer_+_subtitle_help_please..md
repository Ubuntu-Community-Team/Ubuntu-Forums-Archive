---
title: "mplayer + subtitle help please."
date: 2006-05-24
forum: General Help
---

### Post by chiefy on 2006-05-24
First off: I have searched this forum, and I have tried pretty much everything I've seen (the ln'ing of the sunfont.ttf etc.) I can't seem to get .srt subtitles working with mplayer. The only error it gives is "Cannot load subtitle file xxxx.srt" I am at work, so I am not sure what version of mplayer I am running(i am pretty sure it's the standard repository version). I also tried "apt-get install mplayer-fonts" to no avail.

My next step was just compiling mplayer from source. 

Any ideas?

Thanks!

---

### Post by revoltism on 2007-03-04
same deal for me... has do be some bug in mplayer and that it can't do other than western languages as subtitle even if it says it can.

---

### Post by kodoku on 2007-03-04
Heh, a been there, done that for me..

First, you have to check the encoding of the subtitle file.  Just open it up in Gedit and see what the font box says.  If you have asian subtitles, chances are you have a UTF-16 encoded file.  MPlayer only handles up to UTF-8.  The player seems to lack a autoselect font feature, and even then, if the font doesn't exist in its list, then it will display that error message.  If you convert your srt file into UTF-8, I bet you'll be able to play it.  

sudo apt-get libtext-iconv-perl

Then in a terminal, type:
iconv -f "encoding of original text" -t "encoding of output" "original file" -o "output file", all without quotes

Mplayer should be able to handle your converted srt.

The issue, I think, is in the xine engine that Mplayer uses.  I read Xine's website, and adding subtitle support to the engine appears to be a very cumbersome process, as it does not use the system fonts directly.  Instead, every font that xine uses has to be individually compiled into a xine-type format (by default, mplayer only comes with Sans).  You could also enable ttf font support when you compile xine yourself, which should allow you to use ttf fonts (but I have no idea how to compile it to be usuable for mplayer).  I have had absolutely no luck with this.

[http://xinehq.de/index.php/faq#SUPPORTEDFONTS](http://xinehq.de/index.php/faq#SUPPORTEDFONTS)

My solution was to use VLC, despite its crappy support for subtitle formatting.  It allowed me to select UTF-16 as my subtitle font, which works.

---

