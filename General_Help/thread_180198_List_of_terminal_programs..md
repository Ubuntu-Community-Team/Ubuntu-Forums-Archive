---
title: "List of terminal programs."
date: 2006-05-21
forum: General Help
---

### Post by eugman on 2006-05-21
I'm not sure exactly where this should go so someone might want to move it.

I'm new to linux and I've been learning that you can do alot without a gui. Unfortunately I've had to find out about irssi,lynx,typespeed and other stuff on my own. So I thought it's be great to have a big list of common termina programs so people could learn what was used for what.

I'm still quite new to all this so I'm going to need people to post programs since I really can't tell you the difference between pine and mutt.

Just to keep things sinple, Post the general use, the name, and a one sentence description. Then I'll edit into a list in this post.
Examples:
Irc - Irssi - A very popular irc client with support for plugins and scripting.
Games - Bombardier - A fun game where you drop bombs to dlowly destroy a city.
Web - Lynx - A very common terminal browser. Somewhat lacking in features.


Then again there is probably a better way to do this.

Also , as a side note, does anyone know if any overkill servers still exist? It seems like a cool game but it's website says that none in it's list are up.

---

### Post by Harold P on 2006-05-21
CenterICQ is also a good "terminal program". It's a chat client for AIM, MSN, Yahoo, IRC (I think), and of course, ICQ.

It's available through apt:

$ sudo apt-get install centericq

As for overkill, can't help you there. Sorry. :/

---

### Post by johwel on 2008-02-13
Hi everyone,

I know this is an old thread, but for anyone who wondered also like me how to find all the terminal programs - a listing under the /usr/bin directory should reveal a lot of programs, including those running in the window environment.

Do a listing as folows in a terminal session:

cd /usr/bin
ls -l

If you recognise a program, you can run it by simply typing its name. Those with "rwxr-xr-x" rights should be programs and more or less save to try.

---

### Post by johwel on 2008-02-13
Sorry for a second reply, but before trying any of those programs, it might be a good idea to call help or a manual description of the program by typing:

> 
(program name) --help


or

> 
man (program name)


The last quote should provide some information to compile a description list for programs.

---

