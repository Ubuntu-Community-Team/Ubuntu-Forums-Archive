---
title: "any help in java.io.IOException????"
date: 2012-09-25
forum: General Help
---

### Post by marwa aly on 2012-09-25
when i run the GIST program on ubuntu 12.04 LTS 64 bit , these massage appeared 


SEVERE: null
java.io.IOException: Cannot run program "./shell_islandPath": java.io.IOException: error=13, Permission denied
    at java.lang.ProcessBuilder.start(ProcessBuilder.java:475)
    at java.lang.Runtime.exec(Runtime.java:610)
    at java.lang.Runtime.exec(Runtime.java:448)
    at java.lang.Runtime.exec(Runtime.java:345)
    at RunProgram.runMe(RunProgram.java:127)
    at GISTForm$21.run(GISTForm.java:923)
Caused by: java.io.IOException: java.io.IOException: error=13, Permission denied
    at java.lang.UNIXProcess.<init>(UNIXProcess.java:164)
    at java.lang.ProcessImpl.start(ProcessImpl.java:81)
    at java.lang.ProcessBuilder.start(ProcessBuilder.java:468)
    ... 5 more

so can u help me??

---

### Post by marinara on 2012-09-26
where did you get GIST? How did you install?

---

