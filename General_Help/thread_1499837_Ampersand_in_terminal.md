---
title: "Ampersand in terminal"
date: 2010-06-02
forum: General Help
---

### Post by belnac on 2010-06-02
Hello,

Could anyone please explain why appending an ampersand at the end of a command line that executes a program, spawns the program and returns to the command prompt, as opposed to locking the terminal when no ampersand is appended? 

Example:

```
./nautilus &
```

The above would 'spawn' nautilus and return to the terminal straight away.

```
./nautilus
```

Without the ampersand the terminal is in a sort of locked state until the program terminates and all stdout output is shown.

---

### Post by rnerwein on 2010-06-02
> **belnac said:**
> Hello,

Could anyone please explain why appending an ampersand at the end of a command line that executes a program, spawns the program and returns to the command prompt, as opposed to locking the terminal when no ampersand is appended? 

Example:

```
./nautilus &
```The above would 'spawn' nautilus and return to the terminal straight away.

```
./nautilus
```Without the ampersand the terminal is in a sort of locked state until the program terminates and all stdout output is shown.

hi
that's the way the program is written.
if you give an & at the and of a command the shell will do an - fork-> fork->exec
the reason why nautilus isn't block your shell without a given &  is that nautilus do this fork->fork->exec ( and a little bit more) byself.
oh yes: fork = spawn 
if you give a command like: sleep 10  without & the shell will wait till the command is finished ( fork-> wait)

ciao

---

### Post by xolot1 on 2010-06-02
Putting an ampersand at the end of a command causes Bash, the shell, to run the process in the background. Its sort of like multi-tasking. You can have many processes running, but only one in the foreground at a given point. The process in the foreground is the process that appears to have locked up the terminal.  

You can use **jobs** to list the current running jobs for the terminal.

You can use the **&** to start a task in the background, or use the **bg** command to invoke it.

You can use **fg** to bring a task back into the foreground.


Example:

1)

```
willi@willi-desktop $ sleep 60
```

Notice how this locks up the terminal for a minute.


2)

```
willi@willi-desktop $ sleep 60 &
```

Notice how this does not lock up the terminal for a minute.
The task is still running however:

```

willi@willi-desktop $ jobs                                                                                          
[1]+  Running                 sleep 60 & 

```

You can bring it back into the foreground like so:

```
willi@willi-desktop $ fg 1                                                                                          
sleep 60 
```



I'm not sure how to put a task back into the background once its active, but there's probably a keyboard shortcut for it. Control-Z causes the process to suspend and be put into the background.


@rnerwein: This does _NOT_ have to do with the way the program was written, but rather how the shell was written. There are programs that detach themselves from the terminal (see many KDE programs), but this is a different case.

---

### Post by DavorC on 2010-06-02
Try 'man bash' or any of the shell tutorials.

In particular, from the man page:

> 
If  a  command  is terminated by the control operator **&**, the shell executes the command in the *background* in a subshell.  The shell does  not wait  for  the command to finish, and the return status is 0.  Commands separated by a ; are executed sequentially; the shell  waits  for  each command  to terminate in turn.  The return status is the exit status of the last command executed. [emphasis in the original]


---

### Post by Slim Odds on 2010-06-02
Yes, as was said, that's the way that it's designed to work.

You might find the Advanced Bash Scripting Guide very handy also: [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---

### Post by belnac on 2010-06-02
Fantastic replies, everyone. Thank you all!

---

