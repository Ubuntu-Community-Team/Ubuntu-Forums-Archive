---
title: "taskset doesn't always work?"
date: 2010-02-20
forum: General Help
---

### Post by lwi on 2010-02-20
I have a program for which it seems to be impossible to set cpu affinity from launch with the command taskset -c <cpu list> <command> <arguments>

It seems to work fine with xclock:

```

[COLOR="Gray"]vision@ackbar:~$[/COLOR] taskset -c 0,1 xclock -digital &
[1] 15997
[COLOR="Gray"]vision@ackbar:~$[/COLOR] taskset -pc $!
pid 15997's current affinity list: 0,1

```

but when I try it with my own program, it launches correctly but the cpu affinity is not set like I want it to.

I can however set it afterwards using it's PID:

```

[COLOR="Gray"]vision@ackbar:~$[/COLOR] taskset -c 0,1 ltplayerlua < /dev/null >&/dev/null &
[2] 16170
[COLOR="Gray"]vision@ackbar:~$[/COLOR] taskset -pc $!
pid 16170's current affinity list: 0
[COLOR="Gray"]vision@ackbar:~$[/COLOR] taskset -pc 0,1 16170
pid 16170's current affinity list: 0
pid 16170's new affinity list: 0,1
[COLOR="Gray"]vision@ackbar:~$[/COLOR] taskset -pc 16170
pid 16170's current affinity list: 0,1

```

.. it works but I find it very annoying that I can't set it right from the start.

any ideas?

thanks in advance,

Lwi

---

### Post by lwi on 2010-02-21
I hate to do this but... *boomp* :frown:

---

