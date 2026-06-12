---
title: "String extraction."
date: 2009-07-30
forum: General Help
---

### Post by kodalisrikanth on 2009-07-30
Hi,

I have some problem with extracting the text from the logs.
Here is the log file looks like.

linenumber:INFO |Date|time|name|s=sessionid>..garbage.
[COLOR="Red"]Example:
69736:INFO |2009/07/17|15:26:59|p=Helloworld|s=A376B050AD83524106D7023F45233DD> Session "A376B050AD83524106D7023F45233DD" created.[/COLOR]

Here,
Linenumber values are 1,2,3 ...etc
INFO,Date,time,sessionid are fixed size. 
name is variable size.

I want to retrieve all the fields(Line number, Date, Time, Sessionid from this log file)  


work done:
Tried awk,
[B][COLOR="Red"]grep -n 'created\|disposed' /opt/tomcat/logs/catalina.out | awk '{print $1}'
But, this is giving the output in this format.
Linenumber:INFO[/COLOR][/B]

I tried with print$2,$3 .. but no luck.

Please help me out.


Thanks,
Srikanth.

---

### Post by kodalisrikanth on 2009-07-30
The log file is very huge. So, i have to optimize the code.


Thanks,
Srikanth.

---

### Post by DaithiF on 2009-07-30
Hi
using a perl expression:
[COLOR=Black]
[/COLOR]```
grep -n 'created\|disposed' /opt/tomcat/logs/catalina.out | perl -p -e 's/^([0-9]*):.+?\|(.+?)\|(.+?)\|.+?s=(.+?)>.*$/$1\t$2\t$3\t$4/'


```
produces:
```
69736      2009/07/17      15:26:59      A376B050AD83524106D7023 F45233DD

```

cheers
d

---

