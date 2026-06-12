---
title: "cvlc to file"
date: 2011-05-25
forum: General Help
---

### Post by conradin on 2011-05-25
Greetings Knowlegable forums Users,
I really enjoy watching videos in the terminal using cvlc. I think I would like to convert some of the files to that style of output and be able to play them elsewhere, like on windows computers etc...
(someplace where the terminal isnt available...)

anyways, I tried using the code below to send the cvlc output to a file, but it didnt work as I was hoping it would. Only the audio part of the file seems to be present.

```
$ cvlc "mbs.flv" --sout /home/j/Videos/MyVid.flv

```

anyone have any ideas?

If its useful, cvlc, outputs VLC media player 1.0.6 Goldeneye
[0x8b25d20] dummy interface: using the dummy interface module...

---

### Post by conradin on 2011-05-26
Soo, -sout is evidently only for sound. there is a -vout option but That didn't work. 

I also found the help file at 
```
cvlc -H
```
But the stuff there is too complex for me to understand.

---

### Post by nothingspecial on 2011-05-26
The file type has nothing to do with weather or not it can be viewed on the console.

If vlc (or mplayer) can decode and play the file........... and your hardware will allow them to use the framebuffer, then the video/audio encoding does not matter.

Please try again to explain what you are trying to do.


ps. I haven't the faintest idea how the windows cli works.

---

### Post by conradin on 2011-05-26
Ok, Imagine youve downloaded a video and saved it on you hard drive. 
a video like:
[http://www.youtube.com/watch?v=PFSMAj86in4&feature=related](http://www.youtube.com/watch?v=PFSMAj86in4&feature=related)

and named it mbs.flv

Then imagine you're using Ubuntu server edition or you've logged into a non-graphical user session 

so then imagine, (or try it) running the file mbs.flv via cvlc
```
cvlc mbs.flv
```
what you get is very abstract colourful text output. That output is what I want, and, I want to save that output.

---

### Post by nothingspecial on 2011-05-26
I have to admit, I don't know what you are talking about...... sorry.

However, you may be interested to know that you can watch the videos properly in the console if you enable the framebuffer.

See here

[http://ubuntuforums.org/showpost.php?p=10792177&postcount=15](http://ubuntuforums.org/showpost.php?p=10792177&postcount=15)

Once you do that, cvlc <video.file> will output in the console :P

---

### Post by mc4man on 2011-05-26
cvlc is just an interface choice, in this case a dummy interface vs. the default interface, (qt) or a couple of other choices, typically used from the cli.
 It  has nothing much to do with the video being outputted. That, (vout), could be affected by what was chosen and or any video filters.

> what you get is very abstract colourful text output
That sounds like 'Color ASCII art' vout
--vout caca

---

### Post by conradin on 2011-05-27
lol. yeah caca is what I want!
I want to save the caca to a file so I can manipulate it.

---

