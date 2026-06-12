---
title: "k9copy Errors"
date: 2012-03-17
forum: General Help
---

### Post by lefo on 2012-03-17
I've installed k9copy, the medibuntu files, dvdread, etc.  However, I keep getting error messages.  I've tried to run k9copy from the terminal, and I get this error:

"k9copy
k9copy: error while loading shared libraries: libQtCore.so.4: cannot open shared object file: No such file or directory
"

I've tried Googling it, but I keep getting issues with Google Earth that don't really seem to have the same issues.

Can anyone suggest where the problem is?

Thanks.

---

### Post by lefo on 2012-03-17
Also, if it helps, here's the crash report from k9copy...


Application: k9copy (k9copy), signal: Aborted
[Current thread is 1 (Thread 0x7f0b47d03780 (LWP 2572))]

Thread 4 (Thread 0x7f0b323ad700 (LWP 2574)):
#0  0x00007f0b42a9c473 in poll () from /lib/x86_64-linux-gnu/libc.so.6
#1  0x00007f0b3c7d7f68 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x00007f0b3c7d8429 in g_main_context_iteration () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#3  0x00007f0b43d22f3e in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#4  0x00007f0b43cf6cf2 in QEventLoop::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#5  0x00007f0b43cf6ef7 in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#6  0x00007f0b43c0e27f in QThread::exec() () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#7  0x00007f0b43cd9cbf in ?? () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#8  0x00007f0b43c10d05 in ?? () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#9  0x00007f0b40955efc in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
#10 0x00007f0b42aa859d in clone () from /lib/x86_64-linux-gnu/libc.so.6
#11 0x0000000000000000 in ?? ()

Thread 3 (Thread 0x7f0b2a7fb700 (LWP 2594)):
#0  0x00007f0b4095a04c in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/x86_64-linux-gnu/libpthread.so.0
#1  0x00007f0b43c111ab in QWaitCondition::wait(QMutex*, unsigned long) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#2  0x00007f0b43c10a4c in QThread::wait(unsigned long) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#3  0x00000000004ec27f in ?? ()
#4  0x00007f0b43c10d05 in ?? () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#5  0x00007f0b40955efc in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
#6  0x00007f0b42aa859d in clone () from /lib/x86_64-linux-gnu/libc.so.6
#7  0x0000000000000000 in ?? ()

Thread 2 (Thread 0x7f0b29749700 (LWP 2595)):
[KCrash Handler]
#6  0x00007f0b429fb3a5 in raise () from /lib/x86_64-linux-gnu/libc.so.6
#7  0x00007f0b429feb0b in abort () from /lib/x86_64-linux-gnu/libc.so.6
#8  0x00007f0b43c0743b in qt_message_output(QtMsgType, char const*) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#9  0x00007f0b43c077ef in ?? () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#10 0x00007f0b43c07994 in qFatal(char const*, ...) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#11 0x00000000004a0545 in ?? ()
#12 0x00000000004c9b36 in ?? ()
#13 0x00000000004c8769 in ?? ()
#14 0x00000000004e9c15 in ?? ()
#15 0x00007f0b43c10d05 in ?? () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#16 0x00007f0b40955efc in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
#17 0x00007f0b42aa859d in clone () from /lib/x86_64-linux-gnu/libc.so.6
#18 0x0000000000000000 in ?? ()

Thread 1 (Thread 0x7f0b47d03780 (LWP 2572)):
#0  0x00007f0b4095a04c in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/x86_64-linux-gnu/libpthread.so.0
#1  0x00007f0b43c111ab in QWaitCondition::wait(QMutex*, unsigned long) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#2  0x00007f0b43c10a4c in QThread::wait(unsigned long) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#3  0x00000000004c7a12 in ?? ()
#4  0x00000000004c7cac in ?? ()
#5  0x00000000004c7e82 in ?? ()
#6  0x00000000004c8460 in ?? ()
#7  0x00000000004dc848 in ?? ()
#8  0x000000000044f879 in ?? ()
#9  0x0000000000424f44 in _start ()

---

### Post by oldos2er on 2012-03-17
Which version of Ubuntu and which version of k9copy are you running?

---

### Post by lefo on 2012-03-18
> **oldos2er said:**
> Which version of Ubuntu and which version of k9copy are you running?

I'm sorry...

Ubuntu 11.10 with k9copy 2.3.7-3.

Thanks for responding.

---

### Post by oldos2er on 2012-03-18
Thanks for that. 

The latest version of k9copy is 2.3.8, if you want to give it a try. I can't say if doing so will help with your problem. Also the program is no longer being developed, [http://k9copy.sourceforge.net/web/index.php/en/news](http://k9copy.sourceforge.net/web/index.php/en/news)

---

### Post by lefo on 2012-03-19
Thank you. I installed the latest and I'm able to copy again.  Good call.

---

### Post by kalkems on 2012-03-19
If k9copy is not being supported is there another program that will do the same job?
/ernie

---

### Post by oldos2er on 2012-03-20
I use k3b to rip DVDs to make a one-to-one copy. There are several apps available. [http://www.cyberciti.biz/tips/linux-dvd-ripper-software.html](http://www.cyberciti.biz/tips/linux-dvd-ripper-software.html)

---

### Post by kalkems on 2012-03-21
I tried the different program at the link you recommended but I had tons of problems. Some wouldn't install and others just didn't work. I expect part of the problem is my lack of knowledge in copying dvd/cd's but it also seems to have to do with either me using Ubuntu 12.04 or that my version is 64bit.
/ernie

---

### Post by oldos2er on 2012-03-21
kalkems, you should start your own thread and give as may details about your problems as possible.

---

