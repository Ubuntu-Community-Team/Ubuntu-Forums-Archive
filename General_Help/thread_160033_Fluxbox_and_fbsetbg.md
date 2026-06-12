---
title: "Fluxbox and fbsetbg"
date: 2006-04-14
forum: General Help
---

### Post by Cornmuffin on 2006-04-14
I just recently installed the dev version of fluxbox for the first time and I have to say that I am incredibly impressed.  I haven't encountered any real problems thus far except for the 'simple' task of having a desktop background.  I installed fbsetbg and used it to set a wallpaper, which does work.  I also have my /.fluxbox/startup file saying fbsetbg -l.  The problem is, once i restart, the wallpaper does not automatically load as it should.  There is a "lastwallpaper" file which seems to be storing the image, but it just doesn't want to work.  Any suggestions?

---

### Post by DJ Scribblinni on 2006-04-14
Cornmuffin...nice screenname... I had the same problem, but I solved it this way.  There should be a file called "init", it should be located in the same spot your startup file is.  At the end of the file I simply added: ```
session.rootCommand:	fbsetbg -l
```  It solved all problems for me.  Good Luck muffin man.

---

### Post by Cornmuffin on 2006-04-14
ah thanks for the compliment and help, but it still doesn't work.  Heres the code in my /.fluxbox/startup file...maybe i did something wrong but i don't see what i could have screwed up

```
exec /usr/local/bin/fluxbox -log ~/.fluxbox/log
fbsetbg -l 
```

I know the fbsetbg command to set the wallpaper works...because it does display once i use it in the terminal.  I also set your code into the init file as well.

---

### Post by greenpenguin on 2006-04-14
I had a similar problem with blackbox. My solution - if this works with fluxbox - is to make a similar change to the style/theme file.  Copy your theme from wherever (/usr/share/fluxbox/styles on my box) to .fluxbox/styles and then add/change the rootCommand: etc line to suit

Hope that works :)

---

### Post by taurus on 2006-04-14
[QUOTE=Cornmuffin]ah thanks for the compliment and help, but it still doesn't work.  Heres the code in my /.fluxbox/startup file...maybe i did something wrong but i don't see what i could have screwed up

```
exec /usr/local/bin/fluxbox -log ~/.fluxbox/log
fbsetbg -l 
```

I know the fbsetbg command to set the wallpaper works...because it does display once i use it in the terminal.  I also set your code into the init file as well.[/QUOTE]
"exec /usr/local/bin/fluxbox -log ~/.fluxbox/log" should be the last command to run in ~/.fluxbox/startup!!!  In addition, I have
```

fbsetbg -f /home/taurus/pictures/Lunar.jpg &

```

---

### Post by Cornmuffin on 2006-04-14
thanks everyone for your replies, especially taurus.  I had no idea that was supposed to be last!  What i ended up doing which seemed to fix it was add this to my "init" file.  It's slightly different from what scribblinni mentioned.

```
session.screen0.rootCommand:	fbsetbg -l
```

Now it works!

---

