---
title: "Anyone would like to help?"
date: 2009-10-13
forum: General Help
---

### Post by Linuxpeguinkit on 2009-10-13
Hi everyone, i got a problem in this shell scripts where during my execute time, in my third tries, if i enter a correct password then the program still activated my time, anyone can help me to correct my problem ?[IMG]http://www.linuxforums.org/forum/images/smilies/confused.gif[/IMG] 
 
 
 
 
#!/bin/bash
time=60
tries=3
start=$(date +%s)
 
left=$time
while true;do
read -t $left -p "Code: " code
((tries--))
left=$(($time-$(date +%s)+start))
if (( $left<=0 || $tries==0 ));then
echo "Time Activated"
break
fi
if [[ "$code" == "abcde" ]];then
echo "Correct!! Time Deactivated"
break
else
echo "Wrong! Please Try again. There are $left seconds and $tries tries left."
fi
done
exit

---

### Post by wojox on 2009-10-13
```
wojox@wojox-desktop:~$ ./time
Code: erer
Wrong! Please Try again. There are 58 seconds and 2 tries left.
Code: erer
Wrong! Please Try again. There are 57 seconds and 1 tries left.
Code: erer
Time Activated
wojox@wojox-desktop:~$ ./time
Code: abcde
Correct!! Time Deactivated
wojox@wojox-desktop:~$
```

Works fine. Don't understand what your doing.

---

