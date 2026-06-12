---
title: "How do you use coproc???"
date: 2012-01-28
forum: General Help
---

### Post by compiz addict on 2012-01-28
after using this:
coproc minecraft { java blah blah blah ;}

I then do this:
echo say it works! >&${minecraft[1]}
I get this:
-bash: ${minecraft[1]}: ambiguous redirect

My question is: WHY? Isn't that how coproc works? Or at least, that's what every relevant page on the internet says.

Is there a better way to send input to a running process, and preferably receive output as well?

---

### Post by compiz addict on 2012-01-28
*bump*

btw, writing to /prod/somepid/fd/0 doesn't work. It says permission denied (even with sudo), and when I use sudo su it tells me the file is busy.

---

### Post by compiz addict on 2012-01-29
*double bump*
Sorry, I'm not very patient :P I've been Googleing alternative methods and found a way to get output from the program (kind of), and that's only because I found an addon for the program that writes everything to a file.

I also read the program needs to use stdin... is there any other way a program would be able to accept input from a terminal other than that? That's basically what this program is; a server console.

---

