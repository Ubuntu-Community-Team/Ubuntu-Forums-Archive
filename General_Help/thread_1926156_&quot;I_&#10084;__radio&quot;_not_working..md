---
title: "&quot;I &#10084;  radio&quot; not working."
date: 2012-02-15
forum: General Help
---

### Post by SoFl W on 2012-02-15
I am having problems "I &#10084; radio" audio stream.  I have tried it with both Firefox and Chromium (not Chrome)  Clicking the "Listen Live" button does nothing, clicking the play button on top just has the "loading?" icon spinning.

If I knew how to get a stream with VLC I would try that.  I try different radio stations and none seem to work.

Any suggestions?

---

### Post by 23dornot23d on 2012-02-15
Its only available in the USA ... when I try it ...... 

only help I can really give .... also have you tried streamtuner ... old but quick and simple

sudo apt-get install streamtuner

is this the right link to it .... just checking ...

[http://www.iheart.com/](http://www.iheart.com/)

---

### Post by SoFl W on 2012-02-15
I am in the USA, and the stations I want to listen to are also in the USA,  I am sure it is a flash issue but I can't figure out what it isn't running.

---

### Post by 23dornot23d on 2012-02-15
Might be some useful info here

[http://forum.videohelp.com/threads/339818-Can-t-Figure-Source-URL-Stream](http://forum.videohelp.com/threads/339818-Can-t-Figure-Source-URL-Stream)

but  I cannot test it here

another link that is mentioned in the one above ..... seems it constantly changes streams ... no idea why

[http://stream-recorder.com/forum/record-clear-channel-radio-stations-iheartradio-com-t6306.html?](http://stream-recorder.com/forum/record-clear-channel-radio-stations-iheartradio-com-t6306.html?)

---

### Post by SoFl W on 2012-02-16
Thank you, I thought it was something I was doing wrong on my machine it never occurred to me that it might be a system wide problem.  Looks as though it has been happening for a while.


EDIT:
Seems if you use
[http://www.surfmusic.de/media/CALL_LETTERS-fm.m3u](http://www.surfmusic.de/media/CALL_LETTERS-fm.m3u)   -or-
[http://www.surfmusic.de/media/CALL_LETTERS-am.m3u](http://www.surfmusic.de/media/CALL_LETTERS-am.m3u)
with VLC's "Open Network stream" it will work.

example:
[http://www.surfmusic.de/media/kysr-fm.m3u](http://www.surfmusic.de/media/kysr-fm.m3u)


Although it is not solved it is not a Ubuntu problem and I found a work-around so I am going to mark this as solved.

---

