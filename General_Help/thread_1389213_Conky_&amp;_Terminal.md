---
title: "Conky &amp; Terminal"
date: 2010-01-24
forum: General Help
---

### Post by Kruptein on 2010-01-24
if you do the command conky in terminal,
it starts conky ofcourse, but it also shows output to that terminal so you can't do any other commands to that terminal,

Is their an option like you can do with the '&' sign in other cases?

If you do the '&' sign with conky it still gives output,  
also the conky -d  command gives output...

---

### Post by londonali1010 on 2010-01-24
> **Kruptein said:**
> if you do the command conky in terminal,
it starts conky ofcourse, but it also shows output to that terminal so you can't do any other commands to that terminal,

Is their an option like you can do with the '&' sign in other cases?

If you do the '&' sign with conky it still gives output,  
also the conky -d  command gives output...

Yeah, sometimes it does that...I don't know why!  If you use "conky &", after the output, just press return and it should bring your command prompt back up.

Hope this helps!

---

### Post by Kruptein on 2010-01-24
Yeah, I already figured out that I could use the terminal again after a hit on the return, but how should I translate that hit into bash script,
caus I want to echo something , then start conky, and then echo something again, (second echo does not show with conky & until conky is closed)

---

### Post by londonali1010 on 2010-01-24
> **Kruptein said:**
> Yeah, I already figured out that I could use the terminal again after a hit on the return, but how should I translate that hit into bash script,
caus I want to echo something , then start conky, and then echo something again, (second echo does not show with conky & until conky is closed)

I believe there's something like a -q flag that won't output to terminal...Don't know if that will do it for you!

---

### Post by mcduck on 2010-01-24
There are couple of ways to do this kind of stuff.

First, you can simply redirect standard error to a text file (or /dev/null):

```
conky 2> /path/to/some/file &
conky 2> /dev/null &
```

(if that's not enough, "conky &> /dev/null" will redirect both stabndard output and error to /dev/null..)

...or you can use Nohup, which redirects output to a text file in your home directory and also separates the program you run from the terminal process, so that the program stays running even if you close the terminal:

```
nohup conky &
```

(Myself, I just use the Alt-F2 Run dialog to run this kinds of commands.. :))

---

### Post by Kruptein on 2010-01-24
Thanks mcduck, the /dev/null is a good idea,
the -q flag might also be good, but I'm going to stick with the dev/null sorry londonali ;)

---

### Post by VCoolio on 2010-01-24
Programs running in the background will still print their stdout and stderr messages, but you can just continue using the terminal (even if your prompt isn't there sometimes beneath output). You can get conky to keep its output to itself with

out_to_console no
out_to_stderr no

or run the command like explained earlier with >/dev/null 2>&1

---

### Post by Saiko Berry on 2010-01-24
why are you running conky with terminal anyway

---

### Post by Kruptein on 2010-01-24
I have a script that runs conky on every startup,
but If I want to change something to conky after the startup, I have to kill the process, and then restart it, so I wrote a simple (re)start script for conky ...

can you follow?

Now I only have to double-click the script and conky (re)starts.

---

### Post by Saiko Berry on 2010-01-24
Yes thats what I did. lol. I think thats what everyone does, writes a small bash script to start their many parts of conky, since most people have more than 1 if they have 1 at all.

#!/bin/bash
sleep 1 &&
conky -c ~/Conky/conky1 &

---

### Post by Kruptein on 2010-01-24
I only have one, but I'm going to expand it ;)
I still need:
-weather
-music
-own scripts
-...

=D

---

### Post by Saiko Berry on 2010-01-24
Cool =) Put it in Post your Conky RC when youre done, I'm sure people would be happy to see it. =0 Mine is pretty simply for now:

[http://i50.tinypic.com/fuauww.jpg](http://i50.tinypic.com/fuauww.jpg)

---

### Post by Kruptein on 2010-01-24
Mine is also very basic, right now, (I don't know if you can read it very well, caus my wallpaper changes every minute =D)

---

