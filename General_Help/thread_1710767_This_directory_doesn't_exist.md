---
title: "This directory doesn't exist?"
date: 2011-03-20
forum: General Help
---

### Post by chrisandchips on 2011-03-20
Hi, this is my first post in these forums so go easy :P

Basically my problem is that bash doesn't recognise all of the directories in my user folder. However it will find things that I've created myself, ie a folder called workspace which is where my eclipse workspace is located. 

Example: "cd ~/workspace" will get me into the folder i created called 'workspace' perfectly fine. However, "cd ~/documents' brings back "bash: cd: /home/chris/documents: No such file or directory".
But it's there because I can get to it in Nautilus! That's where I want to put all my python scripts but if i can't access that directory through terminal then there's not really much point.

Another example would be trying to follow instructions on downloaded files such as installing an icon set. I try and access "~/downloads" where nautilus tells me my downloaded .zip is but terminal doesn't think downloads exists.

Apologies if it's a really simple problem, I'm a relative newcomer to Ubuntu/Linux, I've started using it as my primary OS now as can't get on with Windows at all these days, and I have to say I'm amazed at how awesome Ubuntu actually is! 

If you could please help me I'd be most grateful, 

Cheers, 

Chris

P.S I'm running GNOME 2.32.0 if this helps

---

### Post by wojox on 2011-03-20
Linux is case sensitive. Did you rename Documents to documents? If not try Documents, Downloads...

---

### Post by AlphaLexman on 2011-03-20
Another way to see case sensitivity is like this...
```
cd ~/[d,D]ocuments
```
or,
```
cd ~/[d,D]ownloads
```
The square brackets denote an 'either, or' situation.

---

### Post by chrisandchips on 2011-03-21
Thanks, I don't know why I didn't think to do that! They are all 'Documents' and 'Downloads' with capital letters to start. Was able to reach them in terminal using a caps, and the either/or statement.

Thanks for your help.

---

