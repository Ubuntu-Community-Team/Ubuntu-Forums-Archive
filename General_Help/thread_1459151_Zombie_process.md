---
title: "Zombie process"
date: 2010-04-21
forum: General Help
---

### Post by Drenriza on 2010-04-21
Im trying to make a new alias, to quickly find zombie processes.
 
```
alias zombie='ps aux | awk '{print $8 " " $2 }' |grep -wi z
```
 
the output i get
awk: line 2: missing } near end of file. 
 
Anyone who can tell me what it wants? it wants } but why and where.
 
Thanks on advance
Kind regards

---

### Post by didkoslawow on 2010-04-21
Can you try without space between **2** and **}** -> **2}**

---

### Post by sq7bti on 2010-04-21
> **Drenriza said:**
> 
```
alias zombie=[COLOR="Red"]'[/COLOR]ps aux | awk '{print $8 " " $2 }' |grep -wi z
```


Closing apostrophe is missing.

S.

---

### Post by dwarfolo on 2010-04-21
You have missed a ' as sq7bti said.
But it won't work anyway since you haven't escaped some string delimiter.
Try this way

```
alias zombie='ps aux | awk "{print $8 \" \" $2 }" |grep -wi z'
```

---

### Post by Drenriza on 2010-04-21
> **dwarfolo said:**
> You have missed a ' as sq7bti said.
But it won't work anyway since you haven't escaped some string delimiter.
Try this way
 
```
alias zombie='ps aux | awk "{print $8 \" \" $2 }" |grep -wi z'
```
 
did not work, just gets the same error.

---

### Post by Arand on 2010-04-21
Hmm, interestingly tricky, this seems to work though:```
alias zombie="ps aux | awk '{ print \$8 \" \" \$2 }' | grep -w Z"
```This will give a brief list.

Other Useful stuff:```
ps -el | grep Z
```Will show some more info, including parent (PPID) process, which can be used to reap the zombies (Not requiring stopping the PPID to get rid of the PID)```
$ gdb -p $PPID
(gdb) call waitpid($PID, 0, 0)
(gdb) quit
```
$PPID is the parent process ID, $PID is the zombie process ID.

references (although much of the info there is erroneous and/or irrelevant):
[http://serverfault.com/questions/12503/what-is-a-zombie-process-and-how-do-i-kill-it](http://serverfault.com/questions/12503/what-is-a-zombie-process-and-how-do-i-kill-it)
[http://www.cyberciti.biz/tips/killing-zombie-process.html](http://www.cyberciti.biz/tips/killing-zombie-process.html)
[http://adminlinux.blogspot.com/2006/12/zombie-process.html](http://adminlinux.blogspot.com/2006/12/zombie-process.html)


- Arand

---

### Post by Drenriza on 2010-04-22
Thanks Arand. Now i dont get the error message anymore.

Before posting here i searched on google and found the ```
ps -el |grep -i Z
``` command. But i wanted to try more then 1 command to see which one would give me most information. And maybe i could combind them with && dunno.

But since i cant get the #1 command to work. And i havnt been able to find anything with ```
ps - el |grep -w Z
```. I dont know which one to use in the future :)

But with the new changes to

```
alias zombie="ps aux | awk '{ print \$8 \" \" \$2 }' | grep -w Z"
```

i dont get the error message anymore, but i dont get any search results
either. So how do i know if it works?

Thanks on advance

---

### Post by Arand on 2010-04-22
Well, if you get no search results. then likely there are no zombie processes.

[http://en.wikipedia.org/wiki/Talk:Zombie_process](http://en.wikipedia.org/wiki/Talk:Zombie_process) has a guide on how to create zombies in a simple bash script, hence you could test it:[LIST]
[*]Start a blank file```
gedit zombie.bash
```
[*]Paste in the script from wikipedia> #!/bin/sh
time=${1:-60}
sleep 1 &
exec sleep $time
[*]Save and exit the file
[*]Test it```
bash zombie.bash &
ps aux | awk '{ print $8 " " $2 }' | grep -w Z
ps -el | grep -w Z
```
[*]You can tweak the time it stays alive by changing the "60" value in the script, currently it's 60 seconds[/LIST]

Fetch me another brain Igor!


- Arand

---

### Post by Drenriza on 2010-04-23
Thanks Arand :).
 
I will give what you've told me a try. If their should be anything later on i make a new thread.
 
Kind Regards

---

