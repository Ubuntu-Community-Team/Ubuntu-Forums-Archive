---
title: "This makes no sense"
date: 2010-12-07
forum: General Help
---

### Post by Rocket J Squirrel on 2010-12-07
Update Manager froze during an update. Synaptic suggested I run 

sudo dpkg -configure -a

See the screenshot for the result. It makes no sense.

A little help?

---

### Post by pastalavista on 2010-12-07
Try it like this ```
sudo dpkg --configure -a
``` and for future reference
```
man dpkg
```

---

### Post by Rocket J Squirrel on 2010-12-08
Oops. If I had studied Package Manager's suggested command I'd have seen the double hyphens. If there wasn't some kind of bug preventing me from pasting anything into Terminal I'd have just done a copy and paste. And if I could have seen any way that dpkg could have read the -a as a -o I'd have done some more tinkering. As it was, it looked like dpkg didn't know that an "a" was not the same as an "o." I guess it was the "o" in "-configure" that dpkg was puzzled by. 

And yeah -- even a cursory glance an the man page would have made the "--" more visible. 

Thanks for the help.

---

