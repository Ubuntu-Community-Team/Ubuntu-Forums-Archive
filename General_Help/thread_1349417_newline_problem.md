---
title: "newline problem"
date: 2009-12-08
forum: General Help
---

### Post by dandeliondream on 2009-12-08
[COLOR=Purple]ddata[/COLOR] (file used in first line of code)
 Francis\CEO\HQ\15000*12*1
 Janine\CFO\Finance\12000*23*2
 Bobby\Manager\IT\7200*5*3
 Jenny\Secretary\HQ\2000*7*4
 Katty\Programmer\IT\2800*899*5
 Fonny Lai\Analyst\Finance\1233*1*6
 Daniel Mee\***. Manager\IT\12000*9*7
 Francis Lee\CEO\a\15000*12*1

How do I change the code below so as to get correct output.
echo -e `cut -d '\' -f3,4 ddata \n` > ddata1 (this line of code is in a bash script file) 


[COLOR=Red]Wrong!![/COLOR]
abc@ubuntu:~$ cat ddata1
HQ\15000*12*1 Finance\12000*23*2 IT\7200*5*3 HQ\2000*7*4 IT\2800*899*5 Finance\1233*1*6 IT\12000*9*7 a\15000*12*1

[COLOR=SeaGreen]Correct[/COLOR]
abc@ubuntu:~$ cat ddata1
HQ\15000*12*1 
Finance\12000*23*2 
IT\7200*5*3 
HQ\2000*7*4
IT\2800*899*5 
Finance\1233*1*6 
IT\12000*9*7
a\15000*12*1

---

### Post by m_duck on 2009-12-08
The following seems to work:```
echo -e "`cut -d '\' -f3,4 ddata` \n" > ddata1
```It was due to the "\n" needing to be applied to the echo command rather than as part of the cut command. I think... I am far from being a bash script expert!

---

### Post by dandeliondream on 2009-12-08
> **m_duck said:**
> The following seems to work:```
echo -e "`cut -d '\' -f3,4 ddata` \n" > ddata1
```It was due to the "\n" needing to be applied to the echo command rather than as part of the cut command. I think... I am far from being a bash script expert!


It works! Thanks! You're good enough to assist newbie like me.

---

