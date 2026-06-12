---
title: "backup using tar... problem"
date: 2010-07-24
forum: General Help
---

### Post by owners4life5 on 2010-07-24
hello

i have a problem when i.m trying to backup using tar.

[see these: (original problem) [http://ubuntuforums.org/showthread.php?t=1506463](http://ubuntuforums.org/showthread.php?t=1506463) (problem solution; see last suggestion) [http://ubuntuforums.org/showthread.php?t=1537041](http://ubuntuforums.org/showthread.php?t=1537041) ]

anyhow, when i try to backup my files, this is what happens.

```
brian@brianlaptop:~$ tar -czvfp /media/backup/backup.tar.gz /home/brian/Desktop (etc...)
```

anyhow, everything goes through, then i get this:

```
gzip: stdout: No space left on device
```

i.m using my formatted iPod, so i know there is enough space to put my files on there???

what am i doing wrong and what should i do?

any help is greatly appreciated...

---

### Post by rubylaser on 2010-07-24
Just so we can see what space you have on your ipod, could you plug it in, then run fdisk -l from a terminal?

---

### Post by DaithiF on 2010-07-24
Hi,
-czvfp file1 file2 will create an archive named p and put file1 and 2 into it
i think you want -czvpf yourarchive file1 file2 etc

---

### Post by owners4life5 on 2010-07-24
> Just so we can see what space you have on your ipod, could you plug it in, then run fdisk -l from a terminal?

i just formatted it... it has about 8 gigs

> Hi,
-czvfp file1 file2 will create an archive named p and put file1 and 2 into it
i think you want -czvpf yourarchive file1 file2 etc

please explain

---

### Post by DaithiF on 2010-07-25
the 'f' parameter tells tar what archive file to create.  the name/location of that file needs to follows the 'f' parameter.  So when you put another option ('p') after the 'f', tar thinks you want to create an archive file called 'p'.  And since this file 'p' does not have any path info. then it is assumed that it should be created in the current directory.

So basically, always put f as the last paramter in the parameter list:
```
tar -cvzpf /media/whatever/ file1 file2 
```

---

