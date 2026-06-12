---
title: "Process Explorer? Task Manager? Top?"
date: 2010-01-31
forum: General Help
---

### Post by aaronchall on 2010-01-31
Is there some kind of program that works like Windows Process Explorer? (It's a sort of souped up and more useful version of Windows Task Manager, created by a company called Sysinternals which was bought by Microsoft who now offers the program for free.)

I ask because sometimes Firefox locks up, and only a reboot will allow me to open it again, mainly because I'm not familiar enough with the command line to hunt down the program and kill it (though a program like process explorer that identifies all of the processes that are running and tells me about each of them would be nice.)

I'm aware of "top" but I'm not sure I can identify a process that's not responding, how do I kill it and restart it?  

Aaron

---

### Post by todak on 2010-01-31
If you know for a fact that firefox is locked up tight, then open a terminal and type this: ```
killall firefox
```.

---

### Post by NightwishFan on 2010-01-31
If you are using a commandline, try:
```
kill PROCCESSNUMBER
```
or
```
killall PROCESSNAME
```

For GUI:

gnome-system-monitor (System -> Administration -> System Monitor) installed by default.

I am sure there are more.

---

### Post by Jose Catre-Vandis on 2010-01-31
htop

---

### Post by jwbrase on 2010-01-31
You can go to System > Administration > System Monitor, then to the processes tab, right click on the offending process, and click "End process". If that doesn't work, right click again, and click on "Kill process".

You can also do the following at the command line:

```
ps -A | grep programname
```

This will return something like the following:

```
username@computername:~$ ps -A | grep opera
 4784 ?        00:00:48 opera
 4955 ?        00:00:07 operapluginwrap
 4956 ?        00:00:00 operapluginclea

```

You can then type:

```
kill -15 number
```

To "ask nicely".

Or:

```
kill -9 number
```

To force the process to end.

With "number" being the number to the left of the name of the process you want to kill, which would be 4784 if I wanted to kill Opera.

---

