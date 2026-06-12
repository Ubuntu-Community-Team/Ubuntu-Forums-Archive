---
title: "manually run 'sudo dpkg --configure -a'"
date: 2012-03-14
forum: General Help
---

### Post by midhul on 2012-03-14
hii please help me  when i try to run commands am end up with this message E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. " am new to ubuntu .please help me how to solve this

---

### Post by nothingspecial on 2012-03-14
Open a terminal Ctrl-Alt-T

and type

```
sudo dpkg --configure -a
```

---

### Post by raja.genupula on 2012-03-14
yeah open your terminal and type as **sudo dpkg --configure -a**. It will ask your password and type it . then press enter .

---

### Post by 0011235813 on 2012-03-14
When I read that, I understood that I had to type in the command. When it gives you an error like that, you have to run the command it tells you to, in this case type in the terminal (Ctr+Alt+T) :
```
sudo dpkg --configure -a 
```
It will ask you for your password, in which case you type it in (it won't show up by the way) .
Note: This error was caused because you tried to install a package and then you suddenly aborted it.

Please click "thread tools" at the top right hand corner of the thread and click "mark as solved" after this. Thanks.

---

### Post by midhul on 2012-03-14
:lolflag: thanks guys ...you rocksss

---

