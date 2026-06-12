---
title: "My aliases are not working when I use ssh"
date: 2012-07-27
forum: General Help
---

### Post by lowell.dennis on 2012-07-27
I know that having output from .bashrc is not a wise thing to do, but to more easily demonstrate my problem, I added the following code snippet to my .bashrc file:

[INDENT]alias toupper='tr "[:lower:]" "[:upper:]"<<<'
    echo $( toupper "$PATH" )
[/INDENT] 
If I use "**ssh User@IP**" to start an ssh session I see my PATH all in caps.

However, if I use "**ssh User@IP ls**" I get the following error prior to the "ls" being executed:

[INDENT]*     /home/ldennis/.bashrc: line 102: toupper: command not found*
[/INDENT] 
Why is this?

Frustrated,

Lowell

---

### Post by hakermania on 2012-07-27
Well, that's a simple structure showing what the problem is:
YOUR BASH EXECUTES -> LOADS YOUR BASHRC -> YOU RUN SSH -> YOU LOGIN TO OTHER COMPUTER -> OTHER COMPUTER'S BASH EXECUTES -> LOADS ITS BASHRC

So, basically, when you run ssh and you login to the other computer you are not actually seeing your computer. You are inside a program (SSH) which shows you a prompt of the other computer.

So, you are working from inside a program which doesn't read your bashrc file. Instead, it reads the other machine's bashrc. So, you have to specify these aliases to the other machine as well.

My explanation isn't the best but I think you get the point... Your .bashrc file contain aliases for running command from withing your terminal. The command 'ssh' is such a command. Once you execute ssh, the .bashrc's aliases stop to work (which is logical, you are not about to run a command under your bash, your bash only knows that you have run ssh). So, ssh logins to the other computer, and loads its .bashrc file. Its aliases work for executing commands to the other machine.

---

### Post by TheFu on 2012-07-27
Basically, each user account on each machine has their own .files like .bashrc.  If both machines share the same {HOME} directory via NFS or some other shared disk storage method, then all the .bashrc file commands will be executed on both machines. 

However, if the storage is not shared, then a copy of your settings like this should be placed in your HOME on the other machine.  Further, if the other machine is not setup identical to your desktop, then those commands may not work in the expected way.  Different operating systems have different versions of all the programs, so they might behave differently.  For commands like 'tr', that doesn't happen very often anymore even when using Solaris, AIX, HP-UX, or any of the flavors of Linux, like Ubuntu.

There are other capabilities when connecting to other machines over the network, for example, a "login" connection isn't the same as a remote shell connection, so different .files can be invoked.  .bashrc does get invoked like you expect, but the ~./.login does not. There is a simple hierarchy in the order that these startup files are run. It is documented here: [http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_01.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_01.html)

---

### Post by Vaphell on 2012-07-27
you don't need aliases for the example you posted if you use bash - it supports to-upper and to-lower parameter expansion right off the bat
```
$ x="SoMe StRiNg"
$ echo ${x^^} ${x,,}
SOME STRING some string
```

---

