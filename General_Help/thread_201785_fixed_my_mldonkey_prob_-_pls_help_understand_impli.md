---
title: "fixed my mldonkey prob - pls help understand implications"
date: 2006-06-22
forum: General Help
---

### Post by glenndavy on 2006-06-22
I've had a problem when starting mldonkey-server - it reports an error that says something along the lines of " mlnetinstall -- f bla bla" (sorry not in postition to give exact message at mo.

I found if I remarked out line 82 like so of /etc/init.d/mldonkey-server start:
    #install -o mldonkey -g mldoney -m 755 -f $PIDFILE 

it all works v-well - I guess it stops the pid file being written - can any one tell me if this will give me any grief?

thx
Glenn

---

### Post by uteck on 2006-06-22
When you installed mldonkey did you tell it to start when the system is booted?  It seems that way since you modified the init.d file.  If you want to always run when you boot then it will not anymore, but otherwise it should not affect anything.

---

### Post by MacMan on 2006-06-22
[QUOTE=glenndavy]
I found if I remarked out line 82 like so of /etc/init.d/mldonkey-server start:
    #install -o mldonkey -g mldoney -m 755 -f $PIDFILE 
[/QUOTE]

I have a better solution for you. Uncomment that line and change it so that it reads:
```

install -o mldonkey -g mldonkey -m 755 -d $(dirname $PIDFILE)

```

This way the script will write the pidfile correctly.

I've had the same problem a few days ago, and I found the solution on this forum. You should have looked harder for it! ;-)

I hope this helps.

Ciao.
-- 
MacMan

---

