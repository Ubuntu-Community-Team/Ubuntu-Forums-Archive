---
title: "missed variable..."
date: 2010-12-13
forum: General Help
---

### Post by ter-pierre on 2010-12-13
Hello guys!

I have an MSExchange tracking log.
This is a text file coma separated, where trhe first 6 lines as the file header.
I need to know the somatory size of the messages.
In this log file I have on the 14 field the message size.
So... I need just totalize the 14 field of each line.
I write the follow script:

#!/bin/bash
B=0
tail -n +6 MSGTRK20101201-1.LOG | cut -d "," -f14 |while read A
        do
        if [ "$A" -gt "0" ] 2> /dev/null
        then
                B=$(($B+$A))
        fi
        done
echo $B "END"
I'm using Ubuntu 10.10 and the result of that script is " 0 END".

Whats happen? What I'm doing wrong?

TKS

---

