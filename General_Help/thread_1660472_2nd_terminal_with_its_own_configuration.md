---
title: "2nd terminal with its own configuration"
date: 2011-01-05
forum: General Help
---

### Post by tawalaya on 2011-01-05
Hi,

I am currently trying to write a small script that is supposed to help me to create a development environment for Opal (don't ask why ~.~ i would like to know my self) anyway, it is all good so far. I did a search for the problem I currently have with that and did not find anything fitting, that is why i did open a new post...

The plan is to run some commands that first backup my old version of the code as a local "save" Copy, then grabbing the newest version from the svn server. At the end, I set some Environment vars like PATH and finally to get my terminal on the screen I do something like this:

```

gnome-terminal -t "Opal Projekt" --working-directory=$curr/src --profile=OPAL --hide-menubar --maximize

```

Like I said, so far all that works fine for me, but now I wrote some scripts beside the backup script that i wont to use within the terminal by JUST typing something like build or clean ...

My idea was to use  alias  for that, a now the problem. I do not get alias to work, I am not sure why. I basically did the same thing as in .bash_aliases but they just aren't there.

here a little more from the script:

```

#!/bin/sh
#
# backup and other stuff...
#

#script with aliases in it
bin/aliases

gnome-terminal -t "Opal Projekt" --working-directory=$curr/src --profile=OPAL --hide-menubar --maximize

```

bin/aliases:
```

#!/bin/sh
alias backup='../bin/backup'
alias build='../bin/build'
alias clean='../bin/clean'

```

---

### Post by Brandon Williams on 2011-01-05
Your aliases will only be present in the script that executes gnome-terminal, not in the shell running within gnome-terminal. There is no way to export aliases from one shell process into another. Instead, I suggest that you export a variable, e.g. 'export OPAL_CONTEXT=true', and then add code to your .bashrc to load your special OPAL aliases file if OPAL_CONTEXT is "true".

---

### Post by tawalaya on 2011-01-05
Big Thanks it is working perfectly now, not as protable as i hoped but what works works ;) ;)

Thanks =D>

---

