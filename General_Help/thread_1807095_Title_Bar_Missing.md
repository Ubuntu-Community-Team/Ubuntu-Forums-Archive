---
title: "Title Bar Missing"
date: 2011-07-18
forum: General Help
---

### Post by MikeyDL on 2011-07-18
Had my xubuntu logon blow up on me for some reason.  I don't have any title bars and the mouse often has an X instead of the usual pointer.  What settings folder do I need to delete to get my logon back to normal?

I created a new test logon and everything is fine for the new logon.

---

### Post by pqwoerituytrueiwoq on 2011-07-18
which version?
What gpu

---

### Post by MikeyDL on 2011-07-18
It's xubuntu 11.04 with an Acer Aspires One netbook so probably an Intel built in graphics.  I would just recreate and live with a new logon except for resetting up Dropbox.  Takes forever to redownload files.

---

### Post by pqwoerituytrueiwoq on 2011-07-18
why not just move the files to the other account
unless you encrypted the account it is really simple

---

### Post by Toz on 2011-07-18
Most probably, the window manager (xwfm4) has crashed. 
Alt+F2 then run ```
xfwm4 --display:0.0 --replace
```

---

### Post by MikeyDL on 2011-07-19
> **Toz said:**
> Most probably, the window manager (xwfm4) has crashed. 
Alt+F2 then run ```
xfwm4 --display:0.0 --replace
```

THANKS! That did the trick.  

Although the --display:0.0 option for xfwm4 seems to be formatted differently (looks like display=).  I ended up running

```
xfwm4 --replace
```

That gave me an error message but after closing out terminal the title bars were back.

---

### Post by Toz on 2011-07-19
My bad - I forgot the =. It should be:
```
xfwm4 --display=:0.0 --replace
```

The other version works as well, though it seems to generate some extra errors (as seen in ~/.xsession-errors)

---

