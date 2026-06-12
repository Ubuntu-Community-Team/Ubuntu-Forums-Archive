---
title: "dividing stdin/stdout"
date: 2011-02-15
forum: General Help
---

### Post by stamoulohta on 2011-02-15
Hello guys,

I would really like some help with this. I've made myself a python program which asks the user for some info while it runs and then prints out the outcome. Lets assume that my program written in bash would look something like this:```
#!/bin/bash

echo -ne "let's meet!\nGive us your name > "
read name
echo $name

```
Now, if I waned to use my program with pipes "|" or ">", all I would have to do would be to add "**1>&2**" in the end of the first two lines.
like this:```
#! /bin/bash

echo -ne "let's meet!\nGive us your name > " 1>&2
read name 1>&2
echo $name

```
and even then using the "|" would be somewhat buggy.

is there any other way of expressing "**1>&2**" or controlling the *standard in* and *standard out* in bash? Something that when used will actually overwrite the pipes!

I thank you in advance,
George.

---

### Post by hawkmage on 2011-02-15
Why are you trying to add pipes into the shell script?  Pipes and redirection allow you to direct the output of an executable/script into another executable/script of file.  

Basically what your are doing with your "1>&2" is telling the shell to take stdout and send it to stderror.  So your echo statement ends up sending your string to stderror.  Then any output form the read command is sent to stderror.  Then you print out when you just read in.

Your example makes no sense, can you explain with using code what you are trying to do we may be able to point you in the correct direction.

---

### Post by stamoulohta on 2011-02-15
haha! I know my example doesn't make sense... but it's just an example. My actual code is in python and is 5 pages long..

Even using the code above, if i type:```
./nonsense >> names.txt
```I will end up with a file containing **only** the names of the users... and that is exactly what I want
**but**, if I type: ```
./nonsense | less
```
The script asks me for my input **inside** *less* and never prints the name I give it anywhere...

What I'm asking is If there is a way of correcting this so my script asks me in a normal tty for my input **and then** feeds it into *less*.

I hope this is clearer..(although it probably isn't ;))

---

### Post by AlphaLexman on 2011-02-15
I'm a little confused about your bash intentions for a python script. Does your python script give the desired output? Or are you just trying to keep it simple without giving away your code?

Maybe the tee command is what you're looking for:
```
echo $name | tee -a names.txt
```

---

### Post by stamoulohta on 2011-02-15
I Don't have a problem giving away my code.. I just try to keep this as simple as possible and in the forum's boundaries. Even if I used python code I would do it as an example like this:```
import sys
a = sys.stdout
b = open("/dev/pts/0", "w")
c = sys.stderr

#### TESTING PIPES
print a.isatty(), "--> stdout"
b.write(str(b.isatty())+" --> tty"+"\n")
c.write(str(c.isatty())+" --> err"+"\n")

a.write("this is in the pipe\n")
print "this is in the pipe"

b.write("this is not in the pipe\n")
sys.stdout = b
print "this is not in the pipe"

c.write("this is not in the pipe\n")
sys.stdout = c
print "this is not in the pipe"

#### SANITIZE
sys.stdout = sys.__stdout__
```
Both this and the Bash example do the same thing and lack in the same thing.. If I use the "|" pipe with them, they get buggy.

I am looking for a standard out/in/error manipulation way. How does Bash assign terminals/files etc to those?!

---

### Post by hawkmage on 2011-02-15
If you want both stdout and stderror to be passed into a pipe try this:
```
script.py 2>&1 | less
```This will cause the stderr (file handle 2) to be redirected to stdout (file handle 1) before piping into less.  

You have to keep in mind that when you use "|" the thing before it and after it are separate processes where the shell takes the stdout from the first one and sends it to the stdin of the other.

---

### Post by stamoulohta on 2011-02-16
Hey! That is my problem exactly!! They both pas to *less* standard input anyway!!

try this:```
#! /bin/bash

echo "standard out"
echo "error" 1>&2

```

and then:```
$ script | less
```
See? they both appear into *less* without me having to use the ***2>&1*** as you proposed.
My guess is that bash treats the whole tty file as an input for the pipe regardless if the script wrote on it via *stdout* or *stderr* So what can I do to keep the error messages **out** of the pipe? Something like a pseudoterminal or any other ideas?

Guys, thank you for your interest very much!
cheers.

---

