---
title: "Partition Problem &quot;Bizare permission ?--------x &quot;"
date: 2009-07-08
forum: General Help
---

### Post by tigga on 2009-07-08
Hello every body

the problem is , after sudden outage my work directory don't open and when i do an ls -l this is the output:

```

work:/data# ls -l
total 8650788
?--------x 206 1836449998 1635188738 33619980 jan 25  1971 WORK
drwxrwxrwx   1 root       root             37 jui  3 16:09 music
drwx------   2 root       root          16384 jun 19 01:14 lost+found

```

I appreciate any help.
Thanx

---

### Post by moster on 2009-07-08
You go there in terminal and type 
```
sudo chmod a=rwx -R WORK
```

it means allow all to ReadWriteExecute, apply that to subdirectories too.

---

