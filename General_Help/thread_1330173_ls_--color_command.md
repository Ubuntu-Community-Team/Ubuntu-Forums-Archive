---
title: "ls --color command"
date: 2009-11-18
forum: General Help
---

### Post by Philip Gray on 2009-11-18
Hi how do I permanently switch off the colour display in the ls command? I used ls --color=none which gave me the desired display without colour coding. However when I send off ls again the colour coding is back. I ask via google how to switch this off. Some posts on the next advised that I copy /etc/DIR_COLOR to my home folder as .dir_color and
change the COLOR parameter to read COLOR=none. I went to the /etc folder but there is no DIR_COLOR file. I did a search for it but this file is nowhere to be found in ubuntu 9.04. What do I do to solve this?

Regards
Philip

---

### Post by t0p on 2009-11-18
You need to edit the alias settings in the .bashrc file in your home directory.  Here's the relevant lines:

```
# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ] && [ -x /usr/bin/dircolors ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'

```

I *think* you need to delete these lines.  But I'm not 100% sure that'll be okay.  So back it up first:

```
cp .bashrc bashrc.bak
```

then edit .bashrc.  Log out and in again.  If it doesn't work properly, you can always restore the original .bashrc.

---

### Post by Philip Gray on 2009-11-18
Hi tOp thanks for yr help.

Regards
Philip

---

### Post by SeanHodges on 2009-11-18
Another way is to create a file in your home directory called ".bash_aliases", and add the following line to it:

```
alias ls='ls --color=none'
```

Save it and restart your terminal.

This way you keep your alias customisations in a separate file, which will be easier when finding your changes later on.

---

