---
title: "problem running scripts"
date: 2012-02-27
forum: General Help
---

### Post by DutchShrek on 2012-02-27
Hi all
I am trying to stream a webcam to justin.tv and found 2 links that both describe a similar method:
[http://www.ws4gl.org/broadcasts/fme-broadcasts](http://www.ws4gl.org/broadcasts/fme-broadcasts)
[http://forums.heroesofnewerth.com/showthread.php?t=229469](http://forums.heroesofnewerth.com/showthread.php?t=229469)

Basically, using ffmpeg.
I have it all installed and to be sure I tested out with skype and through the browser on justin.tv.

When I open justin.tv in the browser it loads up fine and I can start my broadcast with both sound and video. So that's great, it works.
However,
I come from windows and use Flash Media Encoder. The main reason for this is widescreen support and higher quality.

Since FME is windows only I came across the above links.

But here's my problem...
The first link talks about creating a file such as ffjusting.tv.sh with the contents edited to match my info.
I made the file, with my relevant info and then saved as an sh file.
But the file won't run. In properties I changed it to be handled as an executable and the terminal pops up for a blink of an eye and it's gone.

The second link is talking about a bashrc file. I don't even know what that is.

Is there anyone who can point me to a total noob tutorial to accomplish my streaming?

Ps: I'm running Ubuntu 11.10 32 bit

---

### Post by DutchShrek on 2012-02-27
Ok so I found out the bashrc thing.
(Didn't know it was only accessible through terminal)
But the script described in that second link is for desktop streaming and that is not what I want.

So I have to try to fall back to the first link.
But I still can't find out why I can not run that sh file.
Any ideas?

---

### Post by Azdour on 2012-02-28
Hi,

I would open a terminal (ctrl+alt t), go to where the sh file is and try to run it from there. That way you should be able to see if the script reports any errors or just exits without doing anything.

---

