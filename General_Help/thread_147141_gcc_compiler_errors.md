---
title: "gcc compiler errors"
date: 2006-03-19
forum: General Help
---

### Post by Sigma on 2006-03-19
For the past few weeks, I've been able to build GNUChess with no problems, but I ran Automatix last night for the first time, and now I get the following build errors:

> mansoor@ubuntu:~/workspace/cscd94/gnuchess-5.07$ make
Making all in src
make[1]: Entering directory `/home/mansoor/workspace/cscd94/gnuchess-5.07/src'
gcc -DHAVE_CONFIG_H -I. -I. -I.    -pthread -g -O2 -c atak.c
In file included from /usr/include/sched.h:32,
                 from /usr/include/pthread.h:20,
                 from common.h:755,
                 from atak.c:29:
/usr/include/bits/sched.h: In function ‘ReturnCompletedTask’:
/usr/include/bits/sched.h:72: error: storage class specified for parameter ‘clone’
/usr/include/bits/sched.h:98: error: storage class specified for parameter ‘__cpu_mask’
/usr/include/bits/sched.h:107: error: syntax error before ‘__cpu_mask’
In file included from /usr/include/pthread.h:20,
                 from common.h:755,
                 from atak.c:29:
/usr/include/sched.h:41: error: storage class specified for parameter ‘sched_setparam’
/usr/include/sched.h:44: error: storage class specified for parameter ‘sched_getparam’
/usr/include/sched.h:48: error: storage class specified for parameter ‘sched_setscheduler’
/usr/include/sched.h:51: error: storage class specified for parameter ‘sched_getscheduler’
/usr/include/sched.h:54: error: storage class specified for parameter ‘sched_yield’
/usr/include/sched.h:57: error: storage class specified for parameter ‘sched_get_priority_max’
/usr/include/sched.h:60: error: storage class specified for parameter ‘sched_get_priority_min’
/usr/include/sched.h:63: error: storage class specified for parameter ‘sched_rr_get_interval’
In file included from /usr/include/time.h:42,
                 from /usr/include/pthread.h:21,
                 from common.h:755,
                 from atak.c:29:
/usr/include/bits/time.h:40: error: storage class specified for parameter ‘__sysconf’
In file included from /usr/include/pthread.h:21,
                 from common.h:755,
                 from atak.c:29:
/usr/include/time.h:60: error: storage class specified for parameter ‘clock_t’
/usr/include/time.h:181: error: storage class specified for parameter ‘clock_t’
/usr/include/time.h:181: error: conflicting types for ‘clock_t’
/usr/include/time.h:60: error: previous definition of ‘clock_t’ was here
/usr/include/time.h:181: error: syntax error before ‘clock’
/usr/include/time.h:184: error: storage class specified for parameter ‘time’
/usr/include/time.h:188: error: storage class specified for parameter ‘difftime’
/usr/include/time.h:191: error: storage class specified for parameter ‘mktime’
/usr/include/time.h:199: error: storage class specified for parameter ‘strftime’
/usr/include/time.h:229: error: storage class specified for parameter ‘gmtime’
/usr/include/time.h:233: error: storage class specified for parameter ‘localtime’
/usr/include/time.h:240: error: storage class specified for parameter ‘gmtime_r’
/usr/include/time.h:245: error: storage class specified for parameter ‘localtime_r’
/usr/include/time.h:251: error: storage class specified for parameter ‘asctime’
/usr/include/time.h:254: error: storage class specified for parameter ‘ctime’
/usr/include/time.h:263: error: storage class specified for parameter ‘asctime_r’
/usr/include/time.h:267: error: storage class specified for parameter ‘ctime_r’
/usr/include/time.h:272: error: storage class specified for parameter ‘__tzname’
/usr/include/time.h:273: error: storage class specified for parameter ‘__daylight’
/usr/include/time.h:274: error: storage class specified for parameter ‘__timezone’
/usr/include/time.h:279: error: storage class specified for parameter ‘tzname’
/usr/include/time.h:283: error: storage class specified for parameter ‘tzset’
/usr/include/time.h:287: error: storage class specified for parameter ‘daylight’
/usr/include/time.h:288: error: storage class specified for parameter ‘timezone’
/usr/include/time.h:294: error: storage class specified for parameter ‘stime’
/usr/include/time.h:309: error: storage class specified for parameter ‘timegm’
/usr/include/time.h:312: error: storage class specified for parameter ‘timelocal’
/usr/include/time.h:315: error: storage class specified for parameter ‘dysize’
/usr/include/time.h:325: error: storage class specified for parameter ‘nanosleep’
/usr/include/time.h:329: error: storage class specified for parameter ‘clock_getres’
/usr/include/time.h:332: error: storage class specified for parameter ‘clock_gettime’
/usr/include/time.h:336: error: storage class specified for parameter ‘clock_settime’
/usr/include/time.h:355: error: storage class specified for parameter ‘timer_create’
/usr/include/time.h:358: error: storage class specified for parameter ‘timer_delete’
/usr/include/time.h:363: error: storage class specified for parameter ‘timer_settime’
/usr/include/time.h:367: error: storage class specified for parameter ‘timer_gettime’
/usr/include/time.h:370: error: storage class specified for parameter ‘timer_getoverrun’
In file included from common.h:755,
                 from atak.c:29:
/usr/include/pthread.h:166: error: storage class specified for parameter ‘pthread_create’
/usr/include/pthread.h:169: error: storage class specified for parameter ‘pthread_self’
/usr/include/pthread.h:172: error: storage class specified for parameter ‘pthread_equal’
/usr/include/pthread.h:175: error: storage class specified for parameter ‘pthread_exit’
/usr/include/pthread.h:180: error: storage class specified for parameter ‘pthread_join’
/usr/include/pthread.h:186: error: storage class specified for parameter ‘pthread_detach’
/usr/include/pthread.h:194: error: storage class specified for parameter ‘pthread_attr_init’
/usr/include/pthread.h:197: error: storage class specified for parameter ‘pthread_attr_destroy’
/usr/include/pthread.h:201: error: storage class specified for parameter ‘pthread_attr_setdetachstate’
/usr/include/pthread.h:205: error: storage class specified for parameter ‘pthread_attr_getdetachstate’
/usr/include/pthread.h:210: error: storage class specified for parameter ‘pthread_attr_setschedparam’
/usr/include/pthread.h:216: error: storage class specified for parameter ‘pthread_attr_getschedparam’
/usr/include/pthread.h:220: error: storage class specified for parameter ‘pthread_attr_setschedpolicy’
/usr/include/pthread.h:225: error: storage class specified for parameter ‘pthread_attr_getschedpolicy’
/usr/include/pthread.h:229: error: storage class specified for parameter ‘pthread_attr_setinheritsched’
/usr/include/pthread.h:234: error: storage class specified for parameter ‘pthread_attr_getinheritsched’
/usr/include/pthread.h:238: error: storage class specified for parameter ‘pthread_attr_setscope’
/usr/include/pthread.h:242: error: storage class specified for parameter ‘pthread_attr_getscope’
/usr/include/pthread.h:260: error: storage class specified for parameter ‘pthread_attr_setstackaddr’
/usr/include/pthread.h:265: error: storage class specified for parameter ‘pthread_attr_getstackaddr’
/usr/include/pthread.h:284: error: storage class specified for parameter ‘pthread_attr_setstacksize’
/usr/include/pthread.h:289: error: storage class specified for parameter ‘pthread_attr_getstacksize’
/usr/include/pthread.h:304: error: storage class specified for parameter ‘pthread_setschedparam’
/usr/include/pthread.h:310: error: storage class specified for parameter ‘pthread_getschedparam’
/usr/include/pthread.h:334: error: storage class specified for parameter ‘pthread_mutex_init’
/usr/include/pthread.h:337: error: storage class specified for parameter ‘pthread_mutex_destroy’
/usr/include/pthread.h:340: error: storage class specified for parameter ‘pthread_mutex_trylock’
/usr/include/pthread.h:343: error: storage class specified for parameter ‘pthread_mutex_lock’
/usr/include/pthread.h:353: error: storage class specified for parameter ‘pthread_mutex_unlock’
/usr/include/pthread.h:360: error: storage class specified for parameter ‘pthread_mutexattr_init’
/usr/include/pthread.h:363: error: storage class specified for parameter ‘pthread_mutexattr_destroy’
/usr/include/pthread.h:368: error: storage class specified for parameter ‘pthread_mutexattr_getpshared’
/usr/include/pthread.h:372: error: storage class specified for parameter ‘pthread_mutexattr_setpshared’
/usr/include/pthread.h:393: error: storage class specified for parameter ‘pthread_cond_init’
/usr/include/pthread.h:396: error: storage class specified for parameter ‘pthread_cond_destroy’
/usr/include/pthread.h:399: error: storage class specified for parameter ‘pthread_cond_signal’
/usr/include/pthread.h:402: error: storage class specified for parameter ‘pthread_cond_broadcast’
/usr/include/pthread.h:407: error: storage class specified for parameter ‘pthread_cond_wait’
/usr/include/pthread.h:416: error: storage class specified for parameter ‘pthread_cond_timedwait’
/usr/include/pthread.h:421: error: storage class specified for parameter ‘pthread_condattr_init’
/usr/include/pthread.h:424: error: storage class specified for parameter ‘pthread_condattr_destroy’
/usr/include/pthread.h:429: error: storage class specified for parameter ‘pthread_condattr_getpshared’
/usr/include/pthread.h:433: error: storage class specified for parameter ‘pthread_condattr_setpshared’
/usr/include/pthread.h:558: error: storage class specified for parameter ‘pthread_key_create’
/usr/include/pthread.h:561: error: storage class specified for parameter ‘pthread_key_delete’
/usr/include/pthread.h:565: error: storage class specified for parameter ‘pthread_setspecific’
/usr/include/pthread.h:568: error: storage class specified for parameter ‘pthread_getspecific’
/usr/include/pthread.h:581: error: storage class specified for parameter ‘pthread_once’
/usr/include/pthread.h:588: error: storage class specified for parameter ‘pthread_setcancelstate’
/usr/include/pthread.h:592: error: storage class specified for parameter ‘pthread_setcanceltype’
/usr/include/pthread.h:595: error: storage class specified for parameter ‘pthread_cancel’
/usr/include/pthread.h:600: error: storage class specified for parameter ‘pthread_testcancel’
/usr/include/pthread.h:616: error: storage class specified for parameter ‘_pthread_cleanup_push’
/usr/include/pthread.h:625: error: storage class specified for parameter ‘_pthread_cleanup_pop’
In file included from /usr/include/pthread.h:659,
                 from common.h:755,
                 from atak.c:29:
/usr/include/bits/sigthread.h:33: error: storage class specified for parameter ‘pthread_sigmask’
/usr/include/bits/sigthread.h:36: error: storage class specified for parameter ‘pthread_kill’
In file included from common.h:755,
                 from atak.c:29:
/usr/include/pthread.h:677: error: storage class specified for parameter ‘pthread_atfork’
/usr/include/pthread.h:682: error: storage class specified for parameter ‘pthread_kill_other_threads_np’
In file included from atak.c:29:
common.h:774: warning: empty declaration
common.h:775: error: storage class specified for parameter ‘input_status’
common.h:794: error: storage class specified for parameter ‘inputstr’
In file included from common.h:876,
                 from atak.c:29:
inlines.h:42: error: storage class specified for parameter ‘leadz’
inlines.h:42: warning: parameter ‘leadz’ declared ‘inline’
inlines.h:42: error: syntax error before ‘{’ token
atak.c:38: error: syntax error before ‘{’ token
atak.c:42: error: syntax error before ‘a’
atak.c:84: error: storage class specified for parameter ‘rayend’
atak.c:94: error: syntax error before ‘{’ token
atak.c:97: error: conflicting types for ‘t’
atak.c:40: error: previous definition of ‘t’ was here
atak.c:99: error: syntax error before ‘memset’
atak.c:186: error: conflicting types for ‘t’
atak.c:97: error: previous definition of ‘t’ was here
atak.c:188: error: syntax error before ‘a’
atak.c:238: error: redefinition of parameter ‘t’
atak.c:186: error: previous definition of ‘t’ was here
atak.c:240: error: syntax error before ‘a’
atak.c:318: error: syntax error before ‘a’
atak.c:383: error: redefinition of parameter ‘dir’
atak.c:316: error: previous definition of ‘dir’ was here
atak.c:384: error: redefinition of parameter ‘b’
atak.c:97: error: previous definition of ‘b’ was here
atak.c:386: error: syntax error before ‘KingSq’
atak.c:423: error: redefinition of parameter ‘sq’
atak.c:96: error: previous definition of ‘sq’ was here
atak.c:423: error: redefinition of parameter ‘sq1’
atak.c:383: error: previous definition of ‘sq1’ was here
atak.c:424: error: redefinition of parameter ‘b’
atak.c:384: error: previous definition of ‘b’ was here
atak.c:424: error: conflicting types for ‘t’
atak.c:238: error: previous definition of ‘t’ was here
atak.c:426: error: syntax error before ‘*’ token
atak.c:511: error: redefinition of parameter ‘b’
atak.c:424: error: previous definition of ‘b’ was here
atak.c:513: error: syntax error before ‘xside’
atak.c:535: fatal error: opening dependency file .deps/atak.pp: Permission denied
compilation terminated.
make[1]: *** [atak.o] Error 1
make[1]: Leaving directory `/home/mansoor/workspace/cscd94/gnuchess-5.07/src'
make: *** [all-recursive] Error 1


I'm not completely sure if it's something caused by Automatix, but does anyone know how to resolve this problem?

---

### Post by taurus on 2006-03-19
Maybe you need to install the build-essential first!!!
```

sudo apt-get install build-essential

```

---

### Post by Sigma on 2006-03-19
Thanks for your reply, but I already have the build essential.  In fact, I tried reinstalling gcc and libc a number of times, but still get the same error.

---

### Post by Sigma on 2006-03-20
It turns out that this was an actual problem with the code.  I rolled back to an earlier version and it built normally.

---

### Post by MichaelZ on 2006-03-20
[quote=Sigma]
 atak.c:535: fatal error: opening dependency file .deps/atak.pp: Permission denied
compilation terminated.
[/quote] 
I am not sure, but it seems that you have permission problems. May be you can try to run the command with *sudo*. I have had sometimes such a problem when trying to install an application (*make install*). Using *sudo make install*, it worked fine.

Best wishes,
Michael

---

