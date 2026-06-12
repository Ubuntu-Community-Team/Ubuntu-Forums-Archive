---
title: "BASH Script to get PID of Java file"
date: 2011-06-18
forum: General Help
---

### Post by markh789 on 2011-06-18
Okay I have a simple bash script called run.sh:

```

java -jar /testing/run.java

```

How do I get the Process ID and save it in a file called "PID"

---

### Post by amauk on 2011-06-18
The Bash variable $! return the PID of the last backgrounded process
So, if you run the command in the background (append & to end of command)
you can just write $! to a file
```
java -jar /testing/run.java &
echo "$!" > PID
```

---

