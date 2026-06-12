---
title: "Using gnuplot from a script"
date: 2010-11-14
forum: General Help
---

### Post by ab275 on 2010-11-14
Hi, 

I've been trying to make a bunch of graphs using gnuplot from a bash script. The tricky thing is that I have to divide values from two columns:
```

plot "results.csv" using 1:($4/$6) notitle with lp

```When this command is called from a bash script, the columns get mixed up with script arguments. Does anybody have any idea how to make it read the column values like in the interactive mode?

---

### Post by wt8008 on 2010-11-17
Hello

You need to escape the $ sign since it is interpreted by bash. You can use a \ to escape it. See the example below:
```
wt8008@dockstar:~$ bash test.sh one two three
one two $3
wt8008@dockstar:~$ cat test.sh
echo $1 $2 \$3

```

---

