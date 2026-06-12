---
title: "Copy files/folders with GREP"
date: 2011-07-01
forum: General Help
---

### Post by hlygrail on 2011-07-01
I'm attempting to find a particular word wherever it appears within a massive directory listing of teeny tiny text files -- and then copy all files containing this word into a "staging" directory.

Whenever I use the command below (on a test folder of smaller scale), it never carries the directory structure but attempts to copy all files within the "output" folder.
```
cp `grep -ir 'word' *` output
```


Any help on how to copy all these text files and have them retain some sort of directory structure?


Thanks,
Chris

---

### Post by prodigy_ on 2011-07-01
Try something along the lines of this (from the folder you want to copy):

```
grep -lZir 'word' . | cpio --null -pvd /path/to/target-dir
```

P.S. BTW, depending on file contents **grep** might give unexpected results. E.g. **grep 'rain'** matches "grain".

---

### Post by hlygrail on 2011-07-01
Thank you.  That did the trick.

First time I ran it, it behaved a little weird, but that's because I had the output folder in the same directory.  Once I changed that, it brought a tear to my eye how nicely it ran.

Thanks again!

---

### Post by tomerof on 2012-10-29
Hi, 
it's seems to work but i got problem, files name too long.
any other idea?

The command:
```


grep -lzir "tmy.bezeq.co.il" /home/tomer/Desktop/WTLogs/logsdcint01/* | cpio --null -pvd /home/tomer/Desktop/tmy.bezeq


```The results:
```


/home/tomer/Desktop/WTLogs/logsdcint01/dcstli8cu1000043dvoxfytg4_9l3x-dcs-2012-10-25-09-00051-vm-sdcint-01.log
: Cannot stat: File name too long
0 blocks



```

---

### Post by overdrank on 2012-10-29
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

