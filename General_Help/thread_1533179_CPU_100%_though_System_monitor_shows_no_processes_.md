---
title: "CPU 100% though System monitor shows no processes running"
date: 2010-07-17
forum: General Help
---

### Post by wpalumbo on 2010-07-17
Ran the most recent updates several days ago and now System Monitor show my CPU at %100 constantly although it shows no processes running.

Any ideas?

---

### Post by Bradj47 on 2010-07-17
> **wpalumbo said:**
> Ran the most recent updates several days ago and now System Monitor show my CPU at %100 constantly although it shows no processes running.

Any ideas?

How can there be no processes running? Are you sure you're looking in the right place? There should be processes listed in the 'Processes' tab. If not, hopefully it's just a bug with System Monitor. Open a terminal and type 'top' to see a list of processes using the most of your computer's resources. If you want a whole list, type 'ps -ef'. Both of those commands display process ID's (PID). Retrieve the PID then type 'kill <PID>' to kill the process.

---

### Post by yetiman64 on 2010-07-17
If you use "top" in terminal just remember to quit it use the letter q, before closing terminal.

Also in system monitor goto view and select "all processes" as some system processes don't show by default (your problem process _may_ show up then).

---

### Post by wpalumbo on 2010-07-18
To clarify: Upon open sys mon, the CPU load for all displayed process was 0%, my statement 'it showed no processes running.'

After selecting 'showall' the culprit appeared to be 'polkitd'  

I tried sudo kill polkitd and got an error message ERROR: garbage process ID 'polkitd'

---

### Post by McRat on 2010-07-18
I have a Compaq Presario that shows 100% all the time.  Since the machine is running sweet, I'd assume that the System Monitor doesn't work on all systems.

---

### Post by wpalumbo on 2010-07-18
So is there* anyone *out there that can tell me *anything* about this?

What is this process? What does it do?  What is it affected by? Why can't it be shut down.  Why would this process start right after an update?

Anyone?

---

### Post by chriswyatt on 2010-07-18
If you want to kill it you need to do:

```
sudo killall polkitd
```

It's Policy Kit Daemon, I just found this thread which might be of help:

[http://ubuntuforums.org/showthread.php?t=1466794](http://ubuntuforums.org/showthread.php?t=1466794)

In this thread they mention it's an important part of the system and that killing it is probably not a good idea.

---

### Post by McRat on 2010-07-18
> **wpalumbo said:**
> So is there* anyone *out there that can tell me *anything* about this?

What is this process? What does it do?  What is it affected by? Why can't it be shut down.  Why would this process start right after an update?

Anyone?

I looked it up on Google, and it's a service used by the Hardware Abstract Layer to allow hardware device drivers to get higher permissions to do their assigned tasks best I can figure. 

More info is at hal.freedesktop.org

---

### Post by McRat on 2010-07-18
After more reading, the bug is actually caused by pulseaudio, and people have reported fixing it by:

[http://ubuntuforums.org/showpost.php?p=9227332&postcount=23](http://ubuntuforums.org/showpost.php?p=9227332&postcount=23)

---

### Post by wpalumbo on 2010-07-18
sudo killall doesn't kill the process - or, more correctly I think, it may kill it, but the process immediately respawns.

I was able to right click on the process and select 'Stop' which did indeed stop it.  CPU usage immediately went back to normal and there was no more runaway memory creep.

So I have made the machine usable but it is not fixed.  I still don't know what is broken or why and I have to manually stop the process every time I boot.

Stilll looking for an explanation of why/what is broken and how to effect a real fix.

---

### Post by McRat on 2010-07-18
See post above yours for fix.

---

### Post by wpalumbo on 2010-07-18
If  you do the following in exactly this order it returns the system to normal

1. poilkitd stop process
2. delete .dbus
3. delete .pulse

However, everytime you reboot you are right back to square one and have to do it all over again.

The link for deleting .dbus doesn't fix the problem as everything respawns upon reboot.

---

