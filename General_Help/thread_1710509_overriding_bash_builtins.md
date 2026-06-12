---
title: "overriding bash builtins"
date: 2011-03-19
forum: General Help
---

### Post by hwttdz on 2011-03-19
I'm used to being able to put a script in ~/bin and having it overrule the system version of a command.  However for "time" or "kill" since the bash shell implements a version of the command (i.e. /bin/ version is not used) doing this is not enough.  How can I get the shell to run my own version instead of the version in the shell.  

I understand the implications of doing this. I know what I'm doing, I can always /bin/whatever if I want to get the old version (or just chmod -x ~/bin/whatever).

---

### Post by andrewthomas on 2011-03-20
set your path = to ~/bin:$PATH

---

### Post by hwttdz on 2011-03-20
That doesn't work because the shell builtin takes precedence over the path (try it).  As shown by "type -a time".  So if one wants to do this one needs to disable the shell command, which is what "enable -n" can do for you.

---

### Post by The Cog on 2011-03-20
Quote the full path to the command, e.g.
/usr/bin/time ls
and bash won't use its inbuilt version.

---

### Post by tordeu on 2011-03-20
Try to define an alias for the command you want to use.

```
alias kill=/path/to/your/script
```When I do

```
alias kill="echo \"foo\""
```calling kill will print foo.

---

### Post by hwttdz on 2011-03-21
The issue with aliases (if I remember correctly) is that they only take precedence when at the beginning of the command line.  

The issue with always quoting the full path to everything is I'm lazy.

This is exactly what the enable command is for.

---

### Post by tordeu on 2011-03-21
> **hwttdz said:**
> The issue with aliases (if I remember correctly) is that they only take precedence when at the beginning of the command line.  

I thought that what you were doing is just call a program, so then alias would work. And it does not necessarily need to be at the beginning of the command line, it needs to be where a command is expected.

with 
```

alias kill="echo\"foo\""

```

these will still work, although they are not the first thing at the command line:
```

echo "bar" && kill
echo | kill

```
(especially the second one does not make any sense, but the kill alias is used)

> **hwttdz said:**
> 
The issue with always quoting the full path to everything is I'm lazy.

This is exactly what the enable command is for.

Sure, enable is also a possibility. Just don't forget you disabled something. This could lead to strange problems as well once you want to use that command again and you forgot you disabled it in the first place ;)

---

