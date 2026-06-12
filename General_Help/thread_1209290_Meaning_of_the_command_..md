---
title: "Meaning of the command ."
date: 2009-07-10
forum: General Help
---

### Post by jiraaya on 2009-07-10
Hi,
   Im new to linux. if i give just a . on the terminal, what meaning does it take?

---

### Post by Blacklightbulb on 2009-07-10
I didn't really understand your question but I'll reply anyways. If you want help with terminal commands type either.

```
*program --help*
```

or

```
man *program*
```

for the programs manual with commands obviously. If you type

```
man man
```

you get help about the manual command.

Hope I helped!!!

---

### Post by egalvan on 2009-07-10
> **jiraaya said:**
> Hi,
   Im new to linux. if i give just a . on the terminal, what meaning does it take?

it is meaningless by itself.

a dot ( . ) is used as a name for the current directory.
two dots ( .. )are  used as a name for the parent directory.

example

./filename

../filename

it is also used inside the filename as a separator...
if used at the beginning of a filename, it makes a file invisible to a regular directory listing.

There are other meanings. I don't recall them all. :)

---

### Post by sisco311 on 2009-07-10
> **egalvan said:**
> it is meaningless by itself.

...

There are other meanings. I don't recall them all. :)

It's a shorthand for the [source]("http://learnlinux.tsf.org.za/courses/build/shell-scripting/ch10s02.html") command and matches any single character in a [regular expression]("http://en.wikipedia.org/wiki/Regular_expression").

---

### Post by egalvan on 2009-07-10
> **sisco311 said:**
> It's a shorthand for the [source]("http://learnlinux.tsf.org.za/courses/build/shell-scripting/ch10s02.html") command and matches any single character in a [regular expression]("http://en.wikipedia.org/wiki/Regular_expression").

Except that his original question clearly stated...

**[COLOR="Red"]if i give just a .[/COLOR] on the terminal, what meaning does it take?**

In others words, if one types in JUST A PERIOD...

All the examples in the "source" command you cite show the period being used WITH other commands/information/filename/etc


for example...
When I type in JUST A PERIOD in a Hardy/Jaunty terminal, I get...

```
ernest@gx280:~$ .
bash: .: filename argument required
.: usage: . filename [arguments]
ernest@gx280:~$ 

```


BY ITSELF, a period mans nothing...

Used with commands, it has meanings.

---

### Post by sisco311 on 2009-07-10
> **egalvan said:**
> Except that his original question clearly stated...

**[COLOR="Red"]if i give just a .[/COLOR] on the terminal, what meaning does it take?**

In others words, if one types in JUST A PERIOD...

All the examples in the "source" command you cite show the period being used WITH other commands/information/filename/etc


for example...
When I type in JUST A PERIOD in a Hardy/Jaunty terminal, I get...

```
ernest@gx280:~$ .
bash: .: filename argument required
.: usage: . filename [arguments]
ernest@gx280:~$ 

```


BY ITSELF, a period mans nothing...

Used with commands, it has meanings.

semantics, semantics... :)

by itself, a period prints an error message about the usage, so it clearly means something. ;)

. (source) is a bash built-in command, even if you use it (incorrectly) without an argument.


/me wonders, what's the meaning of...
:)

---

### Post by LightningCrash on 2009-07-10
[http://www.ss64.com/bash/period.html](http://www.ss64.com/bash/period.html)

---

### Post by egalvan on 2009-07-10
> **sisco311 said:**
> **semantics, semantics... :)**

Yepper, absolutley, semantics...
but a computer has no concept of anything other than strict syntax.

> by itself, a period prints an error message about the usage, so it clearly means something. ;)

Yes, to a human it means an error message...
to the computer, it has no syntacticly correct meaning, so it complains.

> . (source) is a bash built-in command, even if you use it (incorrectly) without an argument.

Yes, but was his intention

```
cd .
```

or was his intention

```
. source
```

At least two posters here assumed that the missing piece was "source"
but his missing piece (or pieces) may have been something else.
Only the OP knows for sure what he left out :)
and only humans have a propensity for assuming...
computers just throw fits (errors) 

> 
/me wonders, what's the meaning of...
:)

Why wonder... just type in two periods and *see what happens*.

It's how I taught myself programming and computer operations on IBM mainframes in the early '70s.
I remember the day that resulted in my deleting the entire FORTRAN compiler and library... oops... 
it taught me a valuable lesson... 
computers do NOT assume ANYTHING, other than that you want your commands followed TO THE LETTER... oops...

---

### Post by doas777 on 2009-07-10
if I recall correctly, the command '.' is used to run the following command in the current user shell. the default is to run scripts in a child shell (which i think is done so that a script crash can never effect your command shells environment). if you want to run it in the current (perhaps you've temporarily change and env variable), then you have to use . to launch it. one upside is that you don't have to use './' before all your script names.
to use it, just put the name of an executable after:

```

alpha10@21of2:~/lib/bash$ cat ./testthing.sh
#!/bin/bash
for i in `seq 1 4`;
do
        echo "Hello"$i
done
alpha10@21of2:~/lib/bash$ . testthing.sh
Hello1
Hello2
Hello3
Hello4
alpha10@21of2:~/lib/bash$ 

```

---

### Post by Cl0ud9 on 2009-07-10
You can set "." to mean anything by making an alias in your .bashrc
```

alias .='apt-get moo'

```

---

### Post by egalvan on 2009-07-10
> **Cl0ud9 said:**
> You can set "." to mean anything by making an alias in your .bashrc
```

alias .='apt-get moo'

```

+1

Now THAT is thinking like a human! 

:lolflag:

---

