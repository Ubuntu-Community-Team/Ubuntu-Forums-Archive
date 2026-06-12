---
title: "Random Number Script"
date: 2012-04-02
forum: General Help
---

### Post by yodomino6 on 2012-04-02
I have a script that I need to generate a random number 1-14. I had this running great on an older machine (9.10) but I am migrating to 11.10.

I am using the following command:
```
n=$((RANDOM%14+1))
echo $n
```

On my older machine, it works no problem, on the newer one it returns a 1 every time. If I run the command on it's own in Terminal, it will work fine but not in a script.

---

### Post by sanderj on 2012-04-02
That is a matter of which shell you use. You have to use bash. The script then looks like this:


```

#!/bin/bash
n=$((RANDOM%14+1))
echo $n

```

Then "chmod +x" it, and run it.

HTH

---

### Post by brainwash on 2012-04-02
Apparently bash doesn't know the RANDOM var. There are other solutions to generate (pseudo-)random numbers like using awk:
```
#!/bin/bash
n=$(echo | awk '{srand(); print substr(rand(),3)%14+1}')
echo $n
```

---

### Post by Vaphell on 2012-04-02
> Apparently bash doesn't know the RANDOM var
it does
```
$ for i in {1..3}; do sh -c 'echo $((RANDOM%14+1))'; done
1
1
1
$ for i in {1..3}; do bash -c 'echo $((RANDOM%14+1))'; done
10
6
13
```

---

### Post by HiImTye on 2012-04-03
it certainly does, I use it in my XWinWrap bash script
```
 if [ "$SEL" = "$RAND1" ]; then
  RAND2=$((RANDOM%61+1))
  eval SEL=\$OPT$RAND2
 fi
```
[http://ubuntuforums.org/showthread.php?t=1949450](http://ubuntuforums.org/showthread.php?t=1949450)

---

### Post by yodomino6 on 2012-04-04
Sorry for the delay, it's been busy!

Yes, it is a bash script. It is the exact script that worked previously in 9.10. 

Thanks to brainwash, I was able to get it working using his example!

Thanks everyone

---

### Post by Vaphell on 2012-04-04
awk solution is an overkill, it will work if you have a hashbang line at the top to define default shell for the script
```
#!/bin/bash
```
and when using the script you can't call another shell explicitly like *sh my_script* (that would override the default bash)

---

