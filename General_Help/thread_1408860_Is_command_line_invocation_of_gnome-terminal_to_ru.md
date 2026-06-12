---
title: "Is command line invocation of gnome-terminal to run more than one command possible?"
date: 2010-02-16
forum: General Help
---

### Post by narnie on 2010-02-16
Hello,

I am trying to learn how to pass something more than a one-command startup for gnome-terminal.

I will give an example of what I'm trying to do here:
```

#! /bin/bash
#
#TODO write this for gnome and xterm

USAGE="
______________________________________________

${0##*/} [-x] [-g]

run midnight commander in a terminal window

-x    run in xterm (the default)
-g    run in gnome
______________________________________________
"

mcTerm () {
    sleep .5
    mc
    bash
}
export -f mcTerm

if [ "$1" = -h ] ; then echo "$USAGE" ; exit ; fi


if [ $# -lt 1 -o "$1" = -x ]; then
    (
    xterm -maximized -e mcTerm
    ) &
else
    (
    gnome-terminal -x mcTerm
    ) &
fi
```The default option runs xterm withoug any problem.

However, running with the -g option to invoke gnome-terminal, I get a "There was an error creating the child process for this terminal" error.

This same error occurs if the gnome-terminal line is changed to
```

gnome-terminal -e mcTerm

```Is there any way to pass more than one command on to gnome-terminal? I have tried various single and double quoting senarios and in a final attempt, I abstracted to an exported function all to no avail. Perhaps even though gnome-term is better at many things than xterm, xterm trumps it in this instance.

With thanks,
Narnie

---

### Post by kaibob on 2010-02-16
I'm not familar with midnight commander, but you might want to give the following a try:

```
gnome-terminal --execute bash -c "mcTerm"
```

---

### Post by kaibob on 2010-02-17
Post deleted by Kaibob

---

