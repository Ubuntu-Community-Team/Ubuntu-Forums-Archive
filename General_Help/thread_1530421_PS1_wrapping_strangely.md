---
title: "PS1 wrapping strangely"
date: 2010-07-13
forum: General Help
---

### Post by asenine on 2010-07-13
When I try to use a custom PS1, specifically:

```
PS1='\[\033[01;31m[$(date|cut -c12-16)]\] ${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[01;34m\] \w \$\[\033[00m\] '
```

It seems to wrap on the next line at the first closing bracket (the one after the time is displayed).

Any ideas?

Thanks. :)

---

### Post by gmargo on 2010-07-14
While your $PS1 string worked for me, something seems unbalanced with the color sequence around the date.  Try this on for size:
```

PS1='\[\033[01;31m\][\A]\[\033[0m\] ${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[01;34m\] \w \$\[\033[0m\] '

```

---

### Post by asenine on 2010-07-14
> **gmargo said:**
> While your $PS1 string worked for me, something seems unbalanced with the color sequence around the date.  Try this on for size:
```

PS1='\[\033[01;31m\][\A]\[\033[0m\] ${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[01;34m\] \w \$\[\033[0m\] '

```

Wow, thanks! That works without wrapping :)

Solved. :D

---

### Post by khughitt on 2010-07-22
Hello, I'm having a similar issue with a modified PS1 I'm using: when hitting the up/down keys to scroll through the bash history, eventually the prompt becomes distorted and displays part of a command from the history (Same as [https://bugzilla.redhat.com/show_bug.cgi?id=344031](https://bugzilla.redhat.com/show_bug.cgi?id=344031)).

I've tried a few changes but have not had any luck fixing the problem.

Here is the setting I'm using:

```
export PS1="\e[7;2;35m[\u@\h \W]\$ \e[m "
```

Any suggestions?

Thanks!

---

### Post by gmargo on 2010-07-22
> **pwnedd said:**
> 
```
export PS1="\e[7;2;35m[\u@\h \W]\$ \e[m "
```Any suggestions?

Try this.  Added the "non-printing-character" wrappers (\[ ... \]).  No export needed.  See the "PROMPTING" section in the bash(1) man page for full info.
```

PS1="\[\e[7;2;35m\][\u@\h \W]\$ \[\e[m\] "

```

---

### Post by khughitt on 2010-07-23
Thanks gmargo! That worked like a charm. I took at look at the references section of the man pages, too, and that is quite helpful.

On a side-note, I've always been wondering about when "export" should be used, and when you can leave it out. Any suggestions?

Thanks again,

---

### Post by gmargo on 2010-07-24
> **pwnedd said:**
> On a side-note, I've always been wondering about when "export" should be used, and when you can leave it out. Any suggestions?

A shell variable that is "exported" becomes part of the environment for commands spawned by the shell.  This would included variables like TERM, PATH, LD_LIBRARY_PATH, MAIL, PATH, LS_COLORS.  Variables like PS1 have no use to spawned commands.  In fact, PS1 is sort of a special case and should not be exported because generally a $HOME/.bashrc file contains this line:
```

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

```which short-circuits the processing of the rest of the .bashrc file for non-interactive shells.

---

### Post by khughitt on 2010-07-26
> **gmargo said:**
> A shell variable that is "exported" becomes part of the environment for commands spawned by the shell.  This would included variables like TERM, PATH, LD_LIBRARY_PATH, MAIL, PATH, LS_COLORS.  Variables like PS1 have no use to spawned commands.  In fact, PS1 is sort of a special case and should not be exported because generally a $HOME/.bashrc file contains this line:
```

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

```which short-circuits the processing of the rest of the .bashrc file for non-interactive shells.

Ah got it. Thanks for the explanation! :)

Best,

---

