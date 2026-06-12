---
title: "Java eats CPU - howto stop all java commands?"
date: 2011-09-07
forum: General Help
---

### Post by skipidar on 2011-09-07
Hello folks,
I have a problem with a java process - it eats nearly 100% of the cpu. Obviously there are some commands, which wont stop.


[LIST]
[*]I tried to kill the java process, but it returns immediately.
[*]I tried to get all java commands by doing "ps auxwww | grep java" , the result is on the image- i think i found the commands, which are all the ec2 commands on the pic. What do I do now with the result of "ps auxwww | grep java" ? How can I stop all theses commands?
[/LIST]

[IMG]http://i51.tinypic.com/2yn46f9.png[/IMG]

---

### Post by skipidar on 2011-09-07
The solution was quite easy - 

do list all running commands with matching process ids 
```
ps ax
```
and kill the java commands by using 
```
kill THEPIDHERE
```

---

