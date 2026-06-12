---
title: "Conky? How do I run it???"
date: 2011-02-28
forum: General Help
---

### Post by aussie_g on 2011-02-28
OK, I know this is probly a stupid question with an easy solution - but Im a newb so here goes...

I installed conky via the software manager in 10.10....

But I cannot find where it installed it so that I can run it.. It did not create a shortcut in the menu, and looking through the filesystem is making me dizzy....

I would search for it, but I dont know what the filename is, and I sure dont know what the extension is, what is the linux version of an .exe fle?

---

### Post by Frogs Hair on 2011-02-28
It starts in the terminal .
```
conky
```

---

### Post by aussie_g on 2011-02-28
come on dude - nothing is that easy...

OK, well it is that easy - thanks man - I feel even dumberer now

---

### Post by TeoBigusGeekus on 2011-02-28
In order to run conky, you have to create a file called .conkyrc in your home folder.
There's a [humongous thread]("http://ubuntuforums.org/showthread.php?t=281865") in the Community Cafe with a plethora of ideas. 
For detailed info about the commands of the .conkyrc file, see
[http://conky.sourceforge.net/documentation.html]("http://conky.sourceforge.net/documentation.html")
You can test your conky configuration by running
```
conky
``` 
from terminal.
Once you're satisfied, create a new file called conky_start and add these lines to it
```
#!/bin/bash
sleep 5
conky
```
Save it in your home folder and right click it>Permissions tab>Allow executing.
Go to System>Preferences>Startup Applications.
Create a new entry, name it conky (or whatever) and give
```
bash /home/yourusername/conky_start
```
as its command.
Log out and then log in.

---

### Post by stinkeye on 2011-02-28
You'll find this helpful.
[**_[COLOR="DarkRed"]HOW TO: A Beginners Guide to Setting up Conky[/COLOR]_**]("http://ubuntuforums.org/showthread.php?p=5436679#post5437628")

---

### Post by aussie_g on 2011-02-28
Well I got it all sorted - thanks guys...

Whipped up a config for it that suits what I need - found one online & just modified it to suit me.

Thanks guys...

---

