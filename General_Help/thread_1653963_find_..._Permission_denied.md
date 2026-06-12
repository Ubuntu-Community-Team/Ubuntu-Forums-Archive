---
title: "find ... Permission denied"
date: 2010-12-27
forum: General Help
---

### Post by MichaelBurns on 2010-12-27
How can I suppress the "Permission denied" lines in the output of find (without logging in as a sudoer)?  example:
```

user@computer:~$ find / -name foofile
:
:
find: `/lost+found': Permission denied
:
:

```
(i.e. hundreds of utterly useless "Permission denied" lines to sort through)

[i]
edit:  I tried
```

user@computer:~$ find / -name foofile | grep -v Permission

```
and variations of the same spirit, but it still outputs the "Permission denied" lines.  I don't understand this.
[/i]

---

### Post by noah++ on 2010-12-27
In this case, and in most cases when you are running stuff on the command line, **stderr** and **stdout **streams are being printed to the terminal. When you pipe a command's output with **| **operator, it is only piping **stdout**. These "permission denied" errors are sent through **stderr**, though.

To squelch these errors, you might try
```
*[I]find / -name foofile 2>&1 | grep -v Permission*[/I]
```
thus redirecting **stderr **to **stdout** before piping. (I have never tried that, but it seems like it should work.)

The common syntax I've used many times looks more like
```
*[I]find / -name foofile 2>/dev/null*[/I]
```
although that has the side effect of suppressing all error messages. I use it when I am comfortable enough there will be no errors, or that the errors won't tell me anything vital.

---

### Post by MichaelBurns on 2010-12-27
noah++, I hereby uprade you to prime!  So obvious and elegant.  I can't believe that I didn't think of that.  I'm glad that there are members such as yourself here.

edit: BTW, it worked like a charm (the /dev/null version; in my experience error messages are worthless).

---

### Post by noah++ on 2010-12-27
Aww.

**--noah++'**

---

