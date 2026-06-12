---
title: "Pipe and a simple command"
date: 2012-03-05
forum: General Help
---

### Post by badnack on 2012-03-05
Hello, i'm trying in these days to learn more about shell; i've seen the pipe command (whether we can call command the pipe;)) but i've a doubt; why this command it's not correct:
ls /usr/bin | grep firefox | eval
It doesn't lunch anything, what is the correct form?

---

### Post by matt_symes on 2012-03-05
Hi

> ls /usr/bin | grep firefox | eval

What are you trying to do ?

Piping data is very powerful but the data in the pipes from one command to the next have to make sense.

Take a look at this.

```
matthew@matthew-Aspire-7540:~$ ls /usr/bin | wc -l
1836
matthew@matthew-Aspire-7540:~$ 

```

The above lists item in the current directory and then pipes it into word count (wc) with the -l switch to list the number of lines.

It shows there are 1836 file and folders in the /usr/bin directory.

Kind regards

---

### Post by sudodus on 2012-03-05
From```
 man bash
``` you find

```
       eval [arg ...]
              The  args  are read and concatenated together into a single com&#8208;
              mand.  This command is then read and executed by the shell,  and
              its  exit status is returned as the value of eval.  If there are
              no args, or only null arguments, eval returns 0.

```but I think it is hard to use eval, so keep away from until you have gathered some experience!

What do you want to do?

---

### Post by badnack on 2012-03-05
Actually nothing important, i'd like just to learn how to use the pipe.
So how can i execute like that?
I would execute a program (with eval) that is the result of an exspression ( for example ls /usr/bin | grep firefox like before).

---

### Post by matt_symes on 2012-03-05
Hi

For this you do not need eval.

You can run the ls | grep pipe in a subshell. 

At the command prompt.

```
$(ls /usr/bin | grep firefox);
```

Kind regards

---

