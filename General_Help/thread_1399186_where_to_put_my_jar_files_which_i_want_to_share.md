---
title: "where to put my jar files which i want to share"
date: 2010-02-05
forum: General Help
---

### Post by creatxr on 2010-02-05
where to put my jar files which i want to share?
is here /usr/share/java ?
i put my jar here,
but when i run java application which class has only a main methodd with Class.forName(),
it cannot find the jar.
so i must use command "java -cp .:my.jar A" to run 
i want that i don't need -cp option to run my A.class.
how to?

---

### Post by rnerwein on 2010-02-05
hi 
i ain't know nearly nothing about java ( c programmer ) but isn't there a CLASSPATH in java ??

set your CLASSPATH in ~/.bashrc  ( or what ever shell you are using)

CLASSPATH=$CLASSPATH:/where_ever_you_put_your_stuff
export CLASSPATH

ciao

---

