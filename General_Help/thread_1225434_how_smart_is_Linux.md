---
title: "how smart is Linux?"
date: 2009-07-28
forum: General Help
---

### Post by tjk on 2009-07-28
I've often wondered why Linux (kernal??) ever allows a background application to grab the majority (or all) of the processes?  Isn't Linux smart enough to distinguish what is running in the foreground and limit the priority of background apps?  (For example, Python occasionally starts running and uses 100% of my CPU -- making my computer almost inoperable until I kill the app.)

I know that for some of you there is an easy explanation... but I don't know, so I'm asking...

---

### Post by QIII on 2009-07-28
A frequent culprit is not the app itself, but something that is difficult to detect in top.

Do you have vino (remote desktop) running?

---

### Post by tjk on 2009-07-28
> **QIII said:**
> A frequent culprit is not the app itself, but something that is difficult to detect in top.

Do you have vino (remote desktop) running?

Nothing named vino in my process list... not running as far as I know.

---

### Post by QIII on 2009-07-28
That's just it.  It often doesn't show up -- which is why it is a pain.

Not at my Ubuntu machine at the moment.

Someone will chime in momentarily to let you know how to check.

---

### Post by XCan on 2009-07-28
I find the easiest way to check if a process is running is to use grep with ps, i.e.,

```
ps aux | grep vino
```

---

### Post by tjk on 2009-07-28
> **XCan said:**
> I find the easiest way to check if a process is running is to use grep with ps, i.e.,

```
ps aux | grep vino
```

can you interpret this:
  tim      21975  0.0  0.0   7524   908 pts/1    S+   12:01   0:00 grep vino

---

### Post by DeMus on 2009-07-28
> **XCan said:**
> I find the easiest way to check if a process is running is to use grep with ps, i.e.,

```
ps aux | grep vino
```

So when I get the answer:
jan      13573  0.0  0.0   7524   908 pts/0    S+   21:22   0:00 grep vino
it means I have vino running?
What is vino and do I need it? Can I stop it? It does not show up in top and htop, nor in System monitor.
When I use archive manager to unrar a file my PC is very slow although I have 4 cores and only one (not even completely) is used by archive manager, is this caused by vino? Is that really so?

---

### Post by Chris Musampa on 2009-07-28
> **DeMus said:**
> So when I get the answer:
jan      13573  0.0  0.0   7524   908 pts/0    S+   21:22   0:00 grep vino
it means I have vino running?
What is vino and do I need it? Can I stop it? It does not show up in top and htop, nor in System monitor.
When I use archive manager to unrar a file my PC is very slow although I have 4 cores and only one (not even completely) is used by archive manager, is this caused by vino? Is that really so?

If I'm not mistaken that output is the result of the command you entered, ie it is showing the grep that you used to filter the results, if you had a vino process running I would expect more than one line of output.

For exapmple:```
$ ps aux | grep kdm
root      2594  0.0  0.0   3444   704 ?        Ss   12:45   0:00 /usr/bin/kdm
me        5548  0.0  0.0   3344   808 pts/1    S+   20:32   0:00 grep kdm

```

---

### Post by j.bell730 on 2009-07-28
Run *just* ```
ps aux
``` and it will return this at the top: ```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
``` thus, when *I* run it, it's meant to be interpreted as: ```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
jared    31784  0.0  0.0   8604   908 pts/1    S+   15:27   0:00 grep vino
```

---

### Post by DeMus on 2009-07-28
> **Chris Musampa said:**
> If I'm not mistaken that output is the result of the command you entered, ie it is showing the grep that you used to filter the results, if you had a vino process running I would expect more than one line of output.

For exapmple:```
$ ps aux | grep kdm
root      2594  0.0  0.0   3444   704 ?        Ss   12:45   0:00 /usr/bin/kdm
me        5548  0.0  0.0   3344   808 pts/1    S+   20:32   0:00 grep kdm

```

When I do a ps aux | grep vino and I get one line which says vino is running, it even has a id nr. doesn't that mean it is running?
Okay, you expected more lines, but why one line when it is not running?

What is vino, do I need it and if not, can I stop it?

---

### Post by Chris Musampa on 2009-07-28
> **DeMus said:**
> When I do a ps aux | grep vino and I get one line which says vino is running, it even has a id nr. doesn't that mean it is running?
Okay, you expected more lines, but why one line when it is not running?

What is vino, do I need it and if not, can I stop it?

But it doesn't say 'vino' is running, it says 'grep vino' is running.  

I think vino is something to do with vnc in gnome.

---

### Post by DeMus on 2009-07-28
> **Chris Musampa said:**
> But it doesn't say 'vino' is running, it says 'grep vino' is running.  

I think vino is something to do with vnc in gnome.

OK, thanks. So, it's not running. Fine. Then my question remains: why is my computer so slow when using archive manager, or some other programs as well?

---

### Post by Chris Musampa on 2009-07-28
> **DeMus said:**
> OK, thanks. So, it's not running. Fine. Then my question remains: why is my computer so slow when using archive manager, or some other programs as well?

Have you been feeding it those Amsterdam cakes? :D

I don't know is the answer.

---

### Post by Simian Man on 2009-07-28
> **tjk said:**
> I've often wondered why Linux (kernal??) ever allows a background application to grab the majority (or all) of the processes?  Isn't Linux smart enough to distinguish what is running in the foreground and limit the priority of background apps?  (For example, Python occasionally starts running and uses 100% of my CPU -- making my computer almost inoperable until I kill the app.)


The operating system gives computing resources to applications that request them - that's all.  If an application is coded in such a way that it continually performs computations, the OS will give it the resources if they are there.

If an application is taking more resources than it really should need, than it is likely a bug in that program.  The OS can't just say, "it's a background process, it gets no cycles" because, for example, I frequently run simulations as background processes and I *want* them to max out my CPU.

---

### Post by lukeiamyourfather on 2009-07-28
> **Simian Man said:**
> The operating system gives computing resources to applications that request them - that's all.  If an application is coded in such a way that it continually performs computations, the OS will give it the resources if they are there.

If an application is taking more resources than it really should need, than it is likely a bug in that program.  The OS can't just say, "it's a background process, it gets no cycles" because, for example, I frequently run simulations as background processes and I *want* them to max out my CPU.

That's pretty much exactly what I was going to say. :)

On another note if you want to see what's using the majority of the processes at any given time you can create a script or run a command that makes a log of what top spits out. Something like this.

```
top | grep vino > ~/topLog.txt
```

Check the log when you notice things running really slowly. Or instead of logging vino you could log everything top spits out. Cheers!

---

### Post by jocko on 2009-07-28
> **tjk said:**
> I've often wondered why Linux (kernal??) ever allows a background application to grab the majority (or all) of the processes?  Isn't Linux smart enough to distinguish what is running in the foreground and limit the priority of background apps?  (For example, Python occasionally starts running and uses 100% of my CPU -- making my computer almost inoperable until I kill the app.)

I know that for some of you there is an easy explanation... but I don't know, so I'm asking...
> **lukeiamyourfather said:**
> That's pretty much exactly what I was going to say. :)

On another note if you want to see what's using the majority of the processes at any given time you can create a script or run a command that makes a log of what top spits out. Something like this.

```
top | grep vino > ~/topLog.txt
```Check the log when you notice things running really slowly. Or instead of logging vino you could log everything top spits out. Cheers!
Why has everyone got so hung up on vino? If you haven't started vino yourself, it's not running...
If, as the op says, python suddenly starts to use 100% of the cpu it simply means that a python process is either doing it's job and using the cpu as a result of that, or there is a bug in it that makes it use 100% of the cpu. Same if java starts to use 100% of cpu, it's caused by a java application, and if firefox uses 100% cpu it's caused by firefox. 
Why would the kernel programers decide "python is not important, it will get low priority", "java is not important, it should get low priority" but "firefox and mplayer are very important and should be allowed as much cpu time as they request"???
Python is not a "background process", it's a programming language and also the name of the binary that runs programs that are written in python, so everytime you run a program that is written in python, it will show up in top as "python", same as when you run a java application it will show up as "java".
If you think python using 100% cpu is a bug, then have a look at which programs python is running at the moment:```
ps aux | grep python
```

---

### Post by QIII on 2009-07-29
Not hung up on vino.

But you would be surprised how many times I answer people who are having 100% CPU usage and find out that they do, in fact, have vino running.

It is not the only possible problem.  It is simply one that is easy to eliminate as a culprit.

---

