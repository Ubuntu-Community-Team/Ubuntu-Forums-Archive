---
title: "Help with scripting"
date: 2009-10-30
forum: General Help
---

### Post by blazemore on 2009-10-30
I'd like a script which I can put on the desktop, which will run in a terminal on double-click.

I'd like it to perform commands, but suppress the output, like this:

> 
Installing Chinese Language Support...     [Done]
Installing DVD Playback Support...         [Done]
Installing MARS...                         [Done]

And so on

Is this possible?

---

### Post by Lars Noodén on 2009-10-30
Redirect standard output using **>**
Redirect standard error using **2>&1** after redirecting stdout.

See the section for '[REDIRECTION](http://manpages.ubuntu.com/manpages/karmic/en/man1/bash.1.html)' in the bash manual.

Many programs have an option to reduce output, usually something like --no-verbose or --quiet.  Use those also.  

If there are errors, you will need the output either to know of the error or to fix the error.

---

### Post by blazemore on 2009-10-30
My main isue is having it come up properly on double click. It neds to be completely idiotpof.

ugh keyboard battery

---

### Post by Lars Noodén on 2009-10-30
> **blazemore said:**
> My main isue is having it come up properly on double click. It neds to be completely idiotpof.

ugh keyboard battery

That not a matter of scripting but of the desktop environment.  KDE 3.5 was much better than KDE 4 for that kind of thing.  With KDE4, the script can be added to the menu by editing the menu, then after that, it can be added to the desktop or the panel.  It is there you can set up the redirects, if desired.

KDE 3.x used to have the option to run the program in a terminal session.  That and a great many other options are missing in 4.  You'll find a lot missing from konsole, too.  

Make sure that the script works, first, by running it in the terminal.  Then when it completes, it should exit with a value of 0.  

```

touch script.sh
chmod +x script.sh

```

Then

```

#!/bin/bash

# the usual
echo "Hello, World"

# wait for a key press
read -n 1 -s X;
echo "X was \"$X\"";

# tell the OS that everything is OK
exit 0;


```

---

