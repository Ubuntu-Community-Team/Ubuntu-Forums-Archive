---
title: "How do I send a command from tty1 ?"
date: 2009-12-04
forum: General Help
---

### Post by stinkeye on 2009-12-04
If I go to tty1 by pressing ctrl+alt+f1 how do I send the command 
metacity --replace
to run on my normal display at tty7.
thanks.

---

### Post by mo.reina on 2009-12-04
haven't tested it but you can try redirection, though i'm not sure how that works when dealing with X, doesn't it apply automatically?  if you only have one instance of X running, i think typing in metacity --replace will affect that instance of X.  anyway here it is:
```
metacity --replace 0>/dev/tty7
```

to redirect output of programs or commands to another virtual terminal, so i'm assuming it works in the same way:
```
ls 0>/dev/pts/(*enter the number of the terminal here, starting from 0*)
```

---

### Post by WakkiTabakki on 2009-12-04
> **stinkeye said:**
> If I go to tty1 by pressing ctrl+alt+f1 how do I send the command 
metacity --replace
to run on my normal display at tty7.
thanks.

I assume that the scenario for instance is that something's gone wrong with compiz, so you switch to a VT (e.g. tty1) and want to replace it with metacity.
 
To do this you need pass the parameter --display to metacity:
```
metacity -d :0 --replace
```where :0 is the default display name if you only run one X instance (would be the normal case).

/n

---

### Post by stinkeye on 2009-12-04
> **WakkiTabakki said:**
> I assume that the scenario for instance is that something's gone wrong with compiz, so you switch to a VT (e.g. tty1) and want to replace it with metacity.
 
To do this you need pass the parameter --display to metacity:
```
metacity -d :0 --replace
```where :0 is the default display name if you only run one X instance (would be the normal case).

/n
You assume correct.
When I run this I get The error:
no protocol specified
window manager error:unable to open x display :0

I've got no special setup. Just a normal ubuntu install.
Command works on my Gui display when run in terminal.

---

### Post by stinkeye on 2009-12-04
Did a bit of googling and found out I have to add
```
xhost +localhost
```
via the terminal .
Works now.
Thanks for setting me in the right direction.:)

---

