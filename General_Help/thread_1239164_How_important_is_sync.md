---
title: "How important is sync?"
date: 2009-08-13
forum: General Help
---

### Post by Buce on 2009-08-13
I want to write a bash script called 'sync' and put it in my ~/bin directory, so that I can access it from the command line like any normal program. But it seems there's already a sync program in /bin. Can I name my script 'sync', or would that potentially harm my system?

---

### Post by nikhilk on 2009-08-13
sync is part of GNU coreutils. I strongly advise *against* name clashing with core applications of Linux. Renaming it to something else is my recommendation.

---

### Post by Buce on 2009-08-15
Alright, I'll name it syncro instead. I'm curious, though: if my PATH variable only points to my ~/bin directory when ~/.bashrc is sourced, wouldn't program naming conflicts only occur when I'm using an interactive command line?

And, now that I'm thinking about it, what's the best way to ensure that you don't give your personal scripts a name that's already taken by another command? 'man <program>' only works for installed programs, and won't work for shell builtins and such. I've just typed the potential name from a terminal before, but blindly entering commands makes me nervous. Is there a better way to go about it?

---

### Post by luscinius on 2009-08-15
You can start typing the command and press the tab key --- then it will complete it or suggest several variants (if more than one exists). This way you do not need to execute the command to check if it exists. Or you can type 
```
which <commmand-name>
```
--- it will find the location of the executable in the PATH.

---

### Post by Buce on 2009-08-15
But what about programs that are in the repos, but aren't installed on your system? I know there's apt-cache search/show, but that won't work for all commands -- aplay, for example, is pulled in with some alsa package or other. 'apt-cache show aplay' doesn't return any packages, and the output of 'apt-cache search aplay' wouldn't give me the impression that aplay was a command in and of itself. If I was an OSS user who wrote a personal 'aplay' script, then later switched to ALSA, I'd end up with a conflict similar to the one I would've had with the 'sync' script reference in my first post.

Hrm. I guess I could always use tab completion to see if, say, the 'foo' command exists on my system, and then, if it doesn't, try to execute 'foo' and see whether or not I get an error message like this:

```
$ foo
The program 'foo' is currently not installed.  You can install it by typing:
sudo apt-get install packagewhichcontainsfoocommand
bash: foo: command not found
```

It would be nice if there was a way to get this info with a command or something, though. Tab completion + trying the command just doesn't seem robust to me. There must be a routine that generates the message in the code block above by checking to see whether the command exists in a package in the repositories. Can that routine be called from the command line, or is it hidden away somewhere in one of the layers of apt or something?

---

### Post by mc4man on 2009-08-15
It's handled by the command-not-found package which is a collection of scripts that deal with this.

The main one is CommandNotFound.py
Inside the source is a fairly large list that has tons of commands - scan.data

(( there was an interesting post recently about having it offer to install the app for you when not installed, it was just an edit to the above.py but i decided to build a hardy package so still happen have the source .

Ex. picking an obscure name from scan.data

> doug@doug-laptop:~$ imon
The program 'imon' is currently not installed.  You can install it by typing:
sudo apt-get install isdnutils-base
Install it for you now? ([Y]/n)  
 

Edit when I say "tons" I mean just that, over 23,000 lines with multiples per line
searching scan.data for a contemplated name would give you a good idea if it was 'taken'

---

