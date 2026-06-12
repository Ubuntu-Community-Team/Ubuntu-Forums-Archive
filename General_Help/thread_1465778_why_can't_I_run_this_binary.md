---
title: "why can't I run this binary?"
date: 2010-04-29
forum: General Help
---

### Post by Scooter_X on 2010-04-29
I'm going through a tutorial [here]("http://www.ee.surrey.ac.uk/Teaching/Unix/unix7.html") to help me know how to wander around my system in the terminal and just understand better on a general level. 

I'm trying to simply figure out how to compile and run some software from source. I get to my directory where the then installed binary sits. I understand I'm supposed to enter in the command:

> ./unitswhere 'units' is the name of my binary. But I then get the output:

> units: can't find units file '/usr/local/share/units.dat'...what? Why does it refer to that directory that's WAY out there? It seems like it's trying to outguess me on something? I don't know. Anyone out there that does? I'd appreciate an explanation, and help to know what to do to run this binary.

---

### Post by limey_rick on 2010-04-29
The output suggests that the program is looking for a file and the file does not exists. 

Does this help: [http://ss64.com/bash/units.html](http://ss64.com/bash/units.html)

I think you need to specify some parameters to help get this program to run, or install additional control files like units.dat in the correct place - just a guess.

---

