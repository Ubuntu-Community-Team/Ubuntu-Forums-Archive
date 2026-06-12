---
title: "'&gt;' Shell Command Overwriting?"
date: 2009-11-30
forum: General Help
---

### Post by Nekativ on 2009-11-30
I am trying to write the output of ttylog program to a text file.

ttylog > /home/user/log.txt

The '>' command basically writes the output of the program to a file, 'log.txt'. The problem is every time the program runs it overwrites 'log.txt' I am wondering if there is a way to make it so everytime it runs instead of overwriting the file it does something like, log1.txt, log2.txt, log3.txt, ect. 

I know you can do something like that with udev rules with /%n so I assume there must be some method for a shell command.

Any help would be appreciated =D

---

### Post by emigrant on 2009-11-30
you can ammend by this:

ttylog [COLOR=Red]>>[/COLOR] /home/user/log.txt

---

### Post by Nekativ on 2009-11-30
> **emigrant said:**
> you can ammend by this:

ttylog [COLOR=Red]>>[/COLOR] /home/user/log.txt

Thanks for the help, is there any place that I can find a list of commands like '>' and '>>' because I honestly do not know what they are called.

---

### Post by emigrant on 2009-11-30
a good one: :)
[http://linuxcommand.org/](http://linuxcommand.org/)

---

