---
title: "can i call commands via terminal's history?"
date: 2009-09-22
forum: General Help
---

### Post by chriskin on 2009-09-22
terminal has a history - what i would like would be to write the number of the command at the history and run it that way, is that possible?

---

### Post by hambone79 on 2009-09-22
It is possible with a little Bash magic. Just open up your .bashrc file with a text editor and add alias commands like these:
```

alias 1='command you want to run when 1 is typed'
alias 989='command you want to run when 989 is typed'

```

Just save the .bashrc file and you should be good to go (I can't remember...you may have to log out and log back in for the file to be reloaded).

---

### Post by chriskin on 2009-09-22
> **hambone79 said:**
> It is possible with a little Bash magic. Just open up your .bashrc file with a text editor and add alias commands like these:
```

alias 1='command you want to run when 1 is typed'
alias 989='command you want to run when 989 is typed'

```

Just save the .bashrc file and you should be good to go (I can't remember...you may have to log out and log back in for the file to be reloaded).

i would prefer it to be via the history but this one seems ok , thanks :)

---

### Post by DaithiF on 2009-09-22
```
history

```
lists your previous commands with a number for each
if the command you want to re-run was number 500 in the list for example, then to re-run that command do:
```
!500
```

---

### Post by kaibob on 2009-09-22
> **chriskin said:**
> terminal has a history - what i would like would be to write the number of the command at the history and run it that way, is that possible?

You can rerun any command shown in the history by entering a ! followed by the number of the command. For example,

```
!499
```

[http://ubuntuforums.org/showthread.php?t=1239246&highlight=.bash_history](http://ubuntuforums.org/showthread.php?t=1239246&highlight=.bash_history)

---

### Post by chriskin on 2009-09-22
thank you :)

---

### Post by VCoolio on 2009-09-22
you can also press ctrl+r, start typing your command and as soon as it autocompletes press <enter>

---

### Post by chriskin on 2009-09-22
> **VCoolio said:**
> you can also press ctrl+r, start typing your command and as soon as it autocompletes press <enter>

that's even better, perfect to be honest
thanks again :) 
:popcorn:

---

