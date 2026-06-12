---
title: "Why No Attractive Weather icon Sets?"
date: 2011-04-08
forum: General Help
---

### Post by smithark on 2011-04-08
I am using Cairo Dock on Ubuntu 10.10. I have been googling for a new weather icon set, but couldn’t find any attractive ones like the Yahoo Weather or HTC Weather. There is one for Conky though: ([http://www.omgubuntu.co.uk/2010/10/htc-weather-clock-widget-ubuntu/](http://www.omgubuntu.co.uk/2010/10/htc-weather-clock-widget-ubuntu/)). but, Conky is a bit tough to use:confused:. so, i'll be staying away from Conky. any suggestions?

P.S: It would have been even better if there could be some animations. :)

---

### Post by smithark on 2011-04-11
ok guys. since i didnt receive any replies, i have installed the conky script for HTC like weather icons (the one i mentioned above).
but, now everything is ok except i cant get it to run at startup.
i tried adding a 'startup.sh' file with the following contents:

"#!/bin/bash
sleep 20;
conky &"

and added it to startup applications. but no result:(.

at present i run the following command manually everytime my system boots up:
"conky -c ~/weather+clock/conkyrc"

can anyone advice me on this?

thanks in advance

---

### Post by Chronon on 2011-04-11
Is the script executable?  Also, you want to use the same command you are running manually in the script.  If you just run "conky" with no options it uses ~/.conkyrc by default.

---

### Post by smithark on 2011-04-11
@ Chronon,

yes. the script is executable. can you tell me how to edit the script?
also, when i try to run it using the "conky -c ~/weather+clock/conkyrc" command, i get the following:

[I]smitha@smitha-K50IJ:~$ conky -c ~/weather+clock/conkyrc
Conky: desktop window (16000ad) is subwindow of root window (af)
Conky: window type - override
Conky: drawing to created window (0x4c00001)
Conky: drawing to double buffer
sh: --datatype=HT: not found
sh: --datatype=HT: not found[/I]

is this the problem?

---

