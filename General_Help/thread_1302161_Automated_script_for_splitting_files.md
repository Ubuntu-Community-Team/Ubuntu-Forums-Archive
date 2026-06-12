---
title: "Automated script for splitting files ??"
date: 2009-10-26
forum: General Help
---

### Post by cyanide on 2009-10-26
Hi,

   I do a lot of uploading to Rapidshare and MediaFire, and I was wondering if anyone could help me write an automated script which when invoked in a directory would RAR all the sub folders (into seperate RAR's) and then split each of them into 200 MB parts (or whatever size I require) ??

Any help is appreciated.

Thanks.

---

### Post by mike_tyrell on 2010-02-09
Hello,

first like u im a beginner. Second I dont remember from where I got it but credit goes out to him (whoever he is).

but still needs work. saved as whatever.sh make it executable and thats it. It should take every file and compresses it. -v is the size limit in this case 100MB -p is password in this case 12345 and thats it. I think this is easy enough to add ur own commands just follow the same format.

```
for M in *;
do
  rar a -v100000 -p12345 $M.rar $M


done
```

---

### Post by mike_tyrell on 2010-02-09
by the way I made new additions of my own, after splitting it uploads to my rapidshare account. Im trying to do the same with media fire but there is no script for media fire like rapidshare

---

### Post by chronos00 on 2010-04-19
I know this is not for RS or MF, but you can use this for MU, and perhaps get some guidance for making a RS or MF equivalent script.

[http://forums.digitalpoint.com/showthread.php?t=1642377]("http://forums.digitalpoint.com/showthread.php?t=1642377")

Hope this helps!

PS: If you manage to get a MF script working, please let us know!

---

### Post by mike_tyrell on 2010-04-19
so we have a solution for Rapidshare using there python API (instructions on how to use is very simple from rapidshare website) and this will be a solution for 2shared/megaupload using it with the above rar script to upload files.

its very simple to install and use and implement with the above rar script

[http://ubuntu-blog.com/download-from-rapishare-and-megaupload-by-command-shell-download-manager-ubuntu](http://ubuntu-blog.com/download-from-rapishare-and-megaupload-by-command-shell-download-manager-ubuntu)

hope this helps it sure did help me alot :)

---

