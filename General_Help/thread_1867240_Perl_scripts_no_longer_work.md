---
title: "Perl scripts no longer work"
date: 2011-10-22
forum: General Help
---

### Post by acidblue on 2011-10-22
I have some perl scripts I wrote some time ago, maybe 8-10 months ago. that for some reason no longer work.

Only thing that has changed is I upgraded from 10.04 to 10.10.
I have perl 5.10.1-12 installed according to Synaptic.
I don't remember what version I had when I wrote the scripts, I'm, 
guessing 5.006 since I have "use 5.006"  at the top of my scripts.

I have tried commenting out the "use 5.006" but that doesn't work.


Any ideas??
I could post the scripts if that would help.
BTW this is on a 64bit 10.10

---

### Post by gsmanners on 2011-10-22
Saying "no longer work" is too vague. How exactly do they fail?

---

### Post by acidblue on 2011-10-22
When Im in Padre IDE and I click 'run' nothing happens, 'Output' screen is blank.
Same thing when I try to run in terminal, nothing happens.

EDIT:
It seems this is a problem with the Padre IDE, i just checked again using>> 'perl filename.pl'
in a terminal and it works fine, just can't click on 'filename.pl' and use 'run in terminal' doing it this way doesn't work
even if I have "Execute as a Program " is checked.

---

### Post by T.J. on 2011-10-22
I can think of a few things that it might be, but without more information I'm afraid they will be rather vague.


The best thing to do is run the script manually in a terminal window to get the error output, then post it for us to see.


A few thoughts that might help you:

1.  Make sure that if you are not passing the perl command e.g" **perl** *scriptname* explicitly that "#!/usr/bin/perl" is at the top of the script.

2. Make sure that you have all the perl modules installed that your script requires.

3.  Check to see if you are using "strict" in some of your code.  The "strict" setting is a very easy way to make errors if you aren't familiar with it.

4. Make sure you aren't using something in your scripts that was depreciated between versions of perl.  Things like "suidperl" come to mind.

---

### Post by gsmanners on 2011-10-22
I'm not sure, but it might be related to this:

[Error with dependencies when trying to install PADRE]("https://bugs.launchpad.net/ubuntu/+source/padre/+bug/805186")

---

### Post by acidblue on 2011-10-22
Thanks for the replies.
Running manually from the terminal works fine, no error's.
This seems to be limited to the Padre IDE and clicking the script and choosing 'run in terminal'.

All my Perl scripts have the she-bang at the top and I do use 'use strict' most of the time.

Can anyone recommend another Perl IDE??

I rather like Padre, but having to go to the folder and run the script manually to test it is kinda a pain, it's much easier to run it form the IDE.
It seems Padre can run small scripts but can't run larger ones.
I have a script that is about 135 lines that just won't run in padre but runs fine manually from the terminal, go figure.

---

### Post by gsmanners on 2011-10-22
I don't normally mess with Perl, so I have no idea, but you can find a few Eclipse plugins. If you want something lightweight gedit can do proper syntax highlight for Perl and it has a built-in terminal.

---

### Post by acidblue on 2011-10-22
Just discovered Geany will do Perl syntax highlighting and I think it will do debugging as well.
Already had it installed and was using it for C, didn't know it could do Perl.

---

### Post by gsmanners on 2011-10-22
Whoa. Really? Geany is even better than I thought. :)

---

