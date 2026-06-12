---
title: "need bash script syntax help"
date: 2011-07-23
forum: General Help
---

### Post by strider3700 on 2011-07-23
<edit>never mind dump the ;'s and it all works fine</edit>  

I'm trying to write a bash script that will check if XMBC is running if it is then do nothing else start it then do some other things.

This is the start
```
#!/bin/bash

DISPLAY=:0.0
WINCLASS=xbmc.bin.xbmc.bin
STATUS=0
#check if xmbc is already running if so do nothing else start it
if ps -ef|grep -v grep|grep -i /usr/bin/xbmc;
then echo "already running";
else /usr/bin/xbmc "$@" &; 
fi

```

as it currently stands I get 
> ./xbmc-launch.sh: line 10: syntax error near unexpected token `;'
./xbmc-launch.sh: line 10: `else /usr/bin/xbmc "$@" &; '

If I drop the & it works but doesn't background xbmc like I need.  If I drop the if statement and just try to fire xbmc with the & it works.

Can anyone tell me what I need to do to add the & or some other way to start the program backgrounded in the if statement?

Thanks

---

### Post by Bonster on 2011-07-24
Try this

edit:

> if pidof -x xbmc; then exit; else xbmc; fi

add other stuff if u want

---

### Post by CaptainMark on 2011-07-24
replace 
```
if ps -ef|grep -v grep|grep -i /usr/bin/xbmc;
 then echo "already running";
 else /usr/bin/xbmc "$@" &;  fi
```with 
```
if ps -ef |grep xbmc ;
then
    echo "already running"
else
    /usr/bin/xbmc  &
fi
```i believe its the "$@" causing the problem, bash maybe thinks its supposed to be looking for a variable named @, try removing it  (im a bit rusty but maybe)

---

