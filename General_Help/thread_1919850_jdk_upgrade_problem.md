---
title: "jdk upgrade problem"
date: 2012-02-02
forum: General Help
---

### Post by learning_ on 2012-02-02
Ok, here's my dilemma :-k :
I need the current version of jdk installed (1.7.0_02) and I followed these tutorials [http://www.shinephp.com/install-jdk-7-on-ubuntu/]("http://www.shinephp.com/install-jdk-7-on-ubuntu/") [http://docs.oracle.com/javase/7/docs/webnotes/install/linux/linux-jdk.html#install-64](http://docs.oracle.com/javase/7/docs/webnotes/install/linux/linux-jdk.html#install-64) and I forgot to select 1.7.0_02 as the version to use so when I ran the java -version command it returned ```
java version 1.6.0_20
``` but that isn't the problem. After I went back into --config java and fixed that by selecting 1.7.0_02, I tried to find the version again with java -version and now I get this ```
bash: /usr/bin/java: cannot execute binary file

``` ](*,)

I can't find any solution anywhere else. PLEASE someone help!

---

### Post by learning_ on 2012-02-03
ok so this may have seemed obvious but it didn't click until I was just staring at this wall of commands that I put in last night: somehow the java.bin was removed from the /usr/bin/ directory but that's about all I know. I don't even know what that means or how to even start to try and fix it. Any ideas anyone?

---

### Post by howefield on 2012-02-03
Thread closed.

Duplicate here : [http://ubuntuforums.org/showthread.php?t=1919487](http://ubuntuforums.org/showthread.php?t=1919487)

---

### Post by cariboo on 2012-02-03
It seems I merged the two threads while howefield, closed one of the threads. This is the thread linked to in howfield's post.

---

