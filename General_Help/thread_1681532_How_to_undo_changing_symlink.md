---
title: "How to undo changing symlink?"
date: 2011-02-04
forum: General Help
---

### Post by user68 on 2011-02-04
Can anyone please tell me how to undo this? 

*"Simply change the symlink so that it points to /bin/bash.  To do this, open a terminal, and type the following:*
  [I][COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**rm**[/COLOR] [COLOR=#660033]-f[/COLOR] [COLOR=#000000]**/**[/COLOR]bin[COLOR=#000000]**/**[/COLOR][COLOR=#C20CB9]**sh**[/COLOR]
[COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**ln**[/COLOR] [COLOR=#660033]-s[/COLOR] [COLOR=#000000]**/**[/COLOR]bin[COLOR=#000000]**/**[/COLOR][COLOR=#C20CB9]**bash**[/COLOR] [COLOR=#000000]**/**[/COLOR]bin[COLOR=#000000]**/**[/COLOR][COLOR=#C20CB9]**sh**[/COLOR][/I]

  *From now on your scripts should work as their authors expected."*


I followed this when I shouldn't have done and now have got problems...

---

### Post by Vaphell on 2011-02-04
sh is a symlink do dash
```
lrwxrwxrwx 1 root root 4 2010-06-14 06:06 /bin/sh -> dash

```
so create a symlink again, but with dash instead of bash

either way playing with that to fix some script problems doesn't make much sense.
if you want to explicitly define a flavor of shell to run the script with put it in the very first line of the script, e.g.
```
#!/bin/bash
```
it tells the system to use exactly that program when you run executable script
```
/path/to/script/script.sh
```

of course you can override that default by passing the script file as a parameter to the shell of choice
eg
```
**sh** /path/to/script/script.sh
```

---

### Post by user68 on 2011-02-04
Thanks Vaphell !

---

