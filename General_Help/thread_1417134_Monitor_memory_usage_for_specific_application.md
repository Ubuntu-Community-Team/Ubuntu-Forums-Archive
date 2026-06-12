---
title: "Monitor memory usage for specific application"
date: 2010-02-26
forum: General Help
---

### Post by yavoh on 2010-02-26
There's a [problem]("http://forum.videolan.org/viewtopic.php?f=13&t=67478&sid=2cbca9275bbc539225cc989e0f386824") with VLC on Karmic that occasionally causes high memory usage, locking up the machine.  Right now there's no known fix.

I love VLC.  Does anyone know of an application (or a method) to monitor the RAM usage of a particular program and then kill -9 it if it gets beyond a certain point?

Reasoning: sometimes I don't notice that VLC has started chewing up memory and I'm forced to do a hard reset.  I'd rather avoid this.

---

### Post by Ozymandias_117 on 2010-02-26
I don't know of a program... But you can go to System -> Preferences -> Keyboard click the Layouts tab, select Layout options and find "Key sequence to kill the X server"... then you can use ctrl alt bkspace to kill X... At least save you from a complete reboot.

---

### Post by yavoh on 2010-02-26
By the time I notice the leak, the system is completely frozen and doesn't respond to any commands, let alone an x restart.

---

### Post by jswoods7 on 2010-02-26
How about run a bash script in cron? This is ugly but you'll get the idea:

```

max_mem="10" ### 10 percent
process=`ps -ef | grep -v $$ | grep vlc | head -1 | awk '{ print $2 }'`

if [ `ps -o pmem $process | tail -1 | cut -d '.' -f1` -gt "$max_mem" ]; then
    echo "Memory usage too high, killing process $process"
    kill -9 $process
fi
```

---

