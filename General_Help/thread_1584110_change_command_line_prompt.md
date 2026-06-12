---
title: "change command line prompt?"
date: 2010-09-28
forum: General Help
---

### Post by owners4life5 on 2010-09-28
can anyone tell me how to change my command line prompt from this:

```
brian@brian-laptop:~$
```

to...well, just something else?

thanks,

---

### Post by VCoolio on 2010-09-28
Read [this](http://ubuntuforums.org/showthread.php?t=614743). The fun takes place in ~/.bashrc with the PS1= and PS2= variables. Here is mine:
```
PROMPT_COMMAND='RET=$?;'
RET_SMILEY='$(if [[ $RET = 0 ]]; then echo -ne "\[\033[01;32m\]:)"; else echo -ne "\[\033[01;31m\]:("; fi;)'
export PS1="\[\033[01;34m\][\w]\n$RET_SMILEY \[\033[01;33m\]\u \[\033[01;32m\]>> \[\033[0m\]"
```

---

### Post by owners4life5 on 2010-09-29
thanks...it went from
```
brian@brian-laptop~$:
```

to this:
```
gimme commands, plz? >
```

haha thanks again..marking as solved (:

---

