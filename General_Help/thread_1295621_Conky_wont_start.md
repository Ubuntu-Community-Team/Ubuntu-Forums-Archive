---
title: "Conky wont start"
date: 2009-10-19
forum: General Help
---

### Post by Vrekk on 2009-10-19
When i try to start up conky i just get this error and i have no idea how to fix it.

```
Conky: missing text block in configuration; exiting
***** Imlib2 Developer Warning ***** :
	This program is calling the Imlib call:

	imlib_context_free();

	With the parameter:

	context

	being NULL. Please fix your program.

```

First time trying conky so i dont have any thing special in my .conkyrc file

---

### Post by squaregoldfish on 2009-10-19
Conky only displays the stuff from the config file after a line say simply says TEXT.

It seems that you're missing this line.

Steve.

---

### Post by VCoolio on 2009-10-19
You need a conky config file. The first line of the message suggests you don't have one, at least not one with config first, then a line that says "TEXT" and then the contents you want to display. Google for conky and you'll find plenty of configs. The default path for it is ~/.conkyrc and if you run "conky -C > ~/.conkyrc" you´ll get a default config file that you can tweak. 
Read the last pages of [this thread]("http://ubuntuforums.org/showthread.php?p=8006534#post8006534") for more inspiration and also you can ask questions there (it's the sticky "howto of the week"). [Here]("http://conky.linux-hardcore.com/") you can also find nice setups and howtos.

If you still have difficulties, post your conky config with your question.

---

### Post by Vrekk on 2009-10-19
Man I need to learn to troubleshoot more before I post to you guys :|.

Just one question then, how can i make it output what Im listening to (either rhythmbox or xmms2, whichever is easier)

---

### Post by Vrekk on 2009-10-19
Ok one other thing, conky is reporting my mem usage at 98% of my 2gbs while System Monitor is reporting my using 54# of it. I dont have any swap, so that not the reason.

---

### Post by Vrekk on 2009-10-19
Ok im making this thread as solved :D as the problems I listed early are running great now. Thanks for the help getting conky running.

---

