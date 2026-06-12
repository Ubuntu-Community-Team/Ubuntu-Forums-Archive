---
title: "javaw - command not found"
date: 2011-03-25
forum: General Help
---

### Post by birdy62 on 2011-03-25
I want to start use an application that requires javaw, (a virtual slide rule app) . At the moment running the script that launches the app looks like this.
```
./gusr: line 2: javaw: command not found
``` 

The script is just this line:

```
javaw  -cp "./lib/gusr.jar" -ea com.griffenfly.slide.SlideRule
```

Obviously javaw is missing or not in the path for some reaon. How to fix this. 

Output of ```
java -version java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9.7) (6b20-1.9.7-0ubuntu1~9.10.1)
OpenJDK Server VM (build 19.0-b09, mixed mode)
```

Thanks

---

### Post by birdy62 on 2011-04-03
bump!!

---

### Post by luigi_mb on 2011-04-03
javaw.exe (note: not "javaws") is a MS command. Under Linux use "java".

/luigi

---

### Post by birdy62 on 2011-04-04
Thanks, I didn't realise this. The script that actually comes in a tar file specifically packaged for Linux. Running the command produces the error ```
Exception in thread "main" java.lang.NoClassDefFoundError
``` . I was hoping to track down the error myself, but I'll contact the developer.

Thanks again for your help

---

