---
title: "Color of text in shell"
date: 2009-10-02
forum: General Help
---

### Post by Turk on 2009-10-02
Hi,

I would like to change the color of the directories (when I input e.g. ´ls´) (which are blue) to an other colour. How can I do that? I searched on multiple sites, but couldn't find that what I wanted.



Thanks!

---

### Post by fluxbuntu on 2009-10-02
Your looking for .bashrc in your home directory. Edit the lines....

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    #alias grep='grep --color=auto'
    #alias fgrep='fgrep --color=auto'
    #alias egrep='egrep --color=auto'

You should be able to change "auto" to whatever color you want. Not sure if it's just "blue" or a hexidecimal color though.

---

### Post by Bachstelze on 2009-10-02
```
dircolors -p > ~/.dircolors
```

Then edit ~/.dircolors accordingly. Ignore the above message.

---

### Post by Turk on 2009-10-02
Thanks, it works!

---

