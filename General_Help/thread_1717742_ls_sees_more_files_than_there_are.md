---
title: "ls sees more files than there are"
date: 2011-03-30
forum: General Help
---

### Post by john-the-dodo on 2011-03-30
Hi,

I have a folder that is automatically maintained by Mendeley. Having had some trouble with my account there, I checked on the folder content and found that ls sees a lot more files than there are:

> sudo ls -lai /home/john/mendeley/pdf/
insgesamt 796
(shows 188 files plus . and ..)

The 188 is consistent with what dolphin and other applications show. Using ls without -a, it sees "only" 752, however, there are definitely no hidden files in that folder.

Any ideas what happens here? Using Ubuntu 10.04.2 LTS with KDE.

Cheers,
John

---

### Post by lithopsian on 2011-03-30
You say there are no files starting with a dot.  So compare the lists and see what the differences actually are.  I suspect the answer to your problem will then be very simple.

---

### Post by supershin on 2011-03-30
.filename is a hidden file. Hidden files are preceded by a full-stop.

you could run 

ls -a > lsaout.txt
ls > lsout.txt
diff lsaout.txt lsout.txt

you'll see the difference.

---

### Post by john-the-dodo on 2011-03-30
> ls -a > lsaout.txt
> ls > lsout.txt
> diff lsaout.txt lsout.txt
1,2d0
< .
< ..
123a122
> lsout.txt

as I said, there are no hidden files (I'm not a TOTAL beginner ;-))

just to clarify: there are 188 folders without a preceding dot, and none with a dot (invisible) other than the usual . and ..

---

### Post by supershin on 2011-03-30
> however, there are definitely no hidden files in that folder. There are 188 folders without a preceding dot

What about inside the other 188 folders?

Try running 
sdiff lsaout.txt lsout.txt

---

### Post by Vaphell on 2011-03-30
ls counts hardlinks
for a directory it's including parent and all subdirectories
notice how in ls -la 2nd column shows 1 for files and greater numbers for dirs
. and .. add a lot (their subdirs and respective parents)

---

### Post by john-the-dodo on 2011-03-30
thanks, though I think thats not it. filelight shows 686 files with an average of 0.2 MB (138 MB total) for that folder. first I thought that maybe filelight uses ls and interprets wrong, but this phenomenon only occurs for that particular folder, neither its parents nor its children or any other folder.

---

### Post by Vaphell on 2011-03-30
i was wrong, total counts blocks
[http://www.redhat.com/archives/rhl-list/2006-November/msg01207.html](http://www.redhat.com/archives/rhl-list/2006-November/msg01207.html)
[http://www.unix.com/unix-advanced-expert-users/36758-total-ls-l-command.html](http://www.unix.com/unix-advanced-expert-users/36758-total-ls-l-command.html)

try
```
ls -lsh
ls -lash
```

---

