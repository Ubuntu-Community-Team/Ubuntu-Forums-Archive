---
title: "How do I run .jar files?"
date: 2010-07-26
forum: General Help
---

### Post by zack8food on 2010-07-26
title say it all

---

### Post by nmaster on 2010-07-26
at the terminal:```

cd /path/of/the/jar/file
java -jar File.jar
```

if you need to install java, i think that the command will give you an error and give you a list of packages that have java.  install the open jdk/jre package(s)

---

### Post by zack8food on 2010-07-26
I'll try it now

---

### Post by nmaster on 2010-07-26
> **zack8food said:**
> I'll try it now
sounds like a plan...

---

### Post by zack8food on 2010-07-26
/home/zack/downloads/RSBot.jar
 thats what i tried but didnt work

---

### Post by RiceMonster on 2010-07-26
> **zack8food said:**
> /home/zack/downloads/RSBot.jar
 thats what i tried but didnt work

try capitalizing the D in "downloads". Also keep in mind that you cannot cd to a jar file because it is not a directroy.

```
java -jar /home/zack/Downloads/RSBot.jar
```

---

### Post by nmaster on 2010-07-26
> **zack8food said:**
> /home/zack/downloads/RSBot.jar
 thats what i tried but didnt work

sorry, i meant the path to the directory containing the file. do what ricemoster said to do.  its equivalent.

---

### Post by zack8food on 2010-07-26
> **RiceMonster said:**
> try capitalizing the D in "downloads". Also keep in mind that you cannot cd to a jar file because it is not a directroy.

```
java -jar /home/zack/Downloads/RSBot.jar
```

it says

Try: sudo apt-get install <selected package>

---

### Post by slimpickens on 2010-08-09
Don't mean to sound stupid but have you tried right clicking it then select 'open with' then selecting 'SunJava run time'? Its what I do, I know it probably has some old school linux command line users turning in their grave.




[FONT=Verdana,Arial,Times New I2][SIZE=2]**_Winston Church_**[/SIZE][/FONT]**[FONT=Verdana,Arial,Times New I2][SIZE=2]_ill     (1874-1965)_:[/SIZE][/FONT]**       [FONT=Verdana,Arial,Times New I2][SIZE=2]*The     greatest lesson in life is to know that even fools are right sometimes.*[/SIZE][/FONT]

---

