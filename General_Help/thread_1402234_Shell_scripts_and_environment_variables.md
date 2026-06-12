---
title: "Shell scripts and environment variables"
date: 2010-02-08
forum: General Help
---

### Post by brettg on 2010-02-08
Hey, I'm trying to write a simple shell script, its purpose is not important.

The script needs to make use of the system $HOSTNAME environment variable.

I had a look at this [page]("http://www.linux.org/lessons/advanced/x1110.html") which provides the following example.

```
#!/bin/sh

echo "You are user $UID on $HOSTNAME"
echo "Your home directory is: $HOME"
echo "$HOSTNAME is running $OSTYPE"
```

Which is supposed to produce the following output;

```
You are user 500 on penguin.linux.ork
Your home directory is: /home/mike
penguin.linux.ork is running linux-gnu
```

It does not produce that output, instead I get this;

```
You are user  on 
Your home directory is: /home/brettg
 is running 
```

If I change the shebang to use bash it works OK. I don't want to do that because the script I'm writing also has to work on FreeBSD machines which don't have bash (although it can be installed separately)

As always, all ideas welcome!

---

### Post by n0dix on 2010-02-08
Try to run those commands in the console. 
```
echo $HOSTNAME
```
I think it is a problem with your .bashrc file.

---

### Post by jken146 on 2010-02-08
That's a difference between bash and sh.  Read the manpage *environ*.

---

### Post by abhishek.malhotra35 on 2010-02-08
Try to echo the environment variables that you are planning to use. The script you have written is correct.

---

### Post by brettg on 2010-02-08
> Try to run those commands in the console.
Code:

echo $HOSTNAME

I think it is a problem with your .bashrc file.

Doing that works fine (console uses bash, which does work) the problem is related to /bin/sh not /bin/bash.

> That's a difference between bash and sh. Read the manpage environ.

OK, thanks, I will take a look.

---

### Post by john newbuntu on 2010-02-09
In Bourne shell something like this ought to work:

echo "You are user `whoami` (`id -u`) on " `hostname`
echo "Your home directory is: $HOME"
echo "`hostname` is running `uname -o`"

---

### Post by brettg on 2010-02-09
Thanks John, that's a good workaround, thanks.

---

