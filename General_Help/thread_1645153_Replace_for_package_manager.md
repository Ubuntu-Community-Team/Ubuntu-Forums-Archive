---
title: "Replace for package manager"
date: 2010-12-14
forum: General Help
---

### Post by same.500 on 2010-12-14
Hi;
My problem is whit the package managers all of it is not responding (update,GDebi,synaptic), it bater if any one know application replacing them because i'm always having problem whit them and this picture could help ;

---

### Post by surfer on 2010-12-14
what exactly does not work?

can you update from the command line? try:
```
$ sudo apt-get update
$ sudo apt-get upgrade
```
...and post the output if anything goes wrong.

---

### Post by same.500 on 2010-12-14
Thanks! but i'm still having problem whit synaptic package manager it's not responding when trying to build dependency tree this application make aloots of problems to me i'm fixing it during the last three days from adeferent problems when i fix one another one happens  and this not making me enjoying whit ubuntu .

---

### Post by tajiknomi on 2010-12-14
[SIZE=2]What version of Ubuntu are you using...??

Try these Commands in terminal:-

[/SIZE]```
[SIZE=3]sudo dpkg --configure -a[/SIZE]
```

```
[SIZE=3]sudo apt-get install -f[/SIZE]
```

```
[SIZE=3]sudo apt-get clean[/SIZE]
```

[SIZE=2]at last :-[/SIZE]

```
[SIZE=3]sudo apt-get update[/SIZE]
```

[SIZE=2]Any Difference..??[/SIZE]

---

### Post by same.500 on 2010-12-14
Thanks all guys.
I did not do any thing it just works by it's self.:confused:

---

### Post by tajiknomi on 2010-12-15
> **same.500 said:**
> Thanks all guys.
I did not do any thing it just works by it's self.:confused:

[SIZE=2]Glad to see you problem is solved, please mark the ***thread-as-Solved*** in ***thread-tools*** Above...[/SIZE]

---

