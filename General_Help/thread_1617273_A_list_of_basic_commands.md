---
title: "A list of basic commands"
date: 2010-11-09
forum: General Help
---

### Post by kanishkdudeja on 2010-11-09
From where can i get a list of basic commands that can be run from the terminal from ubuntu ?

for example:

nautilus
mount
top
apt-get

---

### Post by blazemore on 2010-11-09
Try this
[http://fosswire.com/post/2008/04/ubuntu-cheat-sheet/](http://fosswire.com/post/2008/04/ubuntu-cheat-sheet/)

---

### Post by kanishkdudeja on 2010-11-09
thanks

---

### Post by aktiwers on 2010-11-09
[img]http://security.crudtastic.com/wp-content/uploads/2010/09/linux-command-wallpaper.png[/img]

---

### Post by rnerwein on 2010-11-09
> **kanishkdudeja said:**
> From where can i get a list of basic commands that can be run from the terminal from ubuntu ?

for example:

nautilus
mount
top
apt-get
hi
try---> man man in a terminal. and you will wonder how much commands and .... on the system.
to print them out you have to convert it via nroff/ troff ( may be there is a easyer way - but i don't know it)
ciao
have fun

---

### Post by kanishkdudeja on 2010-11-09
thanks guys

---

### Post by Hippytaff on 2010-11-09
There are some here
 
[https://help.ubuntu.com/community/UsingTheTerminal#Commands](https://help.ubuntu.com/community/UsingTheTerminal#Commands)
 
[http://www.gnu.org/software/bash/manual/html_node/index.html](http://www.gnu.org/software/bash/manual/html_node/index.html)

---

### Post by kanishkdudeja on 2010-11-09
thnx

---

### Post by WorMzy on 2010-11-09
```
ls `echo $PATH | sed 's/:/ /g'` | sed 's/^\/.*://' | sed '/^$/d' | sort | less
```

Will give you an alphabetic list of the usable commands which you currently have installed.

---

### Post by Hippytaff on 2010-11-09
> **WorMzy said:**
> ```
ls `echo $PATH | sed 's/:/ /g'` | sed 's/^\/.*://' | sed '/^$/d' | sort | less
```
 
Will give you an alphabetic list of the usable commands which you currently have installed.
 
Nice - going into my useful commands file :-)

---

### Post by oldos2er on 2010-11-09
> **WorMzy said:**
> ```
ls `echo $PATH | sed 's/:/ /g'` | sed 's/^\/.*://' | sed '/^$/d' | sort | less
```

Will give you an alphabetic list of the usable commands which you currently have installed.

So will hitting Tab twice.  :)

---

### Post by Hippytaff on 2010-11-09
This is a good link too - [http://www.oreillynet.com/linux/cmd/](http://www.oreillynet.com/linux/cmd/)

---

### Post by WorMzy on 2010-11-09
> **oldos2er said:**
> So will hitting Tab twice.  :)

True, but unless you've set the scrollable lines count to infinite, you'd only be able to see the last few entries. :P

---

### Post by kaldor on 2010-11-09
> **oldos2er said:**
> So will hitting Tab twice.  :)

LOL nice! Thanks :)

---

### Post by oldos2er on 2010-11-09
> **WorMzy said:**
> True, but unless you've set the scrollable lines count to infinite, you'd only be able to see the last few entries. :P

In 10.10 it seems to pipe to 'more' automatically.

---

### Post by WorMzy on 2010-11-09
In that case you can only scroll one way, which is almost as bad. :P

Also, can you search in more? I haven't used it in years, since less is so much better at what it does.

(In all honesty, I *had* forgotten about double-TAB)

---

### Post by oldos2er on 2010-11-09
I agree 'less' is better. The man page for 'more' is a bit beyond my understanding, but apparently it can do some searching.

---

### Post by CharlesA on 2010-11-09
> **oldos2er said:**
> In 10.10 it seems to pipe to 'more' automatically.

That's nice. I remember the first time I did that, I got something like.. "Are you sure you want to display ALL entries" or something like that.

less is more, for sure. :)

---

