---
title: "Terminal Question"
date: 2010-04-26
forum: General Help
---

### Post by Granny_Geek on 2010-04-26
Is it possible for me to create a document/note using the terminal? If so how, also is it safe? Granny

---

### Post by kaibob on 2010-04-27
You can, of course, start a text editor or similar from a terminal window and create a note or document. I assume you are not asking about this.

You can create a text file with the terminal window alone as shown below. Once finished, you end things with a ctrl-d. With rare exception, there is no reason you should use this to create a note or document. It is safe, though. 

> $ cat > file
This is line 1
This is line 2
This is line 3

$ cat file
This is line 1
This is line 2
This is line 3

---

### Post by thiemster on 2010-04-27
> **Granny_Geek said:**
> Is it possible for me to create a document/note using the terminal? If so how, also is it safe? Granny

It's not only possible, it's very easy as well.
The easiest program would probably be nano. I'm not sure if it's installed by default in Ubuntu, but it probably is. Run "nano" (without quotes) from the terminal.

And yes, it's safe ;)

---

### Post by Granny_Geek on 2010-04-27
Thanks kaibob and Thiemstr for your replies:-)

---

### Post by mcoleman44 on 2010-04-27
You can use pico too. And if you want the output of a command to go to a text file then you could do something like this:
```
lshal >lshal.txt
``` lshal.txt will now show up in your home directory.

---

### Post by rjcroy on 2010-04-27
Nano is indeed installed by default. I agree it is probably the most user friendly text editor for terminals.

---

