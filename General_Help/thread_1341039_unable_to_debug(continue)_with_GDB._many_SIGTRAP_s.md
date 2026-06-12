---
title: "unable to debug(continue) with GDB. many SIGTRAP signals."
date: 2009-11-29
forum: General Help
---

### Post by stingx on 2009-11-29
Problem description:
Unable to continue debugging application when stopped by the signal.
GDB catch SIGTRAP signal when instructed to "continue" execution. This problem arises, when stepped in signal handler when application receives signal.

For example this source(test.c):
```

#include <stdlib.h>
#include <signal.h>

void sig_capture() {
	puts("In signal handler");
}

int main() {
	puts("In main");
	
	struct sigaction sa;
	sa.sa_handler = sig_capture;
	sigemptyset(&(sa.sa_mask));
	sa.sa_flags = SA_RESTART;
	sigaction(SIGHUP, &sa, NULL);

	sleep(1000);
	return 1;
}

```
compiled with command:
$ gcc -g test.cpp -o test

Run under gdb:
$ gdb ./test

In another terminal run:
$ killall -SIGHUP test
```

Gdb, as expected, break program execution on signal caught:
GNU gdb 7.0-debian
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i686-pc-linux-gnu"...
(gdb) run
Starting program: /home/testuser/Projects/test 
In main

Program received signal SIGHUP, Hangup.
0x00bf4422 in __kernel_vsyscall ()
(gdb)

```

Call 2 times "next":
```

(gdb) next
Single stepping until exit from function __kernel_vsyscall, 
which has no line number information.
sig_capture () at test.c:4
4	void sig_capture() {
(gdb) next
5		puts("In signal handler");
(gdb)

```
Everything antil now is ok, but then if I want to continue execution strange things happened:
```

(gdb) continue 
Continuing.

Program received signal SIGTRAP, Trace/breakpoint trap.
0x08048491 in sig_capture () at test.c:5
5		puts("In signal handler");
(gdb) continue
Continuing.

Program received signal SIGTRAP, Trace/breakpoint trap.
0x080483c0 in puts@plt ()
(gdb) continue
Continuing.

Program received signal SIGTRAP, Trace/breakpoint trap.
_IO_puts (str=0x80485d0 "In signal handler") at ioputs.c:34
34	ioputs.c: No such file or directory.
	in ioputs.c
(gdb) quit
The program is running.  Exit anyway? (y or n) y

```

I've searched google for this bug and I found same problems in old kernel releases: suddenly SIGTRAP handling were broken. That bug were fixed, but i think partially. E.g. earlier, this bug arises on ALL application breaks (inluding breakpoints), as for now it arises only in signal handling functions.

---

