---
title: "&quot;echo $? &quot; what does that mean?"
date: 2011-04-04
forum: General Help
---

### Post by jiapei100 on 2011-04-04
Hi, all:

Sorry for my simple question again.
What does ```
echo $?
``` mean?

Command ```
echo
``` has been frequently used but I happened to come across this ```
$?
``` staff and I really have no idea what is it about??

Can anybody please help to explain it.


Best Regards
JIA

---

### Post by lithopsian on 2011-04-04
Very simply $? will give the exit status for a command.  Actually a little more than that, but close enough for government work.

---

### Post by jiapei100 on 2011-04-04
Thank you so much .
I got it !!
[http://www.cyberciti.biz/faq/shell-how-to-determine-the-exit-status-of-linux-and-unix-command/](http://www.cyberciti.biz/faq/shell-how-to-determine-the-exit-status-of-linux-and-unix-command/)

Thanks again !!!

Cheers
JIA

> **lithopsian said:**
> Very simply $? will give the exit status for a command.  Actually a little more than that, but close enough for government work.

---

### Post by Dupointx on 2011-04-04
Wait, I've seen echo with a $ before.
example:
```
echo $BASH_VERSION
```In this case you don't see
```
BASH_VERSION
```in the terminal you see the BASH version.

I just checked the Wikipedia article on BASH and it looks like the '$' signifies a BASH variable.
[http://en.wikipedia.org/wiki/Bash_%28Unix_shell%29]("http://en.wikipedia.org/wiki/Bash_%28Unix_shell%29")

[EDIT]: Ah, it looks like you were talking about "$?" never mind then. Thought you meant just $, sorry for not understanding.

---

### Post by CharlesA on 2011-04-04
Running:
```
echo $?
```

Will return the exit status of the last command you ran. Anything other then 0 means that the command didn't complete successfully.

---

