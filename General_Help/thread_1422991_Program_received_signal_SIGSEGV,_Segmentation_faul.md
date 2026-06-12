---
title: "Program received signal SIGSEGV, Segmentation fault"
date: 2010-03-06
forum: General Help
---

### Post by DoSoo on 2010-03-06
Dear All,
I'm debugging some C++ code, but as I know very little about it, I can't find the problem!
Need some Help Please!
Here the debugging output:
> rihab@rihab-laptop:~/ns-test$ gdb ns
(gdb) run /home/rihab/ns-allinone-2.34/ns-2.34/OWNS/demos/owns_demo.tcl
Starting program: /usr/local/bin/ns /home/rihab/ns-allinone-2.34/ns-2.34/OWNS/demos/owns_demo.tcl
type random, seed 99
nodes 7, scale 7,  method pure-random
conn prob 0.4, beta  0.5, gamma 0.5
Creating WDMNodes...
Creating links 0...
Program received signal SIGSEGV, Segmentation fault.
0x08345248 in WDMAgent::sendmsg(int, char const*) ()
(gdb) info s
#0  0x08345248 in WDMAgent::sendmsg(int, char const*) ()
#1  0x0833fc11 in EXPOO_SessionTraffic::timeout() ()
#2  0x0833ea44 in SessionTrafficTimer::expire(Event*) ()
#3  0x0816444d in TimerHandler::handle(Event*) ()
#4  0x0816607c in Scheduler::dispatch(Event*, double) ()
#5  0x081662ca in Scheduler::run() ()
#6  0x08166581 in Scheduler::command(int, char const* const*) ()
#7  0x08345aba in TclClass::dispatch_cmd(void*, Tcl_Interp*, int, char const**)
    ()
#8  0x0834a84e in OTclDispatch (cd=0x86fc218, in=0x8526520, argc=3, 
    argv=0xbfffd59c) at otcl.c:434
#9  0x0834f44e in TclInvokeStringCommand ()
#10 0x0835108e in TclEvalObjvInternal ()
#11 0x0837be5d in TclExecuteByteCode ()
#12 0x08381405 in TclCompEvalObj ()
#13 0x0837bd00 in TclExecuteByteCode ()
#14 0x08381405 in TclCompEvalObj ()
#15 0x083ab925 in TclObjInterpProc ()
#16 0x083abdc3 in TclProcInterpProc ()
#17 0x0834aa4e in OTclDispatch (cd=0x853e248, in=0x8526520, argc=2, 
    argv=0xbfffe21c) at otcl.c:477
#18 0x0834f44e in TclInvokeStringCommand ()
#19 0x0835108e in TclEvalObjvInternal ()
---Type <return> to continue, or q <return> to quit---
#20 0x0837be5d in TclExecuteByteCode ()
#21 0x08381405 in TclCompEvalObj ()
#22 0x083ab925 in TclObjInterpProc ()
#23 0x083abdc3 in TclProcInterpProc ()
#24 0x0834a84e in OTclDispatch (cd=0x86d8fe0, in=0x8526520, argc=2, 
    argv=0xbfffebac) at otcl.c:434
#25 0x0834f44e in TclInvokeStringCommand ()
#26 0x0835108e in TclEvalObjvInternal ()
#27 0x08351d32 in Tcl_EvalEx ()
#28 0x0839a90f in Tcl_FSEvalFile ()
#29 0x0839dfac in Tcl_Main ()
#30 0x083457b4 in nslibmain ()
#31 0x08345812 in main ()Can any one help Me! 
I would be very grateful!

---

### Post by Intrepid Ibex on 2010-03-06
> ...
Program received signal SIGSEGV, Segmentation fault.
...
Is some dependency corrupted (or possibly the app itself)?

---

