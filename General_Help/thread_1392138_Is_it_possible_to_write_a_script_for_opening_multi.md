---
title: "Is it possible to write a script for opening multiple programs?"
date: 2010-01-27
forum: General Help
---

### Post by Envergure on 2010-01-27
Hi, 

I'm wondering if it's possible to write some sort of script so I can have an icon on the desktop which opens a combination of programs I use together frequently.

Specifically, I would like to have an icon called "keyboard practice" which does the following:
1)  Open QJackCtrl and "click" on Start;
2)  Open the Hexter softsynth and make the Jack connections between it and my speakers;
3)  Make the Jack MIDI connection between my MIDI keyboard and Hexter.

---

### Post by t4thfavor on 2010-01-27
If you can learn what commandline options each program has, you will have a much easier time figuring this all out.

I would say theoretically it is possible, I just don't know the programs in question that well.

---

### Post by bodhi.zazen on 2010-01-27
yes you can do this easily.

You have to write a bash script, and you have to know the commands you want to run.

Look at the man pages for options.

[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)

---

### Post by t4thfavor on 2010-01-27
He was talking about doing all the program interop via the script so that the programs were already "hooked" together when they got started. If there are switches for that on the cli, it's possible, if not then better get coding.

---

### Post by AnWe on 2011-01-03
Sorry for digging up an old thread (was googling for a different problem regarding hexter and jack), but this is easy to do with qjackctl, i just did, so I might as well describe it in case anyone else wants to know. 

Use the patchbay in qjackctl, it manages presets for connections. There you define the connections you want (both midi and audio), save them as a patchbay definition and activate it. Whenever you start the relevant programs, qjackctl will now detect the new sockets and connect them the way you specified. There's a slight learning curve with the patchbay, but you wont break anything if you get it wrong, just experiment a bit to find out how it works.

Under the "options" tab in qjackctl setup, make sure "activate patchbay persistence" is checked and points to the correct patchbay definition.

You can also start the programs directly from qjackctl. Look at the "options" tab under "setup", there you can put commands that should start along the jack server. You don't even have to write a script, just separate the commands with semicolons as you would on a command line. 

Take care though, you may need to start them in the background (using &) since qjackctl may appear to hang otherwise (it will wait for the commands to finish before moving on). If qjackctl seems to hang after you've changed startup commands, have a look in the "messages" windows for errors or clues to what went wrong. 

You may also want to "killall" any programs you start this way on/after stopping the jack server.  Non-gui programs started in the background (e.g. a2jmidid) will otherwise just continue to run and bog down your system.

PS. Since hexter is mono out, you might need to define two "sockets" (for the left and right output channels on your soundcard) and connect them separately in the patchbay. If you put both channels in the same socket it will only connect to one channel, which is annoying.


/Andreas

---

