---
title: "segfault+glGetError () from /usr/lib/libGL.so.1"
date: 2010-01-22
forum: General Help
---

### Post by srinivas2828 on 2010-01-22
I am getting error while i am running python program here is the detailed information about the error and i found many links from internet but i couldn't found any solution please help me guys btw i am using ubuntu8.10 32 bit operating system
```

root@VAIO:/home/miriyala# gdb python
GNU gdb 6.8-debian
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...
(gdb) run /home/miriyala/IIITH/mas_framework/mas_framework/apiclient.py 5050&
Asynchronous execution not supported on this target.
(gdb) run /home/miriyala/IIITH/mas_framework/examples/circle.py localhost:5050
Starting program: /usr/bin/python /home/miriyala/IIITH/mas_framework/examples/circle.py localhost:5050
[Thread debugging using libthread_db enabled]
[New Thread 0xb7e0a8c0 (LWP 9300)]
/usr/lib/python2.5/site-packages/OpenGL/platform/__init__.py:20: UserWarning: Module _mysql was already imported from /var/lib/python-support/python2.5/_mysql.so, but /var/lib/python-support/python2.5 is being added to sys.path
  import os, sys, pkg_resources
[New Thread 0xb6180b90 (LWP 9328)]
[Thread 0xb6180b90 (LWP 9328) exited]
bLaunchGUI:  True
[New Thread 0xb6180b90 (LWP 9329)]
[New Thread 0xb57c3b90 (LWP 9330)]
Starting Simulation
play has been clicked
True
starting sim
evStartSim set
[New Thread 0xb4f79b90 (LWP 9331)]
FT: 0.00204801559448 - 1
('TIMES:', '------------------------------')
0.04,0.01,0.00,1.04,0.60,
==================================================
FT: 0.00162792205811 - 2
('TIMES:', '------------------------------')
0.04,0.01,0.00,0.92,0.58,
==================================================
**ERROR**
======
**Program received signal SIGSEGV, Segmentation fault.**
[Switching to Thread 0xb4f79b90 (LWP 9331)]
**0xb644f156 in glGetError () from /usr/lib/libGL.so.1**
(gdb)** bt**
#0  0xb644f156 in glGetError () from /usr/lib/libGL.so.1
#1  0xb6566447 in ffi_call_SYSV ()
    at /build/buildd/python2.5-2.5.2/Modules/_ctypes/libffi/src/x86/sysv.S:60
#2  0xb65662c6 in ffi_call (cif=0xb4f78018, fn=0xb644f150 <glGetError>, 
    rvalue=0x0, avalue=0xb4f78090)
    at /build/buildd/python2.5-2.5.2/Modules/_ctypes/libffi/src/x86/ffi.c:221
#3  0xb6560dc4 in _CallProc (pProc=0xb644f150 <glGetError>, 
    argtuple=0xb7dca02c, flags=<value optimized out>, argtypes=0x0, 
    restype=0x90bb4cc, checker=0x0)
    at /build/buildd/python2.5-2.5.2/Modules/_ctypes/callproc.c:668
#4  0xb6559f69 in CFuncPtr_call (self=0xb647a91c, inargs=0xb7dca02c, kwds=0x0)
    at /build/buildd/python2.5-2.5.2/Modules/_ctypes/_ctypes.c:3363
#5  0x0805d867 in PyObject_Call (func=0xb4f78018, arg=0xb7dca02c, kw=0x0)
    at ../Objects/abstract.c:1861
#6  0x080cc8a7 in PyEval_EvalFrameEx (f=0xb4606cd4, throwflag=0)
    at ../Python/ceval.c:3806
#7  0x080d0345 in PyEval_EvalCodeEx (co=0xb6312d10, globals=0xb64919bc, 
    locals=0x0, args=0xb61dfdd0, argcount=4, kws=0x0, kwcount=0, 
    defs=0xb6317098, defcount=2, closure=0x0) at ../Python/ceval.c:2858
#8  0x08117891 in function_call (func=0xb64a26f4, arg=0xb61dfdc4, kw=0x0)
    at ../Objects/funcobject.c:517
#9  0x0805d867 in PyObject_Call (func=0xb4f78018, arg=0xb61dfdc4, kw=0x0)
    at ../Objects/abstract.c:1861
---Type <return> to continue, or q <return> to quit---
#10 0x08063a7a in instancemethod_call (func=0xb64a26f4, arg=0xb61dfdc4, kw=0x0)
    at ../Objects/classobject.c:2519
#11 0x08062646 in PyObject_CallFunctionObjArgs (callable=0xb64847fc)
    at ../Objects/abstract.c:1861
#12 0xb6559fa3 in CFuncPtr_call (self=0xb620ed94, inargs=0xb61920cc, kwds=0x0)
    at /build/buildd/python2.5-2.5.2/Modules/_ctypes/_ctypes.c:3379
#13 0x0805d867 in PyObject_Call (func=0xb4f78018, arg=0xb61920cc, kw=0x0)
    at ../Objects/abstract.c:1861
#14 0x080cc8a7 in PyEval_EvalFrameEx (f=0x933ac24, throwflag=0)
    at ../Python/ceval.c:3806
#15 0x080d0345 in PyEval_EvalCodeEx (co=0xb787dde8, globals=0xb78a546c, 
    locals=0x0, args=0xb61eab58, argcount=1, kws=0x93326c0, kwcount=0, 
    defs=0x0, defcount=0, closure=0x0) at ../Python/ceval.c:2858
#16 0x0811797e in function_call (func=0xb61d8b54, arg=0xb61eab4c, 
    kw=0xb61919bc) at ../Objects/funcobject.c:517
#17 0x0805d867 in PyObject_Call (func=0xb4f78018, arg=0xb61eab4c, 
    kw=0xb61919bc) at ../Objects/abstract.c:1861
#18 0x080cd502 in PyEval_EvalFrameEx (f=0x933aac4, throwflag=0)
    at ../Python/ceval.c:3875
#19 0x080cfbf5 in PyEval_EvalFrameEx (f=0x933a92c, throwflag=0)
    at ../Python/ceval.c:3681
#20 0x080cfbf5 in PyEval_EvalFrameEx (f=0x9333634, throwflag=0)
    at ../Python/ceval.c:3681
---Type <return> to continue, or q <return> to quit---
#21 0x080d0345 in PyEval_EvalCodeEx (co=0xb7d00ad0, globals=0xb7cfa934, 
    locals=0x0, args=0xb61ea278, argcount=1, kws=0x0, kwcount=0, defs=0x0, 
    defcount=0, closure=0x0) at ../Python/ceval.c:2858
#22 0x08117891 in function_call (func=0xb7d05f7c, arg=0xb61ea26c, kw=0x0)
    at ../Objects/funcobject.c:517
#23 0x0805d867 in PyObject_Call (func=0xb4f78018, arg=0xb61ea26c, kw=0x0)
    at ../Objects/abstract.c:1861
#24 0x08063a7a in instancemethod_call (func=0xb7d05f7c, arg=0xb61ea26c, kw=0x0)
    at ../Objects/classobject.c:2519
#25 0x0805d867 in PyObject_Call (func=0xb4f78018, arg=0xb7dca02c, kw=0x0)
    at ../Objects/abstract.c:1861
#26 0x080c850c in PyEval_CallObjectWithKeywords (func=0xb61e4234, 
    arg=0xb7dca02c, kw=0x0) at ../Python/ceval.c:3464
#27 0x080f9e68 in t_bootstrap (boot_raw=0x9314fb8)
    at ../Modules/threadmodule.c:427
#28 0xb7f9e50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#29 0xb7eeca0e in clone () from /lib/tls/i686/cmov/libc.so.6
(gdb) 

```
what am i suppose to do

---

### Post by srinivas2828 on 2010-01-22
after couple of hours i found somethig usefull
just install libgl1-mesa-swx11 package then worked fine for me

---

