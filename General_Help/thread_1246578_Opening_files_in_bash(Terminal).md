---
title: "Opening files in bash(Terminal)"
date: 2009-08-21
forum: General Help
---

### Post by JacKeown on 2009-08-21
ok so I tried to open a song using a script in bash.  First I used 

[COLOR="Blue"]cd /home/username/Music
[/COLOR]
.....and then I used.....

[COLOR="Blue"]open song.mp3[/COLOR]

and it says
[COLOR="Blue"]
couldn't get a file descriptor refering to the console[/COLOR]

thanks in advance

---

### Post by Johnny B on 2009-08-21
"open" is not the command you want, you have to tell the shell what program to use: 
totem song.mp3
or 
rhythmbox song.mp3
for a script and without a GUI i would use: 
aplay song.mp3

---

### Post by dcstar on 2009-08-21
> **JacKeown said:**
> ok so I tried to open a song using a script in bash.  First I used 

[COLOR="Blue"]cd /home/username/Music
[/COLOR]
.....and then I used.....

[COLOR="Blue"]open song.mp3[/COLOR]

and it says
[COLOR="Blue"]
couldn't get a file descriptor refering to the console[/COLOR]

thanks in advance

Applications "open" files, not terminal sessions.

If **you** want to use a file then **you** have to specify what application to use.

---

### Post by JacKeown on 2009-08-22
sorry i'm quite new thanks for the clarification

---

### Post by PGScooter on 2009-08-22
> **JacKeown said:**
> sorry i'm quite new thanks for the clarification

no worries JacKeown, you'll get the hang of it in no time! You could also use vlc, if you have it installed: ```
vlc filename.mp3
```. And check this out, if you want to open all of the mp3 files in a directory, you can do this (will probably work with rhythmbox as well): ```
vlc directoryname/*.mp3
```. Thus, to open all in the current directory, type ```
vlc *.mp3
```

---

