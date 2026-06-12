---
title: "Command line prefix like in Fedora ( [root@fedora ~]# ) - .bashrc ?"
date: 2010-01-30
forum: General Help
---

### Post by The Men on 2010-01-30
```
[user@ubuntu ~]# <command>
```

What exactly I need to change in my .bashrc file to turn the default Ubuntu command line prefix into Fedora-style one ?

---

### Post by Johnny B on 2010-01-30
the command prompt is set by the $PS1 varible

[http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html]("http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html")

---

### Post by The Men on 2010-01-30
I know, I just can't figure out how to achieve the Fedora-style prompt. I've tried a couple of variations ( from a few tutorials ) but none worked.

---

### Post by rnerwein on 2010-01-30
hi
 do you want some thing like this (include the time too).
 PS1=""
     if [ "`id -u`" -eq 0 ]
     then
        PS1="("["\[\033[01;31m\]\u\[\033[00m\]@\h:\w \A"]")->\s "   # user name is shown in [COLOR=Red]red[/COLOR]
     else
         PS1="("["\[\033[01;32m\]\u\[\033[00m\]@\h:\w \A"]")->\s "  # user name is shown in [COLOR=Lime]green[/COLOR]
     fi
 export PS1

 this results in:
 ([[COLOR=Lime]richi[/COLOR]@tschang:~ 10:29])->bash
  
 may be the colours be good for standard bash in ubuntu too  (i use it in other destros too because i've always open a terminal running root account)

for bash build ins see: man bash | less +3/"PROMPTING"

---

