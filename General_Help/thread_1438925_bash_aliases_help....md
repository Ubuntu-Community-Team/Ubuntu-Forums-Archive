---
title: "bash aliases help..."
date: 2010-03-25
forum: General Help
---

### Post by blur xc on 2010-03-25
[FONT=Verdana]I've got all the standard bash aliases and I'm trying to add one feature but am having troubles.

I want to incorporate a pipe to more from the output of ls.  If I add the line:
```
alias ll='ls -lh --color=always | more
```into my .bashrc I get the page stops and color output of my current working directory, but if I try to list the contents of another direcotry as with
```
ll /etc
```obviously it will still just list my current working directory.

I tired these variations with the same results:
```
alias ll='ls -lh --color=always $* | more
``````
alias ll='ls -lh --color=always $1 | more
```I even copied a function from another website and modified it a bit:
[/FONT][FONT=Century Gothic][FONT=Verdana]```
function ll
{ 
    ls --color=always $* | more
    echo "$(ls -l $* | wc -l) files"
}
```With the same result.  It only ever lists my current directory.  How can I make this work?


Thanks,
BM
[/FONT]
[/FONT]

---

### Post by gmargo on 2010-03-25
Try this:
```

ll()
{
    ls -lh --color=always "$@" | more
}

```

---

### Post by wojox on 2010-03-25
Try this **alias ll='ls -lh --color=always | more'**

```
ll cd /etc
```

---

### Post by blur xc on 2010-03-25
Neither of the above suggestions worked (kind of)- but I have something that does, and I can't figure out why the others don't.

It looks like the $@ is the hot ticket - but explain to me why this works:
```
ll() { ls --color=always -lh "$@" | more; echo "$(ls -lh "$@" | wc -l) files"; }
```and this doesn't:
```
function lla()
{
    ls --color=always -lhA "$@" | more
    echo "$(ls -lA "$@" | wc -l) files"
}
```I've tried the 2nd with and without the () after the function declaration.  As far as I can tell- both are the same exact thing, just that the first one is bash shorthand, all stuck on one line (harder to read) and the 2nd example is in a more human readable long hand format.

This is making my head hurt.  Getting a result is good- but knowing why is a matter of principle.  I'm not going to sleep at night because of this...

Thanks,
BM

---

### Post by anarkhos on 2010-03-25
my filename is :/home/gavin/.bashrc

I think you are missing the trailing `'` character.

in my bashrc:
------------------------8<--------------------------

# The 'ls' family
alias a='ls -Al'
alias l='ls -Al'
alias la='ls -Al'               # show hidden files
alias ls='ls -hF --color'       # add colors for filetype recognition
alias lx='ls -lXB'              # sort by extension
alias lk='ls -lSr'              # sort by size
alias lc='ls -lcr'              # sort by change time
alias lu='ls -lur'              # sort by access time
alias lr='ls -lR'               # recursive ls
alias lt='ls -ltr'              # sort by date
alias lm='ls -al |more'         # pipe through 'more'
alias tree='tree -Csu'          # nice alternative to 'ls'

---

### Post by gmargo on 2010-03-26
> **blur xc said:**
> Neither of the above suggestions worked (kind of)- but I have something that does, and I can't figure out why the others don't.

It looks like the $@ is the hot ticket - but explain to me why this works:
```
ll() { ls --color=always -lh "$@" | more; echo "$(ls -lh "$@" | wc -l) files"; }
```and this doesn't:
```
function lla()
{
    ls --color=always -lhA "$@" | more
    echo "$(ls -lA "$@" | wc -l) files"
}
```I've tried the 2nd with and without the () after the function declaration.  As far as I can tell- both are the same exact thing, just that the first one is bash shorthand, all stuck on one line (harder to read) and the 2nd example is in a more human readable long hand format.

This is making my head hurt.  Getting a result is good- but knowing why is a matter of principle.  I'm not going to sleep at night because of this...

Thanks,
BM

Both of those functions (which, BTW, are _not_ the same) work fine for me.  On both bash-3.2.29 (Hardy) and bash-4.0.33 (Karmic).  What is not working for you?

---

### Post by blur xc on 2010-03-26
> **gmargo said:**
> Both of those functions (which, BTW, are _not_ the same) work fine for me.  On both bash-3.2.29 (Hardy) and bash-4.0.33 (Karmic).  What is not working for you?

Bash 3.2.48 (Jaunty), but I must have been having a retarded moment or something because it is working now...

Thanks,
BM

---

### Post by BenB1 on 2010-08-17
[blur xc]("http://ubuntuforums.org/member.php?u=848014") , Thank you for the chuckles in your signature.

---

