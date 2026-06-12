---
title: "question about  shell script"
date: 2010-11-03
forum: General Help
---

### Post by oren tal on 2010-11-03
I am reading the free book linux 101 hacks.

The book show how to create a new command mkdircd, which create a new directory and then move you to the directory.

so it just to add the following function (down) to the .bash_profile

function mkdircd () { mkdir -p "$@" && eval cd
"\"\$$#\""; }

I have learn script to know that $ mean variable, but I still don't understand how this work.

Can someone explain to me, thanks.

---

### Post by andrewc6l on 2010-11-03
Here is a list of special shell variables that may interest you:
[http://unixhelp.ed.ac.uk/scrpt/scrpt2.2.2.html](http://unixhelp.ed.ac.uk/scrpt/scrpt2.2.2.html)

What your function is doing is two things: the easy part:

mkdir $@
 (that is, make a directory using all the arguments in the command line except the filename)

The more interesting part:
"\"\$$#\""

First thing that gets resolved is $# - which means "the number of arguments". If you do something like "mkdircd /tmp/foo" then $# will become 1 (since there is only one argument, /tmp/foo). If you had two arguments ("mkdir /tmp/a /tmp/b") then $# would be 2.

Next, the quoted things resolve to "$ followed by the number of arguments followed by ". In other words, in the typical case it's the equivalent of doing:
cd "$1"
(where $1 means the first argument passed, which is /tmp/foo). In the two-argument case, it would be equivalent to:
cd "$2"
so you'd end up going into the last directory that you created.

Kind of a neat trick.

---

### Post by Hippytaff on 2010-11-03
> **andrewc6l said:**
> Here is a list of special shell variables that may interest you:
[http://unixhelp.ed.ac.uk/scrpt/scrpt2.2.2.html](http://unixhelp.ed.ac.uk/scrpt/scrpt2.2.2.html)

What your function is doing is two things: the easy part:

mkdir $@
 (that is, make a directory using all the arguments in the command line except the filename)

The more interesting part:
"\"\$$#\""

First thing that gets resolved is $# - which means "the number of arguments". If you do something like "mkdircd /tmp/foo" then $# will become 1 (since there is only one argument, /tmp/foo). If you had two arguments ("mkdir /tmp/a /tmp/b") then $# would be 2.

Next, the quoted things resolve to "$ followed by the number of arguments followed by ". In other words, in the typical case it's the equivalent of doing:
cd "$1"
(where $1 means the first argument passed, which is /tmp/foo). In the two-argument case, it would be equivalent to:
cd "$2"
so you'd end up going into the last directory that you created.

Kind of a neat trick.
My word I wish I had your understanding of bash. Nice link too :-)

---

