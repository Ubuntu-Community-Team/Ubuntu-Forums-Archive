---
title: "Headers in shell scripts"
date: 2011-12-08
forum: General Help
---

### Post by achuth on 2011-12-08
Sir,
I would like to know whether the line "#!bin/bash" SHOULD be the first line of a script.
I have my programs working without that line however.
Can I ignore that line? What are the possible aftereffects of ignoring that line?
What shell will be assumed if we ignore that line in our shell script?

---

### Post by d2btoo on 2011-12-08
From "Advanced Bash-Scripting Guide - Mendel Cooper"

> 
The sha-bang ( #!) at the head of a script tells your system that this file is a set of commands to be fed to the command interpreter indicated. The #! is actually a two-byte magic number, a special marker that designates a file type, or in this case an executable shell script (type man magic for more details on this fascinating topic). Immediately following the sha-bang is a path name. This is the path to the program that interprets the commands in the script, whether it be a shell, a programming language, or a utility. This command interpreter then executes the commands in the script, starting at the top (the line following the sha-bang line), and ignoring comments.

#!/bin/sh
#!/bin/bash
#!/usr/bin/perl
#!/usr/bin/tcl
#!/bin/sed -f
#!/usr/awk -f

Each of the above script header lines calls a different command interpreter, be it /bin/sh, the default shell (bash in a Linux system) or otherwise. Using #!/bin/sh, the default Bourne shell in most commercial variants of UNIX, makes the script portable to non-Linux machines, though you sacrifice Bash-specific features. The script will, however, conform to the POSIX sh standard. 

Note that the path given at the "sha-bang" must be correct, otherwise an error message -- usually "Command not found." -- will be the only result of running the script.
 
#! can be omitted if the script consists only of a set of generic system commands, using no internal shell directives.

Note again that #!/bin/sh invokes the default shell interpreter, which defaults to /bin/bash on a Linux machine.


HTH
d2b

---

### Post by mcduck on 2011-12-08
the shebang tells which shell should be used to execute the script, so if you want to make sure it runs correctly and that you can run the script without having to specify the shell to use when executing the script you should definitely include the shebang. Even more so if you want to distribute the script to other people or make sure it runs on different distributions etc.

It's even more important if you use any Bash-specific features, as for example Ubuntu's default shell (/bin/sh) is actually Dash. (same of course aplies to any other shell that's not Bourne Shell compatible or has additional features that aren't in Bourne Shell)

If you don't include the line, you can run the script if you specify the shell in the command, for example "sh myscript.sh" or "bash myscript.sh". Otherwise the shell used depends on what's the default shell for the user running it. (if you try to use it as system script, executed by cron, any other system script, by the desktop manager when logging in or something like that, the script would be executed using Dash. And if you'd execute it yourself from a terminal it would be interpreted with Bash instead.

Since adding the line doesn't take much extra work, I can't really see any reason not to always add it to your scripts.

Edit:
Just to  make sure you'd notice this important thing, the quote in d2btoo's post is wrong about the default shell (/bin/sh) being Bash on Linux systems. It's true for many distributions, but Ubuntu uses Dash as system shell and Bash only as the login shell for users. So unless you specify the shell, any bash-specifics in system scripts will result in errors. (The reason for the use of Dash is that it's much more lightweight and is able to execute all the system scipts in noticeably shorter time than Bash is. For example the boot times of Ubuntu were considerably reduced as a result from this change. On the other hand it's not comaptible with Bash so using it as login shell for users might cause confusion for people who are used to Bash-specific features on other Linux systems.)

---

### Post by achuth on 2011-12-08
Sir,
I modified the she-bang line as
"#!/bin/bashxyzsdsdf"

That is I added some extra alphabets purposefully.
But I was able to execute the script using "sh mycode.sh" 
What is the reason for this?
I told it to use the the shell called "bashxyzsdsdf" which is not available.
But still the script runs with no problem.
I also saw the following in Wikipedia:
*"Since the initial [number sign]("http://en.wikipedia.org/wiki/Number_sign") is also the character introducing comments in the [Bourne shell]("http://en.wikipedia.org/wiki/Bourne_shell")  and many other interpreters, that interpreter directive itself is  considered by the interpreter to be merely a comment, and skipped.However, it is up to the interpreter to ignore the shebang line*"

[B]Why I am able to execute my shell script even though it specified the shell path(name) incorrectly?
[/B]

---

### Post by CharlesA on 2011-12-08
You told sh to execute the script.

If you ran the script like this:

```
./script
```

It would not run.

---

### Post by mcduck on 2011-12-09
> **CharlesA said:**
> You told sh to execute the script.

If you ran the script like this:

```
./script
```

It would not run.

True, and same of course applies had you tried to double-click it to launch it from GUI, add it to your startup scripts, launcher icons, or any other situation where you don't directy specify the shell to be used for executing the script.

---

### Post by achuth on 2011-12-13
Oh...!!! Thanks..

---

### Post by CharlesA on 2011-12-13
> **achuth said:**
> Oh...!!! Thanks..
No problem. :)

---

