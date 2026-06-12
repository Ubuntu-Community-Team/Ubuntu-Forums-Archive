---
title: "killing connected hosts"
date: 2010-12-01
forum: General Help
---

### Post by zuku on 2010-12-01
Hi,
I need sometimes to kill every connected hosts to my server, so I have connected 40 pts (telnet sessions), now I need to list every tty's PID and then kill it. Is there any command to kill automatically all pts ??

thanks

---

### Post by galvatron408 on 2010-12-01
yes, you can do this...

ps -eaf | grep pts | grep -v grep | awk {'print $2'} | xargs kill

to analyze this line....

ps -eaf will print your processes
pipe via | means send the output to the next command
grep for the word "pts" aka search for "pts"
pipe via |
grep -v grep means don't include the word grep in the search
pipe via |
the awk print $2 means to output only the second field (this is your PID)
pipe via |
finally "xargs kill" will essentially perform a kill on the PID you found

NOTE - I tested this on my ubuntu 10.10 and it doesn't kill my pts unless I force it with a -9... i.e "xargs kill -9"

well, play around with it until you get comfortable. good luck.

---

