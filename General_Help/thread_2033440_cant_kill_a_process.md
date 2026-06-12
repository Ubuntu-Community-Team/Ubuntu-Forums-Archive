---
title: "cant kill a process"
date: 2012-07-26
forum: General Help
---

### Post by cucuru on 2012-07-26
hello! I have a process I cant kill, I think it's something about STAT values, it has T, which I read:

> 
T    Stopped, either by a job control signal or because it is being traced.


This is what I try to do:
```

ubuntu@ubuntu:~$ ps -u
Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
ubuntu    3552  0.1  4.5 437584 46696 pts/0    Ssl+ Jul17  18:01 java spb.init
ubuntu   19001  0.0  0.5   9252  5996 pts/1    Ss   09:08   0:00 -bash
ubuntu   19097  0.0  3.1 415012 32220 pts/1    Tl   09:08   0:11 java spb.initAtlanta
ubuntu   21510  0.8  0.5   9212  5900 pts/3    Ss   12:39   0:00 -bash
ubuntu   21550 21.5  2.6 411468 26900 pts/1    Sl+  12:39   0:00 java spb.initDemo
ubuntu   21565  0.0  0.1   4588  1088 pts/3    R+   12:39   0:00 ps -u
ubuntu@ubuntu:~$ ps -u
Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
ubuntu    3552  0.1  4.5 437584 46696 pts/0    Ssl+ Jul17  18:02 java spb.init
ubuntu   19001  0.0  0.5   9252  5996 pts/1    Ss   09:08   0:00 -bash
ubuntu   19097  0.0  3.1 415012 32220 pts/1    Tl   09:08   0:11 java spb.initAtlanta
ubuntu   21510  0.1  0.5   9212  5900 pts/3    Ss   12:39   0:00 -bash
ubuntu   21550  0.4  2.6 411792 27340 pts/1    Sl+  12:39   0:01 java spb.initDemo
ubuntu   21607  0.0  0.1   4588  1096 pts/3    R+   12:44   0:00 ps -u
ubuntu@ubuntu:~$ kill 21550
ubuntu@ubuntu:~$ ps -u
Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
ubuntu    3552  0.1  4.5 437584 46696 pts/0    Ssl+ Jul17  18:02 java program
ubuntu   19001  0.0  0.5   9252  5996 pts/1    Ss+  09:08   0:00 -bash
ubuntu   19097  0.0  3.1 415012 32220 pts/1    Tl   09:08   0:11 java program2
ubuntu   21510  0.1  0.5   9212  5900 pts/3    Ss   12:39   0:00 -bash
ubuntu   21612  0.0  0.1   4588  1092 pts/3    R+   12:44   0:00 ps -u
ubuntu@ubuntu:~$ kill 19097
ubuntu@ubuntu:~$ ps -u
Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
ubuntu    3552  0.1  4.5 437584 46696 pts/0    Ssl+ Jul17  18:02 java program
ubuntu   19001  0.0  0.5   9252  5996 pts/1    Ss+  09:08   0:00 -bash
ubuntu   19097  0.0  3.1 415012 32220 pts/1    Tl   09:08   0:11 java program2
ubuntu   21510  0.1  0.5   9212  5900 pts/3    Ss   12:39   0:00 -bash
ubuntu   21615  0.0  0.1   4588  1092 pts/3    R+   12:44   0:00 ps -u


```

I want to kill program2 and I cant! what can be my problem?

Thank you in advance

---

### Post by hakermania on 2012-07-26
Try
```

kill -9 19097

```

---

### Post by cucuru on 2012-07-26
Thanks!! it worked!

---

