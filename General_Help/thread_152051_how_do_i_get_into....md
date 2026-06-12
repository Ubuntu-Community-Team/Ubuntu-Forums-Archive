---
title: "how do i get into..."
date: 2006-03-29
forum: General Help
---

### Post by master5o1 on 2006-03-29
the root or sudo thing.

i've just started to use Ubuntu. used linpsire before... but want to install firefox1.5.0.1 but don't know how to do it...i think i need to be in the root account.

help, thanks!

---

### Post by TmP on 2006-03-29
Thats a hard question.. 

Firefox 1.5 isn't officially supported by this version of Ubuntu.

You should assign a root account password:
[http://ubuntuguide.org/#setchangeenablerootpassword](http://ubuntuguide.org/#setchangeenablerootpassword)

then open a console and type "sudo" in front of stuff you need to run as root.

Basically you can only use the programs available from Synaptics menu. They're tested to be compatible.

---

### Post by master5o1 on 2006-03-29
what? where...im, yeah,...

---

### Post by NewWithoutClue on 2006-03-29
With all due respect.. the sudo/root question has been asked more then any other question i've seen... please take advantage of the forums "Search" function.. again I am not trying to be a prick here..

---

### Post by frup on 2006-03-29
[QUOTE=master5o1]what? where...im, yeah,...[/QUOTE]


system/administration/synaptic package manager. almost like your little CNR :D

---

### Post by master5o1 on 2006-03-29
i dont care of you are or are not trying to be a prick...lol.

---

### Post by TmP on 2006-03-29
I'll try to explain.

You run Ubuntu as a user. Users dont have rights to do many things.
Why? If a virus were to infect Ubuntu, it couldn't go outside of the user privilages. It could wreck some havoc but not destroy the system.

So if you want to make some important stuff, like installing software, you need to have administrator privilages, that is you need to be a "root" user. 

For some unnown reason the root user account doesn't have a password when you start a new Ubuntu. In order to become a "root", you need to assign such a password.

To do that, you have to open a console terminal: it's the black window with the message prompt where oyu type commands.

Look up Ubuntu Wiki.
Check the link to [www.ubuntuguide.org](www.ubuntuguide.org).
Search the forums. 

Good luck.

---

