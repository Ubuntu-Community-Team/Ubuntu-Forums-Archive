---
title: "terminal displaying jibrish before file names?"
date: 2012-03-25
forum: General Help
---

### Post by grandkodiak on 2012-03-25
Dunno what happened, but now the terminal is printing jibrish before file names, what happened and how do I fix it?
 
 
 
 
[EMAIL="root@localhost:/"]root@localhost:/[/EMAIL]# ls
ls
&#8592;[0m&#8592;[01;34mbin&#8592;[0m   &#8592;[01;34mdev&#8592;[0m  &#8592;[01;34mhome&#8592;[0m  &#8592;[01;34mlib&#8592;[0m
 &#8592;[01;34mmedia&#8592;[0m  &#8592;[01;34mopt&#8592;[0m   &#8592;[01;34mroot&#8592;[0m  &#8592;[01;34mselinux&#8592;[0m  &#8592;[0
1;34msys&#8592;[0m  &#8592;[01;34musr&#8592;[0m
&#8592;[01;34mboot&#8592;[0m  &#8592;[01;34metc&#8592;[0m  &#8592;[01;36minit&#8592;[0m  &#8592;[01;34mlost+found&#8592;[0m  &#8592;[0
1;34mmnt&#8592;[0m    &#8592;[01;34mproc&#8592;[0m  &#8592;[01;34msbin&#8592;[0m  &#8592;[01;34msrv&#8592;[0m      &#8592;[30;42
mtmp&#8592;[0m  &#8592;[01;34mvar&#8592;[0m
&#8592;[mroot@localhost:/#

---

### Post by Habitual on 2012-03-25
```
echo $PS1
```

output please.

---

