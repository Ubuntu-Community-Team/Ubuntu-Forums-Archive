---
title: "Shutdown/Restart doesn't do anything in 9.10"
date: 2010-02-19
forum: General Help
---

### Post by gohmifune on 2010-02-19
I'm in 9.10, I had KDE 4.3 now with SC 4.4, and it doesn't reboot or shut down from any graphical way I can access. Power management works otherwise, and I can shut down from the command line.

Any help working through this would be great, Google has been useless for me.

---

### Post by rnerwein on 2010-02-19
hi
i don't know this will help you, but i will tell you how i will figure out what's going on.
i hope you are confirm whit shell commands. 
i will suggest that you select shutdow/restart your window manager will get a messages or signal.
now i will try to figure out what's the reaction of it. here is my currently running system.
i'am running gnome !
1. open a terminal
2. ps -ef | grep gdm
root      2040     1  0 09:58 ?        00:00:00 gdm-binary
root      2047  2040  0 09:58 ?        00:00:00 /usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManager/Display1
root      2048  2047  1 09:58 tty7     00:00:29 /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-jIMm0l/database -nolisten tcp vt7
gdm       2085     1  0 09:58 ?        00:00:00 /usr/bin/dbus-launch --exit-with-session
root      2136  2047  0 09:58 ?        00:00:00 /usr/lib/gdm/gdm-session-worker

first i will try now to trace the last process in the chain - that is PID 2136
you must be root to trace this process ( sudo /bin/bash ) and quit the trace with CTRL C
strace -f -o bla -p 2136
(-f follow childs, -o bla is the output file)
have a look in bla ( it's a ascii file)
if i can't figure out what's the reaction is i will trace the next process in the chain.
strace -f -o blu -p 2048 
and so on.
max be this help you. 
....
ciao

---

### Post by 002244 on 2010-02-25
> **gohmifune said:**
> I'm in 9.10, I had KDE 4.3 now with SC 4.4, and it doesn't reboot or shut down from any graphical way I can access. Power management works otherwise, and I can shut down from the command line.

Any help working through this would be great, Google has been useless for me.

I confirm some problems here too: my laptop hangs for a while when Shutdown/Reboot actions selected from Kickoff Application Launcher and nothing happens after that.

Fortunately, I got it working via context menu on a blank screen.

Any help is appreciated.

---

### Post by shid007 on 2010-04-05
I have the same problem... logging out doesn't work either :(

I've found out that it's probably KNotify bug mentioned here [http://osdir.com/ml/kde-bugs-dist/2009-08/msg02999.html]("http://osdir.com/ml/kde-bugs-dist/2009-08/msg02999.html") - I turned off sound notifications and now I can shutdown/reboot/logoff yeeey!

---

### Post by aaronwinborn on 2010-07-27
Same issue here. Turning off the play sound for logging off doesn't help either.

---

### Post by aaronwinborn on 2010-07-27
note that this is in 10.04.1

---

### Post by jonny90046 on 2010-08-05
I'm having the same problem in KDE on 10.04 after an upgrade two days ago.....the work-around referenced doesn't work for me, either. If I find or discover a solution, I will post it asap. If anyone else finds a solution, please, do the same.  Thanks

---

