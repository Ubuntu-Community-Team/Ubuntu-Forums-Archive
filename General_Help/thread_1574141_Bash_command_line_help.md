---
title: "Bash command line help"
date: 2010-09-13
forum: General Help
---

### Post by leegold on 2010-09-13
Hi, say:

$ if
> cat flog.txt | grep 'c'
> then echo "cccc"
> fi;
c
cccc

this works but I am confused what the ">" are for?

if I try it all on one line:

$ if cat flog.txt | grep 'c' then echo "cccc" fi;

I get:
">" every time I press enter. So i don't understand what's going on.

I would like to run the it one line and with one pressing of enter just like simple commands like
$ cat flog.txt | grep 'c'
$ c

but one I start putting if -then -fi in the command  and this ">" returns all the time. How to run on one line w/no ">" returning?

Thanks,

Lee G.

---

### Post by libssd on 2010-09-13
All is revealed: [http://community.linuxmint.com/tutorial/view/100](http://community.linuxmint.com/tutorial/view/100)

> > and >> redirectors  -> Send output to a file instead of the terminal.

> is used to *overwrite* currently existing files contents and replace with the output from the new command.
>> is used to *append* information to currently existing files.  This is useful for logging.
Example: ps aux > processes.log  Sends the output of ps aux to the file processes.log for viewing the command output in a text editor and overwrites the current contents of the file. 

---

### Post by drhrich on 2010-09-13
Bash have 2 prompts, the normal one: $, and a secondary one: >.

The porpouse of this is simply mark when you are in a multiline command, like in your example.

if only end in a fi, until bash found it he will prompt whit >. The same will hapend if you leave a dangling ".

Bye

---

### Post by leegold on 2010-09-14
Could you re-elaborate?

I'm not getting it via posts or links here and I've google it exrensively.

---

### Post by dualbus on 2010-09-15
You should separate the if-then statement with semicolons like this:

```
if condition; then do-something; fi
```Like this:

```
if cat flog.txt | grep 'c'; then echo "cccc"; fi;
```

---

### Post by asmoore82 on 2010-09-15
When Bash prints a ">" prompt back to you, it's letting you know that you are
still finishing the previous command block.

You can change this by setting the internal variable "PS2"

pasted from my terminal...
```
$ if true
> then
> echo "True"
> fi
True
$ PS2="$ "
$ if true
$ then
$ echo "True"
$ fi
True
$
```

You can also customize the primary prompt by changing "PS1"

pasted from my terminal...
```
$ PS1="bash$ "
bash$ PS2="if$ "
bash$ if true
if$ then
if$ echo "True"
if$ fi
True
bash$
```

---

