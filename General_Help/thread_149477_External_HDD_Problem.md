---
title: "External HDD Problem"
date: 2006-03-24
forum: General Help
---

### Post by MasterC on 2006-03-24
I recently had to backup my Windows install (running a dual boot), so I copied all the files I wanted into a folder in my Ubuntu install. So then, after Windows was reinstalled, I copied the backup folder to my external HDD, booted into windows, and now the folder is not on my drive. It shows that I lost space, but the folder is not there. I then booted back into Ubuntu, and it still wasn't there. What gives? Is there a way I can reclaim the lost space?

Thanks for you help in advance! ;)

---

### Post by bionnaki on 2006-03-24
is the folder possibly hidden? cd into the directory and ls -l -a (or just control-h in nautilus).

---

### Post by MasterC on 2006-03-24
Control-H didn't show anything, but ls -l -a gave me this:

```

chris@ubuntu:/media/STORAGE$ ls -l -a
total 164
drwx------   6 chris chris 32768 1969-12-31 16:00 .
drwxr-xr-x   6 root  root   4096 2006-03-23 21:22 ..
drwx------   6 chris chris 32768 2006-03-12 19:31 Downloads
drwx------   2 chris chris 32768 2006-03-12 19:20 Recycled
drwx------   3 chris chris 32768 2006-03-12 19:20 System Volume Information
drwx------  14 chris chris 32768 2006-03-12 19:23 Videos

```

The last four folders I can see, but what are the first two? :-k

---

### Post by trent dillman on 2006-03-24
Ignore the first two....

. is the current directory
.. is the parent directory

---

### Post by MasterC on 2006-03-24
Hmm... didn't know that! Thanks for helping me with that part!

---

### Post by trent dillman on 2006-03-24
no problem

there's a switch for ls that will hide those...

try 
```
ls -laA
```

instead of 
```
ls -l -a
```

note you can combine switches with the ls command as well

---

