---
title: "how to benchmark a process"
date: 2010-03-21
forum: General Help
---

### Post by jero3n on 2010-03-21
I want to measure how CPU time was spent (user, system, i/o waits) for a process or the whole system totally in some period of time, (not in realtime intervals and ignoring idle time)

Is there a way to do this in linux?

---

### Post by huygens on 2010-03-21
In the command line, you can find out this but it will give you the answer once the application close. So, it is not really suitable for application with graphical user interface.

To use the command line tool, just type:
time my_program
And replace my_program by the path to your application.

Depending on your settings, you could get a result like this:
0.00user 0.00system 0:00.00elapsed 66%CPU (0avgtext+0avgdata 0maxresident)k
0inputs+0outputs (0major+287minor)pagefaults 0swaps

If you are familiar with man pages, you can use:
man time
To get more information from the time command.


Other commands, but you have to fiddle a bit to extract the informations, are:
[LIST]
[*]iotop ([apt:iotop]("apt:iotop"))
[*]sar ([apt:sysstat]("apt:sysstat"))
[*]vmstat (included by default in Ubuntu)
[*]iostat (included by default in Ubuntu)
[/LIST]

They will give you either global or per process information about IO, CPU load, etc.

---

### Post by jero3n on 2010-03-21
Very useful info. Thanks

---

