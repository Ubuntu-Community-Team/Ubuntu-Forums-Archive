---
title: "Set environment variables"
date: 2011-07-08
forum: General Help
---

### Post by Mappenz on 2011-07-08
Hi,

i would like to set a path variable. I found a few pretty straight forward looking instructions. Those didn't work for me, probably because i don't understand how Linux paths work. 

I want the pathvariable point to ```
~/glassfish3/bin
```

also:

```
michael@michi:~/glassfish3/bin$ echo $SHELL
/bin/bash

```

---

### Post by Mappenz on 2011-07-08
I figured it out. Sorry about postin prematurely. Found the solution here: [http://linuxwiki.de/UmgebungsVariable](http://linuxwiki.de/UmgebungsVariable)

I was confused the previous instructions using HOME in the path.

Making it permanent by writing ```
[B]
PATH=$PATH:/home/michael/glassfish3/glassfish/bin/
export PATH[/B]
```

in .profile doesn't work for me.

---

