---
title: "Background Jobs die when I log out of ssh"
date: 2010-08-18
forum: General Help
---

### Post by Lyuokdea on 2010-08-18
Hi All,

I'm trying to remotely work on an ubuntu server that I've set up. I have some bash scripts which i would like to run in the background. The bash scripts look like:

#!/bin/bash
./run1.pl
./run2.pl
./run3.pl

And they run a bunch of smaller simulation scripts. If the bash file is named runall.sh, I've been trying to run the command (remotely) with:

./runall.sh &

However, when I log out of the remote session, this appears to kill all of my scripts. Shouldn't they be ok because they are already in the background? I am logging on from an OS X Snow Leopard machine, if this makes a difference.

I have a temporary workaround, which is to write a script called runallall.sh which looks like:

#!/bin/bash
./runall.sh &

And which seems to get runall.sh to decouple from my remote session - but this is not a great option. Is there a better way to do this?

Thanks!

~Lyuokdea

---

### Post by surfer on 2010-08-18
use [screen]("http://www.gnu.org/software/screen/").

this lets you reconnect to a lost session.

---

### Post by Vaphell on 2010-08-18
nohup is your answer
[http://www.cyberciti.biz/tips/nohup-execute-commands-after-you-exit-from-a-shell-prompt.html](http://www.cyberciti.biz/tips/nohup-execute-commands-after-you-exit-from-a-shell-prompt.html)

---

### Post by bilkay on 2010-08-23
$ at now
>yourscript
>^D
$ exit

---

### Post by Zorgoth on 2010-08-23
I think that you have to run "disown" after you start the process with an & sometimes.  Also I second the recommendation of screen.  I use it every day at work and it has never failed me once.

---

### Post by silverglade00 on 2010-08-23
> I have a temporary workaround, which is to write a script called runallall.sh which looks like:

#!/bin/bash
./runall.sh &

This would seem to imply that you need to change runall.sh to 

```

#!/bin/bash
./run1.pl &
./run2.pl &
./run3.pl &

```

---

