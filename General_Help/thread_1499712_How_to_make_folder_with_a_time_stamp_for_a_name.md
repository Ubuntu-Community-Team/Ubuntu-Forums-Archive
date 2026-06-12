---
title: "How to make folder with a time stamp for a name?"
date: 2010-06-02
forum: General Help
---

### Post by e24ohm on 2010-06-02
Folks:
I need to make a few folders, but I need the fold name to reflect the time which they were created. For example: if I create a folder at on 2010.06.03 at 13:01:34 then I would need a file name something similar to the following 20100603_130134. In addition, could the same method be used for .tar files?

I would like a bash script which I can run to perform the following; however, I am not familiar with scripting in Linux yet. Can anyone offer some help? Much appreciated!!!

Thanks,
E

---

### Post by sisco311 on 2010-06-02
```
mkdir $(date +%Y%m%d_%H%M%S)
```
For details see:
```
man bash | less +/"Command Substitution"
```
```
man date
```

[uhelp]community/UsingTheTerminal[/uhelp]
[http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by e24ohm on 2010-06-05
> **sisco311 said:**
> ```
mkdir $(date +%Y%m%d_%H%M%S)
```
For details see:
```
man bash | less +/"Command Substitution"
```
```
man date
```

[uhelp]community/UsingTheTerminal[/uhelp]
[http://linuxcommand.org/](http://linuxcommand.org/)

Thank you. I will try this when I get back to the client's site.

---

