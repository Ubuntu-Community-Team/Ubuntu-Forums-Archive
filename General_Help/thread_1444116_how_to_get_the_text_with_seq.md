---
title: "how to get the text with seq?"
date: 2010-03-31
forum: General Help
---

### Post by luofeiyu on 2010-03-31
i can get the result with seq command
~$ seq 1 10
1
2
3
4
5
6
7
8
9
10
1)what i want is :
1.mov
2.mov
3.mov
4.mov
5.mov
6.mov
7.mov
8.mov
9.mov
10.mov
how to write the script?
2)what i want is :
1.mov 2.mov 3.mov 4.mov 5.mov 6.mov 7.mov 8.mov 9.mov 10.mov
there is only one  blank space between  them.
how to write the script?
your script are welcome.

---

### Post by sisco311 on 2010-03-31
```
for i in $(seq 1 10); do 
  echo -n "${i}.mov "
done
echo
```

---

### Post by geirha on 2010-03-31
In bash, you can use brace expansion to achieve that.
```
echo {1..10}.mov
```

---

### Post by luofeiyu on 2010-03-31
why this command can't run?
echo /home/pt/t/{3..10}.MOV.mpg | mkvcdfs

---

### Post by sisco311 on 2010-03-31
> **luofeiyu said:**
> why this command can't run?
echo /home/pt/t/{3..10}.MOV.mpg | mkvcdfs

What's the error message?

Try:
```
mkvcdfs /home/pt/t/{3..10}.MOV.mpg
```

---

### Post by luofeiyu on 2010-03-31
it's ok
 mkvcdfs /home/pt/t/{3..10}.MOV.mpg
think you

---

### Post by luofeiyu on 2010-04-01
pt@pt-laptop:~$ echo /home/pt/t/{3..10}.MOV.mpg | mkvcdfs
Usage: mkvcdfs MPEG-files ....
dear sisco311,can you tell me why the command can't run?

echo /home/pt/t/{3..10}.MOV.mpg | mkvcdfs

---

