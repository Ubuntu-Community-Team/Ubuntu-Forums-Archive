---
title: "Bash script: export:bad interpreter"
date: 2010-05-15
forum: General Help
---

### Post by WitchCraft on 2010-05-15
Question: I get this error message:
> 
export: bad interpreter: No such file or directory


when I execute this bash script

```

#!/bin/bash
MONO_PREFIX=/opt/mono-2.6
GNOME_PREFIX=/opt/gnome-2.6
export DYLD_LIBRARY_PATH=$MONO_PREFIX/lib:$DYLD_LIBRARY_PATH
export LD_LIBRARY_PATH=$MONO_PREFIX/lib:$LD_LIBRARY_PATH
export C_INCLUDE_PATH=$MONO_PREFIX/include:$GNOME_PREFIX/include
export ACLOCAL_PATH=$MONO_PREFIX/share/aclocal
export PKG_CONFIG_PATH=$MONO_PREFIX/lib/pkgconfig:$GNOME_PREFIX/lib/pkgconfig
PATH=$MONO_PREFIX/bin:$PATH
PS1="[mono-2.6] \w @ "

```

But the bash path seems to be correct:
> 
asshat@IS1300:~/sources/mono-2.6# which bash
/bin/bash


```

asshat@IS1300:~# cd sources/
asshat@IS1300:~/sources# cd mono-2.6/
asshat@IS1300:~/sources/mono-2.6# ./mono-2.6-environment 
export: bad interpreter: No such file or directory
asshat@IS1300:~/sources/mono-2.6# ls
download  mono-2.4  mono-2.4-environment  mono-2.6  mono-2.6-environment
asshat@IS1300:~/sources/mono-2.6# cp mono-2.6-environment mono-2.6-environment.sh
asshat@IS1300:~/sources/mono-2.6# ./mono-2.6-environment.sh 
export: bad interpreter: No such file or directory
asshat@IS1300:~/sources/mono-2.6# ls
download  mono-2.4-environment  mono-2.6-environment
mono-2.4  mono-2.6              mono-2.6-environment.sh
asshat@IS1300:~/sources/mono-2.6# bash mono-2.6-environment
asshat@IS1300:~/sources/mono-2.6# 

```

What am I doing wrong? Or is this a Lucid bug?
[i did chmod + x]

---

### Post by gmargo on 2010-05-15
I don't know where the bad interpreter error message is coming from.  But you are using the script incorrectly.  You desire to modify your current shell's environment, so you must run the commands with the "source" command:
```

$ source mono-2.6-environment

```

---

### Post by WitchCraft on 2010-05-18
Shouldn't source interpret it as TCL script? This is a bash script

---

### Post by rnerwein on 2010-05-18
hi
just give it a try: 
vi your_script_name
and then: ESC : - set list - to see if you get some non printable pattern in your script.
when i do that i get the answer: bash: ./x: /bin/bash: Defekter Interpreter: No such file or directory
and in the shell try: echo $SHELL
to see which shell you are running. i know that in the orginal borne shell you can't call export and set the variable on the
same line.
ciao

---

### Post by gmargo on 2010-05-18
> **WitchCraft said:**
> Shouldn't source interpret it as TCL script? This is a bash script
Where in the world did you get that idea?

Read the bash(1) man page; the "source" command is explained in the "SHELL BUILTIN COMMANDS" section.

I'll bet _rnerwein_ has hit upon the answer - you must have bad characters in the file.

---

### Post by jobix on 2010-05-18
I was able to execute the script successfully on my 10.04 desktop.

You could try the elimination process to debug this issue. Start off with commenting out all but one line. Execute and see what happens. If there is no error, add another line in and execute. Reiterate the process until you find the offending line.

---

