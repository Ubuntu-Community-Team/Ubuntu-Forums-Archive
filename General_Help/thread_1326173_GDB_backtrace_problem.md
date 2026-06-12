---
title: "GDB backtrace problem"
date: 2009-11-14
forum: General Help
---

### Post by kongstad on 2009-11-14
Hi

I am filling out a bug report for gnome-panel

I have to supply a backtrace from when the process hangs. 
I am following the instructions on
[http://wiki.ubuntu.com/Backtrace](http://wiki.ubuntu.com/Backtrace)

GDB is run from tty1, since X freezes up along with gnome panel. so I ctrl-alt-1 into tty1 and enter
gdb 2>&1 | tee gdb-gnome-panel.txt
(gdb) handle SIG33 pass nostop noprint
(gdb) set pagination 0
(gdb) attach <PID>
(gdb) continue
Where PID is the PID for gnome-panel


Then i alt-7 into Xorg and coax gnome-panel to hang.

Xorg then stops respongind, and gnome panel hogs the CPU, and starts eating memory.

 Then I ctrl-alt-1 into tty1 and press ctrl-c to send stop to gnome-panel through gdb, but the only thing that happens is that CTRL-C is printed on the screen.

If I kill the gnome-panel process from another terminal, GDB is still hung.

What am I doing wrong? 

Is my best bet to make gnome-panel hang, and then kill it, forcing it to core-dump, and the try to get a back-trace from the core dump?

---

