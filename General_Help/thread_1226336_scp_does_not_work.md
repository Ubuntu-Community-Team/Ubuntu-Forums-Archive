---
title: "scp does not work"
date: 2009-07-29
forum: General Help
---

### Post by gaston.julia on 2009-07-29
Hi there,

I have got a ubuntu server set up to run simulations. Sometimes I would like to move/copy files around using "scp me@simServer:/path/to/file .". But all that it is doing is the execution of the .bashrc script. I can tell that because .bashrc echos a line to the shell. In that .bashrc I defined a function to switch from one simulation environment to another. If I turn off these functions all works fine.
Help appreciated.

Attached is the .bash_omnet as a text file and is called from .bashrc with:
```

if [ -f ~/.bash_omnet ]; then
    . ~/.bash_omnet
fi

```cheers,
gaston



Both machines are running ubuntu 8.04

---

### Post by DaithiF on 2009-07-29
Hi,
its a fairly long-standing bug in scp that if .bashrc echos anything to stdout then scp breaks.  So the quick fix is to take out any echo's from your .bashrc, or indeed anything called by .bashrc (ie. your .bash_omnet file)

example bug report (though red-hat, i couldn't find an equivalent in ubuntu):
[https://bugzilla.redhat.com/show_bug.cgi?id=20527](https://bugzilla.redhat.com/show_bug.cgi?id=20527)

---

### Post by asmoore82 on 2009-07-29
this is the interesting bit from the rsync manpage:

> The most common cause is incorrectly configured shell  startup  scripts
       (such  as  .cshrc  or .profile) that contain output statements for non-
       interactive logins.

your .bashrc should start out like mine, [COLOR="Red"]that[/COLOR] should fix it:
```
**$ head .bashrc** 
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

[B][COLOR="Red"]# If not running interactively, don't do anything
[ -z "$PS1" ] && return[/COLOR][/B]

# don't put duplicate lines in the history. See bash(1) for more options
export HISTCONTROL=ignoredups
# ... and ignore same sucessive entries.
```

---

### Post by gaston.julia on 2009-07-30
Cheers Guys,

everything worked out well.
But I am not too sure how to mark this thread solved.

Thanks again,
gaston

---

