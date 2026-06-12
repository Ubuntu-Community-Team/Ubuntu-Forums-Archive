---
title: "set the classPath to External jars"
date: 2011-07-18
forum: General Help
---

### Post by lakshmijs433 on 2011-07-18
i am new to ubuntu how to set the classpath to external jars

---

### Post by dethorpe on 2011-07-18
Its the same as any java implementation, just add the paths to your CLASSPATH environment variable (in your .bashrc file if want it evertime you logon) or use the -cp option on the java command line
 
e.g.
 
```
 
export CLASSPATH=$CLASSPATH:/path/to/some/jar/classname.jar:/path/to/another/jar/anotherclassname.jar

```
 
or 
 
```
 
java -cp $CLASSPATH:/path/to/some/jar/classname.jar:/path/to/another/jar/anotherclassname.jar programname

```

---

### Post by lakshmijs433 on 2011-07-19
Thank you

---

