---
title: "Quick Data Manipulation Help Required"
date: 2009-08-05
forum: General Help
---

### Post by matessim on 2009-08-05
so lets say i have a list of hosts
10.10.2.157 0016763337DA -

10.10.2.84 001676333CF9 -

10.10.2.85 0015001C6FFB -

the problem is i need them in a format where the mac adresses are like this
10.10.2.157 00:16:76:33:37:DA -
10.10.2.84 00:16:76:33:3C:F9 -
10.10.2.85 00:15:00:1C:6F:FB -

i have about a 150 of theese enteries... it would be nice to have some Shellcode-Fu ninja to help me

---

### Post by matessim on 2009-08-06
bump :S

---

### Post by Johnny B on 2009-08-06
do you just want to remove the blank lines?
> cat filename | grep -v '^$'

---

### Post by matessim on 2009-08-06
there are no blank lines on both versions, i don't see them in the original post if there are....
what i need is to put a : every  2 digits on the mac adress, i need 5, because first : is after the 2nd, and theres no : after the last letter, just 2 letters before (or 1?
like 00:00:00:00:00

---

### Post by Johnny B on 2009-08-06
sorry i missed those semicolons...
try this:      (Not tested, dont over write your file!)
> awk '{cat filename | awk 'print(substr($1,1,4))":"(substr($1,5,6))}'

---

### Post by matessim on 2009-08-06
matessim@matessim-laptop:/home/logs$ awk '{cat HOSTS.LST | awk 'print(substr($1,1,4))":"(substr($1,5,6))}' 
bash: syntax error near unexpected token `('
matessim@matessim-laptop:/home/logs$ 

tried it twice to make sure it doesn't work

---

### Post by Johnny B on 2009-08-06
sorry, about that, i just tried it too
i may need a minute...

---

### Post by matessim on 2009-08-06
Take your time, really appriciate your help

---

### Post by Johnny B on 2009-08-06
ok i tried this twice so....

> cat file | sed '/^$/d' | awk '{print $1" "(substr($2,2,2))":"(substr($2,4,2))":"(substr($2,6,2))":"(substr($2,8,2))":"(substr($2,10,2))" -" }'

and if you want put sort on the end 
> <long command>  | sort

---

### Post by matessim on 2009-08-06
holy **** it works

---

### Post by Johnny B on 2009-08-06
Lol

---

### Post by matessim on 2009-08-06
how do i output it to a file? i tried making a sh but itsnot working, it only echo's it in terminal```

cat /home/logs/HOSTS.LST | sed '/^$/d' | awk '{print $1" "(substr($2,2,2))":"(substr($2,4,2))":"(substr($2, 6,2))":"(substr($2,8,2))":"(substr($2,10,2))" -" }' > cleanhosts.LST
```

---

### Post by Johnny B on 2009-08-06
add
>  > /home/username/filename
to the end, dont forget the leading space

---

### Post by matessim on 2009-08-06
I bow to you, Man! thanks for all the help!

---

### Post by matessim on 2009-08-06
omg... i still have a problem, i can't load them the macs still appear as empty when i load
whats the diffrence between
10.0.0.1 00:0F:B0:CE:00:D9 -
10.0.0.2 00:0F:B0:CE:00:D9 -
10.0.0.138 00:20:8F:11:6E:03 -

and
10.10.2.136 00:7E:96:C3:F5 -
10.10.2.63 08:04:85:25:A5 -
10.10.2.80 01:67:6C:DF:38 -
10.10.2.65 01:67:6C:DF:38 -
10.10.2.68 00:7E:96:C3:B3 -
10.10.2.1 08:04:85:25:B7 -

that the first loads and the second doesn't

---

### Post by Mka on 2009-08-06
```
while read line ; do
ip=`echo $line | awk -F\  '{print $1}'`;
mac=`echo $line | awk -F\  '{print $2} | awk '{print(substr($1,1,2))":"(substr($1,3,2))":"(substr($1,5,2))":"(substr($1,7,2))":"(substr($1,9,2))":"(substr($1,11,2))}'`;
echo $ip " " $mac " -";
done < FILENAME.txt

```

---

### Post by Johnny B on 2009-08-06
oops forgot #12:
> cat /home/logs/HOSTS.LST | sed '/^$/d' | awk '{print $1" "(substr($2,2,2))":"(substr($2,4,2))":"(substr($2, 6,2))":"(substr($2,8,2))":"(substr($2,10,2))**":"(substr($2,12,2))**" -" }' > cleanhosts.LST

---

### Post by matessim on 2009-08-06
you magican! it works!!!

---

