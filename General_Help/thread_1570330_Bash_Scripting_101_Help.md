---
title: "Bash Scripting 101 Help"
date: 2010-09-08
forum: General Help
---

### Post by niugnep on 2010-09-08
Hi everyone I'm new here and I need some help on some Bash scripting 101. My background with linux is I'm pretty new to it. I've been using it on my netbook for the past few months but nothing hardcore. I know how to make directories, delete files and directories and use a little VI. I was introduced to Bash scripting by reading articles online stating creating these scripts are helpful. I would really like to know how to go about doing this but most of the articles I read assume I know at least some stuff about it and I don't know where to start. Can someone give me a brief over view of this? I know it's similar to Windows batch files but much more powerful. Thanks in advance hope to see you guys around.

---

### Post by harrismh777 on 2010-09-08
If you know a "little" VI, you know more about linux than you're telling.

:)

(and congratulations, 'cause real men use vi)   flamesuit: ON

[http://www.freeos.com/guides/lsst/](http://www.freeos.com/guides/lsst/)

See the above on-line tutorial on shell programming... very straight forward.

I would also recommend "Beginning Linux Programming 3rd Edition" chapter two (2) has a good into into shell programming ... its a Wrox book.

Get yourself a copy of O'Reilly's "Linux in a Nutshell" (I have the 5th edition, but get the latest) its the "Horse" cover.

Just in case you are so new to this that you might get a con job from somebody, be very leary about trying scripting commands recommended by well-meaning helpful types. Some of them are very dangerous. You shouldn't run into this around here, but it happens, so be careful. Scripting is *very* useful; so don't be afraid to dive in.

):P

---

### Post by xiboce on 2010-09-08
> **harrismh777 said:**
> 

(and congratulations, 'cause real men use vi)   flamesuit: ON


I would have supported the above statement is the gender wasn't involved :p

...oh ok, bad joke.

I would also suggest "learning bash" from oreilly as well. It has a couple of chapters meant as intro to new users.

---

### Post by niugnep on 2010-09-08
Thanks guys, I'm going to start reading up and maybe buy some books. I want to get a Linux certification and I found a Comptia Linux+ book at a garage sale, it was free so I guess I'll start there. My background isn't in tech but trying to change career paths. How long you guys think it will take? Oh and BTW when I mean I know "a little about VI" I really mean only just a little like :q! :wq and that's it! =P

---

### Post by harrismh777 on 2010-09-08
> **niugnep said:**
> Thanks guys, Oh and BTW when I mean I know "a little about VI" I really mean only just a little like :q! :wq and that's it! =P

That being the case, chapter nine (9) of the "Linux in a Nutshell" book covers vi, ex, and vim editors and (although not a tutorial) does a really good job of summing stuff up in a small space.

[http://www.linuxconfig.org/Vim_Tutorial](http://www.linuxconfig.org/Vim_Tutorial)


Learning vi takes some time and patience, but is well worth the effort, because *all* unix-like operating systems (and some others) ship with vi, and because vi can be used to configure, maintain, and control the system without a graphical interface or over the network from a minimal terminal and without special keys. Its just something that everyone should have in their tool box. 

The thing that stumps folks early on with vi is that it is a modal editor. ... meaning that the keyboard has two (or more) completely different set of functions depending which "mode" the editor is in. Pressing the ESC key is something you are going to want to remember right NOW. ,... places the editor into control mode (move the cursor around, give the editor commands, etc).  In this mode the "i" key will insert at the current position and place the editor into typing mode (enter characters into the file). The "a" key will insert "after" , etc. To get back to the control mode (to move the cursor again or give a command like search and replace 'n so forth just press the ESC key. 

The cursor movement keys are the h, j, k, l, keys (only in command control mode). Did I mention that pressing the ESC key will set the editor into command control mode?  Just checking...  :)

dd deletes a line
yy yanks a line
x deletes a character 

dive in and have fun. 


How long the learning curve will be for you depends on your personal initiative and drive, and how much effort you are will to put into it.


:D

---

