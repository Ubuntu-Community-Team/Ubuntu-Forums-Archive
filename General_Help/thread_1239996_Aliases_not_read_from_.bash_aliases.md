---
title: "Aliases not read from .bash_aliases"
date: 2009-08-14
forum: General Help
---

### Post by SuaSwe on 2009-08-14
Good morning everyone!

Since upgrading to Jaunty, ~/.bash_aliases isn't working. The lines referring to it in ~/.bashrc are still present and uncommented, and I have changed nothing in the alias file (or indeed the .bashrc file) since the upgrade from Intrepid. I don't have the actual file to hand (am at work and will not have internet at home for a week - the horror!) but all entries go a little something like this:

```

# Some useful aliases
alias agi='sudo aptitude install'
alias agu='sudo aptitude update'

```

... and so on. When I try running them in Terminal all I get is the standard 

> 
#suave@home:$ agi sound-juicer
-bash: agi: command not found


The commands themselves, when typed in full, work perfectly fine.

Any suggestions much appreciated, otherwise I'll just fiddle with it again when I get home!

---

### Post by ajgreeny on 2009-08-14
It certainly works OK in my system; I've just tried it out in my .bash_aliases file

Make sure the paragraphs in .bashrc look exactly like this
```
# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

```
Perhaps yours has a slightly different layout or something is not quite right.

---

### Post by SuaSwe on 2009-08-14
Quoting from memory, that is exactly what it looks like, unchanged from the Intrepid days. Thanks a bunch though, I shall make a note in my notebook (I know, stone age or what?) and cross-check when I get home!

---

### Post by SuaSwe on 2009-08-17
Update on this:

Had a look in .bash_aliases, removed some superfluous (but correctly entered!) commands and lo and behold, it now works. :) It probably just needed a sharp kick.

---

