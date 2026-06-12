---
title: "write a script to cd into a directory"
date: 2010-04-27
forum: General Help
---

### Post by gamblor01 on 2010-04-27
I have come across this question many times and recently had this discussion again:

"I wrote a script to cd into a directory for me.  How come it doesn't work when I run it?"

I have seen some information out there on google but there doesn't seem to be one centralized answer, so I will try to offer one here.  For those of us that have taken an operating systems course, you should understand why already (or I am assuming you know, as processes are such a fundamental part of an operating system).  For everyone else, here is my simple/unofficial explanation, along with some suggestions on how to accomplish what you are after.  This assumes you are running a bash shell (run the command "echo $SHELL" if you aren't sure).  I can't be certain that all of the solutions below will work in all shells.

The shell, terminal, console, whatever you want to call it is a running process in the operating system.  It has what is known as an "environment".  You can see all of the variables in this environment by running the "set" command without any arguments.  When you invoke a script, you are actually spawning a child process, that has a totally different environment.  Any modifications made to the environment for the child process cannot be made to the parent environment.  For example:

```

bmayes@bdmlin:~$ cat foo.sh
#!/bin/bash

echo "starting script foo.sh"
export FOO="My parent won't save me!"
echo "$FOO"
echo "exiting script foo.sh"
bmayes@bdmlin:~$ echo $FOO

bmayes@bdmlin:~$ ./foo.sh 
starting script foo.sh
My parent won't save me!
exiting script foo.sh
bmayes@bdmlin:~$ echo $FOO

bmayes@bdmlin:~$

```Clearly you can see that when I echo the FOO environment variable in my shell nothing prints, both before and after the script.  In the child script however, I was able to successfully echo the variable FOO.

So a script alone will not force the variable to be set in the parent shell.  The same is true if we cd into another directory:

```

bmayes@bdmlin:~$ pwd
/home/bmayes
bmayes@bdmlin:~$ cat foo.sh
#!/bin/bash

cd /tmp
bmayes@bdmlin:~$ ./foo.sh 
bmayes@bdmlin:~$ pwd
/home/bmayes

```There are a few ways you can accomplish what you want however:

**1. Source the child script**

The syntax varies by shell but usually involves either . (aka "dot") or the source command:

```

bmayes@bdmlin:~$ pwd
/home/bmayes
bmayes@bdmlin:~$ . ./foo.sh
bmayes@bdmlin:/tmp$ pwd
/tmp

```**2. Create an alias**

You can create an alias for the cd command that you want to execute, assuming there are no arguments to pass.  If this is something you want to persist, then simply place the alias defintion in your .bashrc file:

```

alias cdlong='cd /some/really/long/path/here'

```**3. Create a function**

Let's suppose that you have two directories under the path /some/really/long/path/here -- one named foo and one named bar.  Instead of using the above alias to cd into the directory, and then subsequently cd into either subdirectory, we can create a function that uses the argument and executes the cd as one command.  Again, simply place this in your .bashrc if you will rely on it heavily (i.e. more than just the current session:

```

cdlongfunc () { cd "/some/really/long/path/here/$*"; }

```And now you can cd into the foo or the bar directory by passing them as an argument to the function.  For example, to cd into the directory /some/really/long/path/here/foo you would just type:

```

cdlongfunc foo

```You can also use the $1, $2, ..., $N syntax to accept N arguments and do what you want with them.  So feel free to do something like:

```

cdlongfunc2 () { cd "/some/really/long/path/$1/$2"; }

```and then

```

cdlongfunc2 here foo

```Hope this helps!  Feel free to add any comments if you have additional information that may be useful to others.

---

### Post by blur xc on 2010-04-27
Wow- there are some complicated ways of doing a relatively simple task.  It never occurred to me to write an script to cd into some long path.  I created aliases, which work great.  I have aliases to cd into my downloads, documents, videos, pictures and photos (off the top of my head).  On my system (amateur photog) my photos are on /media/FreeAgent_Drive/Photos (external 1tb drive) which is a pain to type, which is what prompted me to make aliases...

BM

---

### Post by kaibob on 2010-04-27
> **gamblor01 said:**
> Feel free to add any comments if you have additional information that may be useful to others.

The following FAQ deals with the same topic. It doesn't add anything new to what is covered in your post but explains the issue somewhat differently and might be of some help to others interested in this issue. 

[http://wiki.bash-hackers.org/mirroring/bashfaq/060](http://wiki.bash-hackers.org/mirroring/bashfaq/060)

---

