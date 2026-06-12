---
title: "enable/disable console-kit-daemon"
date: 2010-02-26
forum: General Help
---

### Post by asmith20002 on 2010-02-26
Hi.

I have this process when do 'top':


  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 2512 root      25   0  8552 1128  920 R   99  0.3 959:54.45 console-kit-dae

It is eating 95% of the CPU, I can kill the process I guess. But how can I disable/enable it anytime I want? 
I have /etc/init.d/consolekit-setup and /etc/init.d/console-screen.sh but:

sudo /etc/init.d/consolekit-setup stop OR /etc/init.d/console-screen.sh stop  does nothing. 
I want to be able to disable/enable it anytime I want.

How can I do it?
Thanks

---

### Post by iponeverything on 2010-02-26
console-kit should not consume that much cpu. 

If you provided relevant details like:

hardware and ubuntu version and when and what causes the situation to occur, perhaps someone where can provide you with a practical solution to you problem.

---

### Post by asmith20002 on 2010-02-26
The whole thing is my VPS service. It is ubuntu 8.04. My webserver is running on this ubuntu.

What this console is doing exactly? and what I will miss if I kill the process?

---

### Post by iponeverything on 2010-02-26
In my opinion, console-kit is not necessary on servers machines. If your running a gnome on the server, you might run into issues not having console-kit running.

For an explanation of console-kit see:  

[http://www.freedesktop.org/software/ConsoleKit/doc/ConsoleKit.html](http://www.freedesktop.org/software/ConsoleKit/doc/ConsoleKit.html)

This not the correct way to disable it, but it will work:

```
su mv /usr/sbin/console-kit-daemon /usr/sbin/console-kit-daemon.bkup

sudo cp /bin/true /usr/sbin/console-kit-daemon
```

and and reboot. 

Before you take this action you might consider making sure that your system is up to date with regard to the kernel, apache, console-kit and other services that server is delivering.

---

