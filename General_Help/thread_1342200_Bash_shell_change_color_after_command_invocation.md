---
title: "Bash shell: change color after command invocation"
date: 2009-11-30
forum: General Help
---

### Post by Elktro on 2009-11-30
In Bash shell I know that I can change color by defining variable PS1. e.g.
```

PS1="\[\033[01;32m\]\w> \[\033[00m\]"
```

Where \[\033[00m\] changes the color back to the default. What I however want, is to write my command with fancy red and *after* pressing "enter", color should be back to the default. So that I could do this:

```
*(red)* user@my_computer~$ *(still red)* cat my_text.txt
*(default color)* Hello World!
*(red)* user@my_computer~$ 
```

One way to do this would be via a variable that is shown after command invocation. So, is there such environment variable?

Or any other suggestion?

---

### Post by Elktro on 2009-12-01
I have found a solution that at least works. It feel, however, little suspicious as I am using the DEBUG trap.

I put the code below to my [FONT="Courier New"].bashrc[/FONT] file.

```

PS1="\[\033[01;32m\]\w> \[\033[01;31m\]"
export DEFAULTCOLOR="\033[00m"
trap 'echo -en $DEFAULTCOLOR' DEBUG

```

any comments are highly welcomed.

---

