---
title: "banshee grief SIGSEGV error"
date: 2009-11-25
forum: General Help
---

### Post by sdowney717 on 2009-11-25
any ideas. the program was running great. I went away for an hour, then its acting horribly. turns grey, plays videos in a separate window. crashing, running super slow. my pc is core 2 duo 3,5 ghz

> #93 0x00436ba2 in ?? ()
#94 0x00436b53 in ?? ()
#95 0x004360b2 in ?? ()
#96 0x00e1c3f9 in ?? ()
#97 0x00e1c1fa in ?? ()
#98 0x081112ae in mono_runtime_exec_main ()
#99 0x081134da in mono_runtime_run_main ()
#100 0x080b19bd in mono_main ()
#101 0x0805aba5 in ?? ()
#102 0x001b0b56 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#103 0x0805aae1 in ?? ()

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted


---

### Post by sdowney717 on 2009-11-25
i solved by deleting the folder banshee in .config
and redoing all the rss feeds. This time I made a backup copy of the folder.
the database sqlite3 got corrupted!

actually it got corrupted again
I suppose it is not ready for having 30 podcast rss feeds loaded. 
When the database goes bad, the cpu usage spikes to 100% and it overheats my cpu
for me not reliable program.
I am running the 1.5.1 version

---

