---
title: "fdisk -l in order, grep whole line..."
date: 2010-05-02
forum: General Help
---

### Post by J V on 2010-05-02
How can I make "fdisk -l" return values in order on disk?

The /dev locations are always screwed up...

Also, I noticed when doing "ps aux | grep fire" that it stops displaying output right after the match, I want it to display the whole line, how to?

---

### Post by srs5694 on 2010-05-02
I don't believe there's a way to do what you want with fdisk alone. There is an fdisk command ('f' on the experts' menu) that sorts partitions so that they're in disk order; however, this is limited by the restrictions imposed by the primary/logical/extended distinction -- if there are primary partitions after your extended partition, those late primary partitions will be out of order. You might also use pipes through grep and sort to do the job, although I'm not sure sort offers precisely the options you'd need, so you might need to add some more tools to get the job done.

As to your grep issue, I've never seen that problem. Could you post an example output to illustrate, just to avoid the possibility of misinterpretation?

---

### Post by J V on 2010-05-02
I can't be bothered writing a python app to sort the fdisk properly...

My grep issue:```
j@jubuntu:~$ ps aux | grep fire
j        22324  0.0  0.0   7616   916 pts/3    S+   00:57   0:00 grep --color=auto fire
j@jubuntu:~$ ps aux | grep firefox
j        22326  0.0  0.0   7616   916 pts/3    S+   00:57   0:00 grep --color=auto firefox
```I know they are different PIDs, but the firefox PIDs tend to jump around (And I can't spot the "Fire" process on ps aux alone, part of the pipe?), perhaps this is a problem with something else, as grep does find the entire line for other processes...

---

### Post by srs5694 on 2010-05-02
Both of those outputs are finding the grep command itself, which is normal. If you've got another process running that should match "fire" (such as a firefox process), then something is wrong; however, it looks to me that you simply don't have any matching processes. Here it is on my system (which is running Gentoo, not Ubuntu):

```

$ ps aux | grep fire
root      9330  0.0  0.0      0     0 ?        S    Mar23   0:00 [firegl]
rodsmith 19390  0.0  0.0   6112   736 pts/16   S+   19:11   0:00 grep --colour=auto fire
rodsmith 24107  1.2 28.6 2932412 1089964 ?     Sl   Apr23 164:41 firefox
$ ps aux | grep firefox
rodsmith 19392  0.0  0.0   6108   632 pts/16   S+   19:11   0:00 grep --colour=auto firefox
rodsmith 24107  1.2 28.6 2932412 1087992 ?     Sl   Apr23 164:42 firefox

```

Both of these outputs caught the grep line, both caught a single firefox instance, and the search for "fire" also caught something called firegl. Try grepping "init" rather than "fire"; every Linux system should have a process called init (and there may be others that'll match, too).

---

### Post by J V on 2010-05-03
Oh man I feel so stupid, of course thats the grep command xD

Why does it show up all the --color=auto stuff?

---

### Post by ibuclaw on 2010-05-03
In ~/.bashrc, grep is an alias to 'grep --color=auto', just like ls is an alias to 'ls --colour=auto'.

Psst, as for the extraneous output, this is why I prefer to use:
```
ps -el | grep firefox
```
Instead.

But this has the caveat that it only shows the process name, not the command used to call it.

Regards
Iain

---

### Post by J V on 2010-05-03
Thanks :)

---

