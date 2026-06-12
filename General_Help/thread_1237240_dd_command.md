---
title: "dd command"
date: 2009-08-11
forum: General Help
---

### Post by ub007 on 2009-08-11
while [ $i -ne 31500 ] do dd if=/dev/random of=my_dir/$RANDOM.bin bs=65536 count=800; i=`expr $i +1`; done

This creates 50 MB files in my_dir.I was wondering how it creates files of that size --> 51,200 KB. the bs states 65536 which is 65536/1024 == 64bytes.

mayb I'm stupid enough to miss something quite obvious here,but kinda annoying cz I cant seem to figure it out at the moment.

Cheers
david

---

### Post by nikhilk on 2009-08-11
> **ub007 said:**
> while [ $i -ne 31500 ] do dd if=/dev/random of=my_dir/$RANDOM.bin bs=65536 count=800; i=`expr $i +1`; done

This creates 50 MB files in my_dir.I was wondering how it creates files of that size --> 51,200 KB. the bs states 65536 which is 65536/1024 == 64bytes.

mayb I'm stupid enough to miss something quite obvious here,but kinda annoying cz I cant seem to figure it out at the moment.

Cause 64*800=51200 :)
What you are doing here is moving 800 blocks each of size 64kB from input file to the output file.
Change either bs or count value and you should be fine e.g.
```
while [ $i -ne 31500 ] do dd if=/dev/random of=my_dir/$RANDOM.bin bs=65536 count=1; i=`expr $i +1`; done
```
```
while [ $i -ne 31500 ] do dd if=/dev/random of=my_dir/$RANDOM.bin bs=1 count=65536; i=`expr $i +1`; done
```
```
while [ $i -ne 31500 ] do dd if=/dev/random of=my_dir/$RANDOM.bin bs=81 count=800; i=`expr $i +1`; done
```

---

