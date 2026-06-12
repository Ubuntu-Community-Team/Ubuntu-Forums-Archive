---
title: "what does the &quot;$&quot; sign mean in  the terminal"
date: 2011-09-29
forum: General Help
---

### Post by oleink on 2011-09-29
I've always wondered about this what does the "$" indicate in the terminal/command line

---

### Post by haqking on 2011-09-29
> **oleink said:**
> I've always wondered about this what does the "$" indicate in the terminal/command line

means a normal user, some unix systems end the prompt with % which means same thing.

# means a root user

---

### Post by jwbrase on 2011-09-29
> **oleink said:**
> I've always wondered about this what does the "$" indicate in the terminal/command line

Pretty much it's just there as a separator between the prompt and what you actually type. It's like the > in a Windows/DOS prompt.

```
username@computer:~$
```

on Linux (or any other system that uses bash or a similar shell) is pretty much the same as:

```
C:\My Documents>
```

on Windows.

---

### Post by sisco311 on 2011-09-29
Traditionally, a shell prompt either ends with $, % or #. If it ends with $, this indicates a shell that's compatible with the Bourne shell (such as a POSIX shell, or a Korn shell, or Bash). If it ends with %, this indicates a C shell (csh or tcsh).  If it ends with #, this indicates that the shell is running as the system's superuser account (root), and that you should be extra careful.

Prompts are often highly individualized. Your Bash prompt will probably be much longer than $.

Also in Bash, $ usually means "Expand". It is not part of your variable name! You can expand "$variable" content, "$(command)" output or "$((arithmetic))" results.

Used as a special parameter $ expands to the PID of the shell: **echo $$**

Bash also supports $"..." quoting syntax for locale-specific translation. If the current locale is C or POSIX, the dollar sign is ignored. If the string is translated and replaced, the replacement is double-quoted.

Bash also has a special form of quoting, $'string' in which backslash-character combinations are expanded. For example, echo $'this is a literal tab: \t'

$[...] is an obsolete, deprecated syntax for math.

---

### Post by elliotn on 2011-09-30
gee I wanted to know too. thanks

---

### Post by jwbrase on 2011-09-30
> **sisco311 said:**
> If it ends with %, this indicates a C shell (csh or tcsh).

zsh also uses % and is fairly Bourne-shell-like, though it has a lot of influence from csh by way of tcsh and ksh. (Also, tcsh as it comes from the Ubuntu repositories uses > as its default prompt character).

---

### Post by oleink on 2011-10-03
thanks a bunch guys! Very helpful

---

### Post by haqking on 2011-10-03
> **oleink said:**
> thanks a bunch guys! Very helpful

dont forget to mark as solved using thread tools ;-)

cheers

---

