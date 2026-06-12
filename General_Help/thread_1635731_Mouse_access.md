---
title: "Mouse access"
date: 2010-12-02
forum: General Help
---

### Post by ZeeMythical on 2010-12-02
Hey there !!

Ive been struggling with this the whole day :( so thought i might as well ask for a bit of help

I was wondering if anyone can tell me how to access my mouse. Apparently it sends the delta x and delta y values to the computer. I have tried 
/dev/input/mouse
but the data didnt make sense at all.
after snooping around a bit i saw one could convert the data using xxd
xxd /dev/input/mouse
this did look a bit better but still does not make any sense :( 
is there a way to get say integer values instead of 1's and 0's, perhaps using C++ even or some other CLI command?


I also looked at mouse package formats. Seems complicated to get the actual value from the given packet. Any help would be appreciated :) 

Thnaks in advance :p

---

