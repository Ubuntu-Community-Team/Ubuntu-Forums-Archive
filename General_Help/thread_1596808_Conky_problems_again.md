---
title: "Conky problems again"
date: 2010-10-14
forum: General Help
---

### Post by mr-woof on 2010-10-14
hi all,

I've been running 10.04 for a couple of months and right from the start, conky wouldn't start automatically. It would run if you did a alt-f2 and used the conky command. 

So after reading that other people where having the same problems and had sorted it out with a start up script. So:

#!/bin/bash
sleep 60 && conky;

Nothing complex, it's been working fine. Within the last day or so I completed the last set of updated, reboot, no conky. It won't run now either with alt-f2 :confused:

Anyone got any ideas?

---

### Post by Toz on 2010-10-14
Open up a terminal window, type in 'conky' and press enter. Reply back with the output from the command.

Also, post the contents of your .conkyrc file (assuming your using the default config file).

/ToZ

---

