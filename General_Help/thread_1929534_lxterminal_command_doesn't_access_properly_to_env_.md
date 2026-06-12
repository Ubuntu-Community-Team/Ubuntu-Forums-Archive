---
title: "lxterminal command doesn't access properly to env variables"
date: 2012-02-22
forum: General Help
---

### Post by Luca Borrione on 2012-02-22
Hi guys,

I need to launch bash scripts I wrote with the command *lxterminal*. That because I added some custom links (launchers) to the start menu in order to access my scripts easily.
So, normally, I open my start-menu I go under a *Scripts* folder I added and I simply select the script I need .. a command is associated and executed which usually is something as
```
lxterminal --command "bash /home/foo/scripts/[myScriptName].sh"
```

As you can easily understand I created a folder inside my home called *scripts* where I store all my custom scripts.

Everything always worked great! :)
Until I had to access to env variables :(

For a script I'm writing I need to access to some env variables I exported in my *~/.bashrc* file as for example
```
export PATH=/opt/jdk1.6.0_22/bin:$PATH
export JAVA_HOME=/opt/jdk1.6.0_22
export JRE_HOME=/opt/jdk1.6.0_22
```

Everything is exported right as I have:

```
[B][COLOR="SeaGreen"]$ source ~/.bashrc
$ env | grep 'JAVA'[/COLOR][/B]
JAVA_HOME=/opt/jdk1.6.0_22
 
```

Now let's say I write a basic script like:
```
**[COLOR="Red"]#!/bin/bash[/COLOR]**

**[COLOR="RoyalBlue"]echo[/COLOR]** 'start'
**[COLOR="RoyalBlue"]echo[/COLOR]** $(env | grep HOME)
**[COLOR="RoyalBlue"]echo[/COLOR]** $(env | grep LOGNAME)
**[COLOR="RoyalBlue"]echo[/COLOR]** $(env | grep JAVA)
**[COLOR="RoyalBlue"]echo[/COLOR]** 'exiting'

**[COLOR="RoyalBlue"]sleep[/COLOR]** 5
**[COLOR="RoyalBlue"]exit[/COLOR]**
```

If I launch the script with the following mode, I correctly get the following output:
```
[B][COLOR="SeaGreen"]$ cd ~/scripts
$ bash '[myScriptName].sh'[/COLOR]
start
HOME=/home/foo/.config
LOGNAME=foo
JAVA_HOME=/opt/jdk1.6.0_22
exiting[/B]
```

But if I launch it the way I need, I don't have the expected output as above:
```
**[COLOR="SeaGreen"]$ lxterminal --command "bash /home/foo/scripts/[myScriptName].sh"[/COLOR]**

```
a new lxterminal window is correctly opening with the output:
```
[B]start
HOME=/home/foo XDG_CONFIG_HOME=/home/foo/.config
LOGNAME=foo

exiting[/B]
```

What's wrong? **I cannot access to any exported env vars** :(

---

### Post by Khayyam on 2012-02-22
Luca ...

Firstly does '--command' necessarily need to call bash, if the *.sh is execuable, and a "bash script", then it should work without it.

Secondly, does invoking bash with the '-c' (command) switch change the behavoir?

BTW .bashrc is only read for interactive shells.

HTH ... khay

---

### Post by Luca Borrione on 2012-02-22
Hello!

yes, you're right:
1) I can launch an executable bash script with simply:
```
lxterminal -e "/home/foo/scripts/[myScriptName].sh"
```

2) .bashrc is sourced only for interactive shells, so I solved using
```
lxterminal --command "bash -i home/foo/scripts/[myScriptName].sh"
```

Thank you! :)

Side notes:
a) I don't know if there's a better way to solve this issue in a more elegant way without using --comand as in point 1

b) I haven't succeeded in using the -c switch ... ???
I tried with no lucky
```
lxterminal -c "bash home/foo/scripts/[myScriptName].sh"
```
Maybe I haven't got you well ..

---

### Post by Khayyam on 2012-02-22
> **Luca Borrione said:**
> [...]Side notes:

a) I don't know if there's a better way to solve this issue in a more elegant way without using --comand

Like 'xterm', 'lxterminal' has the '-e' ('execute') switch, this would be the usual way of running an application/script in place of a shell. I'm not an 'lxterminal' user but I imagine it has the same features as xterm, rxvt, etc.

> **Luca Borrione said:**
> b) I haven't succeeded in using the -c switch ...

```
lxterminal -c "bash home/foo/scripts/[myScriptName].sh"
```

I wrote "invoking bash with the '-c" ('command') switch", so 'bash -c'. I think 'lxtermenal -e' would be the prefered method however.

best ... khay

---

