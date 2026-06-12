---
title: "kworkers are going crazy and spoil OpenMp"
date: 2012-03-01
forum: General Help
---

### Post by awada on 2012-03-01
How could I stop kworkers going crazy ?

term-1 top,
term-2 cbm1 <- APP using OpenMP to calculate PI,
term-3 exec command for debugging

++ For about 5 minuts since APP started, kworkers were sane,
++ and APP used cpu 198% (dual core).
++ Screenshot :
    [http://a-wada.s30.xrea.com/xxknl/Screenshot-2012-02-22-13-16-08.png](http://a-wada.s30.xrea.com/xxknl/Screenshot-2012-02-22-13-16-08.png)

++ but, then kworkers woke up and ate cpu 80%+- **incessantly**
++ and APP's went down to 100%+-.
    [http://a-wada.s30.xrea.com/xxknl/Screenshot-2012-02-22-13-17-41.png](http://a-wada.s30.xrea.com/xxknl/Screenshot-2012-02-22-13-17-41.png)
    [http://a-wada.s30.xrea.com/xxknl/Screenshot-2012-02-22-13-19-05.png](http://a-wada.s30.xrea.com/xxknl/Screenshot-2012-02-22-13-19-05.png)
    [http://a-wada.s30.xrea.com/xxknl/Screenshot-2012-02-22-13-35-57.png](http://a-wada.s30.xrea.com/xxknl/Screenshot-2012-02-22-13-35-57.png)

++ referring to "7. Debugging" in "/usr/src/linux-source-3.0.0/Documentation/workqueue.txt"

```
a-wada:~/pai$ sudo su -c 'echo workqueue:workqueue_queue_work > /sys/kernel/debug/tracing/set_event'
[sudo] password for a-wada:
a-wada:~/pai$ sudo su -c 'cat /sys/kernel/debug/tracing/trace_pipe > out.txt'
^C
a-wada:~/pai$ ll out*
-rw-r--r-- 1 root root 23032133 2012-02-22 13:30 out.txt
a-wada:~/pai$ sudo su -c 'cat /proc/THE_OFFENDING_KWORKER/stack > out2.txt'
cat: /proc/THE_OFFENDING_KWORKER/stack: No such file or directory
a-wada:~/pai$ ll out*
-rw-r--r-- 1 root root 23032133 2012-02-22 13:30 out.txt
-rw-r--r-- 1 root root 0 2012-02-22 13:33 out2.txt
```[http://a-wada.s30.xrea.com/xxknl/out.txt](http://a-wada.s30.xrea.com/xxknl/out.txt) <- output of above commands


[http://a-wada.s30.xrea.com/pailnx64/paicbm.c](http://a-wada.s30.xrea.com/pailnx64/paicbm.c) <- source-code of "cbm1" & log when executed normally. 

Please HELP.  Thanks in Advance!

---

