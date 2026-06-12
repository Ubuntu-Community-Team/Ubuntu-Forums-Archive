---
title: "Two questions from a newbie"
date: 2010-04-08
forum: General Help
---

### Post by J-Sigaard on 2010-04-08
I have two questions, as the title suggests;

First off, I have been quite clumsy lately. I recently poured water into my computer by accident; and it works somewhat fine, though the keys A and E do not work. At this point I am using an external keyboard, but since it's a laptop and I am using it at school, that is not what one would wish for.
So, my question is; is there any way which will allow me to use the Keyboard Shortcuts to make a shortcut which will for example use ALT+Ctrl+<button> to write the letter A?

My second question is;
Do anyone know what has happened with what I will describe in the following text; or perhaps recognice the problem and a solution?
One of my friends has installed XUbuntu on his netbook. It has been running just fine; and for a while after he upgraded to 9.10, his computer went somewhat broke. It boots up fine, and it loads the login screen; but instead of being able to log in, it switches to a terminal. We have tried using it to log in, but as none of us are any good with the terminal we have not succeeded. Attempts at making backups from his /home folder has gone wrong too.

Sorry for the somewhat long questions, and for a possible wrong placement in the forum.
I hope you can understand what I write, and even come up with some kind of answer/help

Best regards
Jesper Sigaard

---

### Post by Vaphell on 2010-04-08
[http://hektor.umcs.lublin.pl/~mikosmul/computing/articles/custom-keyboard-layouts-xkb.html](http://hektor.umcs.lublin.pl/~mikosmul/computing/articles/custom-keyboard-layouts-xkb.html)

look into it, maybe you'll manage to go around the non-working a and e

---

### Post by partloer on 2010-04-08
Hi Jesper Sigaard,

Second Question:
When upgrading to 9.10 many times something broke for people (including me) and X11 doesn't work anymore.  A couple options would to backup the data and install a fresh copy of 9.10 (or wait for 10.04).  The other option would be try and work on this to try and get X11 the load.  

For either of the above options I would backup everything this can be done by either a USB flash drive, USB external hard drive, or transfer to another computer on a network.  This all depends on how much data you need to backup and what you have for equipment.

Let me know I and will try and help you.

---

### Post by J-Sigaard on 2010-04-09
Well, thanks to you both :)

But;
Vaphell, I tried your link, and it seems to be what I need; but the files that need editing I do not have, and I have not had success trying to install either Xfree86 or X.org.
This might just be because I am a bit dumb when it comes to this operating system, though.

Partloer, it would be great if we could make a full backup, but as I wrote in my original post, we tried to copy his home folder with; cp -r /home/ <destination> but we did not succed.

So, any further help would be very appreciated!

---

### Post by partloer on 2010-04-10
J-Sigaard,

How are you trying to backup the directory?  When you say that you didn't succeed in backing up the home directory what went wrong (error message, doesn't work, not sure how)?

---

### Post by J-Sigaard on 2010-04-12
Well there was no error message, but it did not copy either. It made an empty line in which the cursor blinked in the terminal, and then after some time it returned with the user name.

---

### Post by partloer on 2010-04-12
Have you tried just writing to your backup location to make sure that you have permission to write to it?

Another option would be to try rsync and see if you get the same results.

---

