---
title: "SPSS Keeps Crashing, Won't Run, Weird Java Crash Reports!"
date: 2009-07-09
forum: General Help
---

### Post by DaveyR on 2009-07-09
I have to use SPSS outputs for University work (they are inflexible on this and I'm not too keen on 'R') and bought myself an Linux copy of the program. I have SPSS 16.

After disabling compiz, I managed to install it without any hassle. However the program refuses to start. I go to the directory (in my "Home" folder) type in ./SPSS, the loading screen pops up and I get this sort of output:

[b]#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xe9000000, pid=11875, tid=3327105936
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_11-b03 mixed mode)
# Problematic frame:
# C  0xe9000000
#
# An error report file with more information is saved as hs_err_pid11875.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted[/b]

I installed, reinstalled it. I tried ./spss as well as double clicking on the run files. Submitted the error to Sun, tried it over a hundred times and I get slightly different error messages.

I've googled the error and I can't find any help.

I'm using Ubuntu 9.04 64-bit, java 1.6.0_13-b03 and Java HotSpot 64-bit Server VM build 11.3-b02 mixed mode (I don't understand any of this) if that's any help.

Thanks! And I've would have submitted the full error report, but it's too big to attach, plus it looks like mostly gibberish!

---

### Post by DaveyR on 2009-07-10
OK, here is just one of the many full crash report that SPSS has generated:

[b]#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0x00001704, pid=4578, tid=3342310288
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_11-b03 mixed mode)
# Problematic frame:
# C  0x00001704
#

---------------  T H R E A D  ---------------

Current thread is native thread

siginfo:si_signo=11, si_errno=0, si_code=1, si_addr=0x00001704

Registers:
EAX=0x00000002, EBX=0xc2002065, ECX=0x00000004, EDX=0x00000000
ESP=0xc73777b4, EBP=0xc73777c0, ESI=0x00000002, EDI=0x00000000
EIP=0x00001704, CR2=0x00001704, EFLAGS=0x00010246

Top of Stack: (sp=0xc73777b4)
0xc73777b4:   c2351604 c2554d8c c2554d30 c73777cc
0xc73777c4:   c23515d2 c2554d8c c73777dc c247cce6
0xc73777d4:   f7fddff4 0a1c7bd8 c73777ec c230ef71
0xc73777e4:   f7cfd8e8 09691f73 c737783c f7fce77d
0xc73777f4:   00000001 ffadc644 09f19898 00000000
0xc7377804:   f7fd9da0 ffadc644 00000001 0a1c7960
0xc7377814:   00000000 0000000f f7b025f5 f7fd29e1
0xc7377824:   00000040 0000003c f7fce68b f7fddff4 

Instructions: (pc=0x00001704)
0x000016f4:   
[error occurred during error reporting, step 100, id 0xb]

Stack: [0xc6b79000,0xc737a000),  sp=0xc73777b4,  free space=8185k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  0x00001704
C  [libspsswlib.so+0x7f5d2]
C  [libspsswlib.so+0x1aace6]
C  [libspsswlib.so+0x3cf71]
C  [ld-linux.so.2+0x1077d]
C  [ld-linux.so.2+0x14e62]
C  [ld-linux.so.2+0x10346]
C  [ld-linux.so.2+0x144ee]
C  [libdl.so.2+0xbec]
C  [ld-linux.so.2+0x10346]
C  [libdl.so.2+0x101c]
C  [libdl.so.2+0xb21]  dlopen+0x41
C  [libplatdep.so+0x21c8a]  _ZN20DynamicLoadedLibrary14LoadLibraryNowEv+0x6c
C  [libserver.so+0x2f434]  _ZN11RegDatabase13ModuleManager10ModuleDataC9EPKc+0xe6
C  [libserver.so+0x2f344]  _ZN11RegDatabase13ModuleManager10ModuleDataC1EPKc+0x1e
C  [libserver.so+0x2f0f0]  _ZN11RegDatabase13ModuleManager14GetClassObjectERK5_GUIDS3_PPvsP6IRegDB+0x1a6
C  [libserver.so+0x2eec0]  _ZN11RegDatabase17CreateClassObjectERK5_GUIDsS2_PP8IUnknown+0x5e
C  [libserver.so+0x43cdf]  _ZN7Session17InstantiateObjectERK15VPackageRequestR10VProxyInfob+0x215
C  [libserver.so+0x215e5]  _ZN14DefaultPackage17OnCallSynchronousEtRK13VSerializableRS0_+0x357
C  [libnetcom.so+0x1bb9d]  _ZN5Proxy16ProcessCallProt1ER10DataBuffer+0x1f1
C  [libnetcom.so+0x1b8ef]  _ZN5Proxy11ReceiveCallER10DataBuffer+0xaf
C  [libserver.so+0x42674]  _ZN7Session11ReceiveCallER10DataBufferP9ThreadHot+0x13e
C  [libnetcom.so+0x1ef42]  _ZN6Router8TransactER10DataBufferP9ThreadHot+0x20
C  [libnetcom.so+0x223f4]  _ZN14ServiceRequest7ExecuteEP9ThreadHot+0x92
C  [libserver.so+0x4ef91]  _ZN10ThreadPool14ProcessRequestERP14ServiceRequestPNS_10PoolThreadE+0x71
C  [libserver.so+0x4e91c]  _ZN10ThreadPool11ThreadEntryEPNS_10PoolThreadE+0x9c
C  [libserver.so+0x5054f]  _ZN10ThreadPool10PoolThread3RunEv+0x17
C  [libplatdep.so+0x2dbf3]  _ZN9ThreadHot5EntryEv+0x15
C  [libserver.so+0x50582]  _ZN10ThreadPool10PoolThread5EntryEv+0x24
C  [libplatdep.so+0x2db1a]  _Z9EntryFuncPv+0x52
C  [libpthread.so.0+0x64ff]


---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
  0xc9ca3438 JavaThread "MsgReceiverThread" [_thread_blocked, id=4679]
  0xc9ca27e0 JavaThread "DataWriteThread" [_thread_blocked, id=4678]
  0xc9ca6530 JavaThread "DataReadThread" [_thread_in_native, id=4677]
  0x09f3a988 JavaThread "WaitCursor Thread" daemon [_thread_blocked, id=4667]
  0x09fc8f50 JavaThread "TimerQueue" daemon [_thread_blocked, id=4666]
  0xcb2153d0 JavaThread "XML-RPC Weblistener" [_thread_in_native, id=4665]
  0x0a086760 JavaThread "AWT-EventQueue-0" [_thread_blocked, id=4591]
  0x09fdb6b0 JavaThread "AWT-Shutdown" [_thread_blocked, id=4590]
  0x0a4627b8 JavaThread "Image Fetcher 3" daemon [_thread_blocked, id=4589]
  0x0a504ed0 JavaThread "Timer-0" daemon [_thread_blocked, id=4588]
  0x0a4f6e90 JavaThread "AWT-XAWT" daemon [_thread_in_native, id=4587]
  0x0a4e45d0 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=4586]
  0x09f23db0 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=4584]
  0x09f228a0 JavaThread "CompilerThread0" daemon [_thread_blocked, id=4583]
  0x09f21900 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=4582]
  0x09f18508 JavaThread "Finalizer" daemon [_thread_blocked, id=4581]
  0x09f166f8 JavaThread "Reference Handler" daemon [_thread_blocked, id=4580]
  0x09eb77c8 JavaThread "main" [_thread_blocked, id=4578]

Other Threads:
  0x09f139e8 VMThread [id=4579]
  0x09f25378 WatcherThread [id=4585]

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 def new generation   total 1024K, used 611K [0xce140000, 0xce250000, 0xd08a0000)
  eden space 960K,  62% used [0xce140000, 0xce1d5fa8, 0xce230000)
  from space 64K,  18% used [0xce240000, 0xce242fe8, 0xce250000)
  to   space 64K,   0% used [0xce230000, 0xce230000, 0xce240000)
 tenured generation   total 12844K, used 10988K [0xd08a0000, 0xd152b000, 0xee140000)
   the space 12844K,  85% used [0xd08a0000, 0xd135b170, 0xd135b200, 0xd152b000)
 compacting perm gen  total 17664K, used 17478K [0xee140000, 0xef280000, 0xf2140000)
   the space 17664K,  98% used [0xee140000, 0xef251b38, 0xef251c00, 0xef280000)
No shared spaces configured.

Dynamic libraries:
08048000-08053000 r-xp 00000000 08:06 2549447                            /home/dave/Documents/Statistics/SPSS/bin/SPSS
08053000-08057000 rw-p 0000a000 08:06 2549447                            /home/dave/Documents/Statistics/SPSS/bin/SPSS
09e8f000-0a54f000 rw-p 09e8f000 00:00 0                                  [heap]
c1244000-c1248000 r-xp 00000000 08:06 2580849                            /home/dave/Documents/Statistics/SPSS/lib/libomxspv.so.1
c1248000-c124a000 rw-p 00004000 08:06 2580849                            /home/dave/Documents/Statistics/SPSS/lib/libomxspv.so.1
c124a000-c1262000 r-xp 00000000 08:06 2580645                            /home/dave/Documents/Statistics/SPSS/lib/libomxtext.so.1
c1262000-c1269000 rw-p 00018000 08:06 2580645                            /home/dave/Documents/Statistics/SPSS/lib/libomxtext.so.1
c1269000-c127e000 r-xp 00000000 08:06 2580817                            /home/dave/Documents/Statistics/SPSS/lib/libomxhtml.so.1
c127e000-c1286000 rw-p 00014000 08:06 2580817                            /home/dave/Documents/Statistics/SPSS/lib/libomxhtml.so.1
c1286000-c1293000 r-xp 00000000 08:06 2580696                            /home/dave/Documents/Statistics/SPSS/lib/libomxsav.so.1
c1293000-c1297000 rw-p 0000c000 08:06 2580696                            /home/dave/Documents/Statistics/SPSS/lib/libomxsav.so.1
c1297000-c12ca000 r-xp 00000000 08:06 2580783                            /home/dave/Documents/Statistics/SPSS/lib/libomxxml.so.1
c12ca000-c12d9000 rw-p 00032000 08:06 2580783                            /home/dave/Documents/Statistics/SPSS/lib/libomxxml.so.1
c12d9000-c12f6000 r-xp 00000000 08:06 2580962                            /home/dave/Documents/Statistics/SPSS/lib/libomtree.so.1
c12f6000-c12ff000 rw-p 0001c000 08:06 2580962                            /home/dave/Documents/Statistics/SPSS/lib/libomtree.so.1
c12ff000-c133d000 r-xp 00000000 08:06 2580709                            /home/dave/Documents/Statistics/SPSS/lib/libomfactry.so.1
c133d000-c134d000 rw-p 0003d000 08:06 2580709                            /home/dave/Documents/Statistics/SPSS/lib/libomfactry.so.1
c134d000-c135f000 r-xp 00000000 08:06 2580876                            /home/dave/Documents/Statistics/SPSS/lib/libomcell.so.1
c135f000-c1366000 rw-p 00011000 08:06 2580876                            /home/dave/Documents/Statistics/SPSS/lib/libomcell.so.1
c1366000-c136d000 r-xp 00000000 08:06 2580701                            /home/dave/Documents/Statistics/SPSS/lib/libstrtable.so.1
c136d000-c1370000 rw-p 00006000 08:06 2580701                            /home/dave/Documents/Statistics/SPSS/lib/libstrtable.so.1
c1370000-c138c000 r-xp 00000000 08:06 2580852                            /home/dave/Documents/Statistics/SPSS/lib/libomsopmgr.so.1
c138c000-c1395000 rw-p 0001c000 08:06 2580852                            /home/dave/Documents/Statistics/SPSS/lib/libomsopmgr.so.1
c1395000-c13f8000 r-xp 00000000 08:06 2581030                            /home/dave/Documents/Statistics/SPSS/lib/libviewerxml.so.1
c13f8000-c1413000 rw-p 00063000 08:06 2581030                            /home/dave/Documents/Statistics/SPSS/lib/libviewerxml.so.1
c1413000-c1426000 r-xp 00000000 08:06 2581095                            /home/dave/Documents/Statistics/SPSS/lib/libspssdx.so.1
c1426000-c142c000 rw-p 00013000 08:06 2581095                            /home/dave/Documents/Statistics/SPSS/lib/libspssdx.so.1
c142c000-c1597000 r-xp 00000000 08:06 2580879                            /home/dave/Documents/Statistics/SPSS/lib/libspssxd.so.1
c1597000-c15d7000 rw-p 0016a000 08:06 2580879                            /home/dave/Documents/Statistics/SPSS/lib/libspssxd.so.1
c15d7000-c15f3000 rw-p c15d7000 00:00 0 
c15f3000-c1673000 r-xp 00000000 08:06 2580922                            /home/dave/Documents/Statistics/SPSS/lib/libuparser.so.1
c1673000-c169c000 rw-p 00080000 08:06 2580922                            /home/dave/Documents/Statistics/SPSS/lib/libuparser.so.1
c169c000-c16da000 r-xp 00000000 08:06 2580940                            /home/dave/Documents/Statistics/SPSS/lib/libcpputil.so.1
c16da000-c16f1000 rw-p 0003d000 08:06 2580940                            /home/dave/Documents/Statistics/SPSS/lib/libcpputil.so.1
c16f1000-c16fe000 r-xp 00000000 08:06 2581005                            /home/dave/Documents/Statistics/SPSS/lib/libindutil.so.1
c16fe000-c1702000 rw-p 0000c000 08:06 2581005                            /home/dave/Documents/Statistics/SPSS/lib/libindutil.so.1
c1702000-c1708000 r-xp 00000000 08:06 2580896                            /home/dave/Documents/Statistics/SPSS/lib/libxalanMsg.so.19.0
c1708000-c1709000 rw-p 00006000 08:06 2580896                            /home/dave/Documents/Statistics/SPSS/lib/libxalanMsg.so.19.0
c1709000-c1b7b000 r-xp 00000000 08:06 2580792                            /home/dave/Documents/Statistics/SPSS/lib/libxalan-c.so.19.0
c1b7b000-c1caf000 rw-p 00471000 08:06 2580792                            /home/dave/Documents/Statistics/SPSS/lib/libxalan-c.so.19.0
c1caf000-c1cb0000 rw-p c1caf000 00:00 0 
c1cb0000-c1d98000 r-xp 00000000 08:06 2581032                            /home/dave/Documents/Statistics/SPSS/lib/libchartutl.so.1
c1d98000-c1de7000 rw-p 000e7000 08:06 2581032                            /home/dave/Documents/Statistics/SPSS/lib/libchartutl.so.1
c1de7000-c1fc6000 r-xp 00000000 08:06 2580847                            /home/dave/Documents/Statistics/SPSS/lib/libvizchart.so.1
c1fc6000-c2075000 rw-p 001df000 08:06 2580847                            /home/dave/Documents/Statistics/SPSS/lib/libvizchart.so.1
c2075000-c2078000 r-xp 00000000 08:06 2580764                            /home/dave/Documents/Statistics/SPSS/lib/libtmsutil.so.1
c2078000-c2079000 rw-p 00003000 08:06 2580764                            /home/dave/Documents/Statistics/SPSS/lib/libtmsutil.so.1
c2079000-c209e000 r-xp 00000000 08:06 2580654                            /home/dave/Documents/Statistics/SPSS/lib/libcvtrans.so.1
c209e000-c20a9000 rw-p 00024000 08:06 2580654                            /home/dave/Documents/Statistics/SPSS/lib/libcvtrans.so.1
c20a9000-c20aa000 r-xp 00000000 08:06 2580859                            /home/dave/Documents/Statistics/SPSS/lib/libreadonly.so.1
c20aa000-c20ab000 rw-p 00000000 08:06 2580859                            /home/dave/Documents/Statistics/SPSS/lib/libreadonly.so.1
c20ab000-c21d3000 r-xp 00000000 08:06 2580813                            /home/dave/Documents/Statistics/SPSS/lib/libspsswctl.so.1
c21d3000-c2235000 rw-p 00127000 08:06 2580813                            /home/dave/Documents/Statistics/SPSS/lib/libspsswctl.so.1
c2235000-c224f000 rw-p c2235000 00:00 0 
c224f000-c227b000 r-xp 00000000 08:06 2580799                            /home/dave/Documents/Statistics/SPSS/lib/libtransspc.so.1
c227b000-c2289000 rw-p 0002c000 08:06 2580799                            /home/dave/Documents/Statistics/SPSS/lib/libtransspc.so.1
c2289000-c229d000 r-xp 00000000 08:06 2580905                            /home/dave/Documents/Statistics/SPSS/lib/libvizedit.so.1
c229d000-c22a6000 rw-p 00013000 08:06 2580905                            /home/dave/Documents/Statistics/SPSS/lib/libvizedit.so.1
c22a6000-c22af000 r-xp 00000000 08:06 2580956                            /home/dave/Documents/Statistics/SPSS/lib/libspssjvm.so.1
c22af000-c22b2000 rw-p 00008000 08:06 2580956                            /home/dave/Documents/Statistics/SPSS/lib/libspssjvm.so.1
c22b2000-c22c8000 r-xp 00000000 08:06 2580964                            /home/dave/Documents/Statistics/SPSS/lib/libspsswmsg.so.1
c22c8000-c22d2000 rw-p 00015000 08:06 2580964                            /home/dave/Documents/Statistics/SPSS/lib/libspsswmsg.so.1
c22d2000-c2497000 r-xp 00000000 08:06 2580960                            /home/dave/Documents/Statistics/SPSS/lib/libspsswlib.so.1
c2497000-c2558000 rw-p 001c5000 08:06 2580960                            /home/dave/Documents/Statistics/SPSS/lib/libspsswlib.so.1
c2558000-c45af000 rw-p c2558000 00:00 0 
c45af000-c46da000 r-xp 00000000 08:06 2581036                            /home/dave/Documents/Statistics/SPSS/lib/libspsswpkg.so.1
c46da000-c4705000 rw-p 0012b000 08:06 2581036                            /home/dave/Documents/Statistics/SPSS/lib/libspsswpkg.so.1
c4705000-c4721000 rw-p c4705000 00:00 0 
c4721000-c473b000 r-xp 00000000 08:06 2580700                            /home/dave/Documents/Statistics/SPSS/lib/libzlib.so.1
c473b000-c473f000 rw-p 0001a000 08:06 2580700                            /home/dave/Documents/Statistics/SPSS/lib/libzlib.so.1
c473f000-c4746000 r-xp 00000000 08:06 2580830                            /home/dave/Documents/Statistics/SPSS/lib/libutilmsg.so.1
c4746000-c4749000 rw-p 00007000 08:06 2580830                            /home/dave/Documents/Statistics/SPSS/lib/libutilmsg.so.1
c4749000-c4750000 r-xp 00000000 08:06 2581084                            /home/dave/Documents/Statistics/SPSS/lib/libutilpckg.so.1
c4750000-c4752000 rw-p 00006000 08:06 2581084                            /home/dave/Documents/Statistics/SPSS/lib/libutilpckg.so.1
c4752000-c4753000 rw-p c4752000 00:00 0 
c4753000-c4754000 ---p c4753000 00:00 0 
c4754000-c4f54000 rwxp c4754000 00:00 0 
c4f54000-c4fef000 r-xp 00000000 08:06 2581046                            /home/dave/Documents/Statistics/SPSS/lib/libifcore.so.5
c4fef000-c4ff6000 rw-p 0009b000 08:06 2581046                            /home/dave/Documents/Statistics/SPSS/lib/libifcore.so.5
c4ff6000-c4ff9000 rw-p c4ff6000 00:00 0 
c4ff9000-c5005000 r-xp 00000000 08:06 2580756                            /home/dave/Documents/Statistics/SPSS/lib/libsfthread.so.1
c5005000-c500a000 rw-p 0000c000 08:06 2580756                            /home/dave/Documents/Statistics/SPSS/lib/libsfthread.so.1
c500a000-c50a0000 r-xp 00000000 08:06 2581099                            /home/dave/Documents/Statistics/SPSS/lib/libdatasrc.so.1
c50a0000-c50d1000 rw-p 00095000 08:06 2581099                            /home/dave/Documents/Statistics/SPSS/lib/libdatasrc.so.1
c50d1000-c50e7000 r-xp 00000000 08:06 2581075                            /home/dave/Documents/Statistics/SPSS/lib/libspssiocv.so.1
c50e7000-c50f5000 rw-p 00016000 08:06 2581075                            /home/dave/Documents/Statistics/SPSS/lib/libspssiocv.so.1
c50f5000-c5105000 rw-p c50f5000 00:00 0 
c5105000-c511d000 r-xp 00000000 08:06 2580951                            /home/dave/Documents/Statistics/SPSS/lib/libdedstore.so.1
c511d000-c5124000 rw-p 00018000 08:06 2580951                            /home/dave/Documents/Statistics/SPSS/lib/libdedstore.so.1
c5124000-c5171000 r-xp 00000000 08:06 2580917                            /home/dave/Documents/Statistics/SPSS/lib/libspssdemg.so.1
c5171000-c518d000 rw-p 0004d000 08:06 2580917                            /home/dave/Documents/Statistics/SPSS/lib/libspssdemg.so.1
c518d000-c51a7000 r-xp 00000000 08:06 2580722                            /home/dave/Documents/Statistics/SPSS/lib/libsvrdmgr.so.1
c51a7000-c51b1000 rw-p 0001a000 08:06 2580722                            /home/dave/Documents/Statistics/SPSS/lib/libsvrdmgr.so.1
c51b1000-c51dc000 r-xp 00000000 08:06 2580708                            /home/dave/Documents/Statistics/SPSS/lib/libspssdeds.so.1
c51dc000-c51ea000 rw-p 0002a000 08:06 2580708                            /home/dave/Documents/Statistics/SPSS/lib/libspssdeds.so.1
c51ea000-c51ed000 ---p c51ea000 00:00 0 
c51ed000-c526b000 rwxp c51ed000 00:00 0 
c526b000-c526e000 ---p c526b000 00:00 0 
c526e000-c52ec000 rwxp c526e000 00:00 0 
c52ec000-c52ef000 ---p c52ec000 00:00 0 
c52ef000-c536d000 rwxp c52ef000 00:00 0 
c536d000-c5374000 r-xp 00000000 08:06 2581056                            /home/dave/Documents/Statistics/SPSS/lib/libspawn.so.1
c5374000-c5376000 rw-p 00006000 08:06 2581056                            /home/dave/Documents/Statistics/SPSS/lib/libspawn.so.1
c5376000-c5377000 ---p c5376000 00:00 0 
c5377000-c5b77000 rwxp c5377000 00:00 0 
c5b77000-c5b78000 ---p c5b77000 00:00 0 
c5b78000-c6378000 rwxp c5b78000 00:00 0 
c6378000-c6379000 ---p c6378000 00:00 0 
c6379000-c6b79000 rwxp c6379000 00:00 0 
c6b79000-c6b7a000 ---p c6b79000 00:00 0 
c6b7a000-c737a000 rwxp c6b7a000 00:00 0 
c737a000-c737b000 ---p c737a000 00:00 0 
c737b000-c7b7b000 rwxp c737b000 00:00 0 
c7b7b000-c7b7c000 ---p c7b7b000 00:00 0 
c7b7c000-c837c000 rwxp c7b7c000 00:00 0 
c837c000-c837d000 ---p c837c000 00:00 0 
c837d000-c8b7d000 rwxp c837d000 00:00 0 
c8b7d000-c8b7e000 ---p c8b7d000 00:00 0 
c8b7e000-c937e000 rwxp c8b7e000 00:00 0 
c937e000-c937f000 r-xp 00000000 08:06 2580809                            /home/dave/Documents/Statistics/SPSS/lib/libmaintsps.so.1
c937f000-c9380000 rw-p 00000000 08:06 2580809                            /home/dave/Documents/Statistics/SPSS/lib/libmaintsps.so.1
c9380000-c9381000 ---p c9380000 00:00 0 
c9381000-c9b81000 rwxp c9381000 00:00 0 
c9b81000-c9b89000 r-xp 00000000 08:06 2580979                            /home/dave/Documents/Statistics/SPSS/lib/libpkginpr.so.1
c9b89000-c9b8c000 rw-p 00007000 08:06 2580979                            /home/dave/Documents/Statistics/SPSS/lib/libpkginpr.so.1
c9b8c000-c9be2000 r-xp 00000000 08:06 2581002                            /home/dave/Documents/Statistics/SPSS/lib/libserver.so.1
c9be2000-c9c00000 rw-p 00055000 08:06 2581002                            /home/dave/Documents/Statistics/SPSS/lib/libserver.so.1
c9c00000-c9cc1000 rw-p c9c00000 00:00 0 
c9cc1000-c9d00000 ---p c9cc1000 00:00 0 
c9d00000-c9d02000 rw-p c9d00000 00:00 0 
c9d02000-c9d05000 r-xp 00000000 08:06 2580957                            /home/dave/Documents/Statistics/SPSS/lib/libspssmsgs.so.1
c9d05000-c9d07000 rw-p 00002000 08:06 2580957                            /home/dave/Documents/Statistics/SPSS/lib/libspssmsgs.so.1
c9d07000-c9d15000 r-xp 00000000 08:06 2580856                            /home/dave/Documents/Statistics/SPSS/lib/libserverclient.so.1
c9d15000-c9d1a000 rw-p 0000e000 08:06 2580856                            /home/dave/Documents/Statistics/SPSS/lib/libserverclient.so.1
c9d1a000-c9d21000 r-xp 00000000 08:06 2580845                            /home/dave/Documents/Statistics/SPSS/lib/libsvrerrs.so.1
c9d21000-c9d24000 rw-p 00006000 08:06 2580845                            /home/dave/Documents/Statistics/SPSS/lib/libsvrerrs.so.1
c9d24000-c9d34000 r-xp 00000000 08:06 2581018                            /home/dave/Documents/Statistics/SPSS/lib/libfwserver.so.1
c9d34000-c9d39000 rw-p 00010000 08:06 2581018                            /home/dave/Documents/Statistics/SPSS/lib/libfwserver.so.1
c9d39000-c9d5d000 r-xp 00000000 08:06 2580705                            /home/dave/Documents/Statistics/SPSS/lib/libnetcom.so.1
c9d5d000-c9d6c000 rw-p 00023000 08:06 2580705                            /home/dave/Documents/Statistics/SPSS/lib/libnetcom.so.1
c9d6c000-c9d72000 r--s 00000000 08:06 1901975                            /home/dave/.fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
c9d72000-c9d75000 r--s 00000000 08:06 1901974                            /home/dave/.fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
c9d75000-c9d78000 r--s 00000000 08:06 1901973                            /home/dave/.fontconfig/6eb3985aa4124903f6ff08ba781cd364-x86.cache-2
c9d78000-c9d79000 r--s 00000000 08:06 1901972                            /home/dave/.fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
c9d79000-c9d7c000 r--s 00000000 08:06 1901971                            /home/dave/.fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
c9d7c000-c9d83000 r--s 00000000 08:06 1901970                            /home/dave/.fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
c9d83000-c9d86000 r--s 00000000 08:06 1901969                            /home/dave/.fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
c9d86000-c9d8e000 r--s 00000000 08:06 1901968                            /home/dave/.fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
c9d8e000-c9d99000 r--s 00000000 08:06 1901967                            /home/dave/.fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
c9d99000-c9d9b000 r--s 00000000 08:06 1901966                            /home/dave/.fontconfig/ddd4086aec35a5275babba44bb759c3c-x86.cache-2
c9d9b000-c9d9c000 r--s 00000000 08:06 1901965                            /home/dave/.fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
c9d9c000-c9dbe000 r--s 00000000 08:06 1901964                            /home/dave/.fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
c9dbe000-c9dc3000 r-xp 00000000 08:06 2580629                            /home/dave/Documents/Statistics/SPSS/lib/libfwsecure.so.1
c9dc3000-c9dc5000 rw-p 00004000 08:06 2580629                            /home/dave/Documents/Statistics/SPSS/lib/libfwsecure.so.1
c9dc5000-c9dcb000 r-xp 00000000 08:06 2580715                            /home/dave/Documents/Statistics/SPSS/lib/libfwutility.so.1
c9dcb000-c9dce000 rw-p 00005000 08:06 2580715                            /home/dave/Documents/Statistics/SPSS/lib/libfwutility.so.1
c9dce000-c9df3000 r-xp 00000000 08:06 2580926                            /home/dave/Documents/Statistics/SPSS/lib/libfmsgs.so.1
c9df3000-c9e04000 rw-p 00024000 08:06 2580926                            /home/dave/Documents/Statistics/SPSS/lib/libfmsgs.so.1
c9e04000-c9e10000 r-xp 00000000 08:06 2580912                            /home/dave/Documents/Statistics/SPSS/lib/libvmessages.so.1
c9e10000-c9e16000 rw-p 0000b000 08:06 2580912                            /home/dave/Documents/Statistics/SPSS/lib/libvmessages.so.1
c9e16000-c9e1e000 r-xp 00000000 08:06 2581059                            /home/dave/Documents/Statistics/SPSS/lib/liblocssrvr.so.1
c9e1e000-c9e21000 rw-p 00007000 08:06 2581059                            /home/dave/Documents/Statistics/SPSS/lib/liblocssrvr.so.1
c9e21000-c9e24000 ---p c9e21000 00:00 0 
c9e24000-c9ea2000 rwxp c9e24000 00:00 0 
c9ea2000-c9ea9000 r--s 00000000 08:06 1901963                            /home/dave/.fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
c9ea9000-c9eaf000 r--s 00000000 08:06 1901962                            /home/dave/.fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
c9eaf000-c9eb6000 r--s 00000000 08:06 1902415                            /home/dave/.fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
c9eb6000-c9eb8000 r--s 00000000 08:06 1901954                            /home/dave/.fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-x86.cache-2
c9eb8000-c9ebb000 ---p c9eb8000 00:00 0 
c9ebb000-c9f39000 rwxp c9ebb000 00:00 0 
c9f39000-c9f75000 rw-s 00000000 00:09 557072                             /SYSV00000000 (deleted)
c9f75000-ca8c8000 r-xp 00000000 08:06 2580793                            /home/dave/Documents/Statistics/SPSS/lib/libicudata.so.32.0
ca8c8000-ca8c9000 rw-p 00952000 08:06 2580793                            /home/dave/Documents/Statistics/SPSS/lib/libicudata.so.32.0
ca8c9000-cac0d000 r-xp 00000000 08:06 2580781                            /home/dave/Documents/Statistics/SPSS/lib/libxerces-c.so.26.0
cac0d000-cad2e000 rw-p 00343000 08:06 2580781                            /home/dave/Documents/Statistics/SPSS/lib/libxerces-c.so.26.0
cad2e000-cae88000 r-xp 00000000 08:06 2580649                            /home/dave/Documents/Statistics/SPSS/lib/libicui18n.so.32.0
cae88000-caee8000 rw-p 0015a000 08:06 2580649                            /home/dave/Documents/Statistics/SPSS/lib/libicui18n.so.32.0
caee8000-caee9000 rw-p caee8000 00:00 0 
caee9000-cafea000 r-xp 00000000 08:06 2580787                            /home/dave/Documents/Statistics/SPSS/lib/libicuuc.so.32.0
cafea000-cb01b000 rw-p 00100000 08:06 2580787                            /home/dave/Documents/Statistics/SPSS/lib/libicuuc.so.32.0
cb01b000-cb031000 r-xp 00000000 08:06 2580672                            /home/dave/Documents/Statistics/SPSS/lib/libvserial.so.1
cb031000-cb039000 rw-p 00016000 08:06 2580672                            /home/dave/Documents/Statistics/SPSS/lib/libvserial.so.1
cb039000-cb04c000 r-xp 00000000 08:06 2580695                            /home/dave/Documents/Statistics/SPSS/lib/libtempdir.so.1
cb04c000-cb053000 rw-p 00013000 08:06 2580695                            /home/dave/Documents/Statistics/SPSS/lib/libtempdir.so.1
cb053000-cb096000 r-xp 00000000 08:06 2580886                            /home/dave/Documents/Statistics/SPSS/lib/libplatdep.so.1
cb096000-cb0ae000 rw-p 00042000 08:06 2580886                            /home/dave/Documents/Statistics/SPSS/lib/libplatdep.so.1
cb0ae000-cb1bf000 r-xp 00000000 08:06 2580853                            /home/dave/Documents/Statistics/SPSS/lib/libspssstat.so.1
cb1bf000-cb1e4000 rw-p 00110000 08:06 2580853                            /home/dave/Documents/Statistics/SPSS/lib/libspssstat.so.1
cb1e4000-cb200000 rw-p cb1e4000 00:00 0 
cb200000-cb300000 rw-p cb200000 00:00 0 
cb300000-cb301000 ---p cb300000 00:00 0 
cb301000-cb308000 rwxp cb301000 00:00 0 
cb308000-cb30e000 r-xp 00000000 08:06 2580669                            /home/dave/Documents/Statistics/SPSS/lib/libvutility.so.1
cb30e000-cb311000 rw-p 00006000 08:06 2580669                            /home/dave/Documents/Statistics/SPSS/lib/libvutility.so.1
cb311000-cb315000 r-xp 00000000 08:06 2580763                            /home/dave/Documents/Statistics/SPSS/lib/libsockbsd.so.1
cb315000-cb316000 rw-p 00004000 08:06 2580763                            /home/dave/Documents/Statistics/SPSS/lib/libsockbsd.so.1
cb316000-cb319000 ---p cb316000 00:00 0 
cb319000-cb397000 rwxp cb319000 00:00 0 
cb397000-cb39a000 ---p cb397000 00:00 0 
cb39a000-cb418000 rwxp cb39a000 00:00 0 
cb418000-cb41f000 r-xp 00000000 08:06 2556048                            /home/dave/Documents/Statistics/SPSS/bin/_jvm/lib/i386/libnio.so
cb41f000-cb420000 rw-p 00006000 08:06 2556048                            /home/dave/Documents/Statistics/SPSS/bin/_jvm/lib/i386/libnio.so
cb420000-cb431000 r-xp 00000000 08:06 2556059                            /home/dave/Documents/Statistics/SPSS/bin/_jvm/lib/i386/libnet.so
cb431000-cb432000 rw-p 00011000 08:06 2556059                            /home/dave/Documents/Statistics/SPSS/bin/_jvm/lib/i386/libnet.so
cb432000-cb435000 ---p cb432000 00:00 0 
cb435000-cb4b3000 rwxp cb435000 00:00 0 
cb4b3000-cb4b6000 ---p cb4b3000 00:00 0 
cb4b6000-cb534000 rwxp cb4b6000 00:00 0 
cb534000-cb537000 ---p cb534000 00:00 0 
cb537000-cb5b5000 rwxp cb537000 00:00 0 
cb5b5000-cb5b8000 ---p cb5b5000 00:00 0 
cb5b8000-cb636000 rwxp cb5b8000 00:00 0 
cb636000-cb639000 ---p cb636000 00:00 0 
cb639000-cb6b7000 rwxp cb639000 00:00 0 
cb6b7000-cb731000 r-xp 00000000 08:06 2556029                            /home/dave/Documents/Statistics/SPSS/bin/_jvm/lib/i386/libfontmanager.so
cb731000-cb73b000 rw-p 00079000 08:06 2556029                            /home/dave/Documents/Statistics/SPSS/bin/_jvm/lib/i386/libfontmanager.so
cb73b000-cb73f000 rw-p cb73b000 00:00 0 
cb73f000-cb743000 r-xp 00000000 08:05 107520                             /usr/lib32/libXdmcp.so.6.0.0
cb743000-cb744000 rw-p 00003000 08:05 107520                             /usr/lib32/libXdmcp.so.6.0.0
cb744000-cb75c000 r-xp 00000000 08:05 107270                             /usr/lib32/libxcb.so.1.1.0
cb75c000-cb75d000 r--p 00017000 08:05 107270                             /usr/lib32/libxcb.so.1.1.0
cb75d000-cb75e000 rw-p 00018000 08:05 107270                             /usr/lib32/libxcb.so.1.1.0
cb75e000-cb848000 r-xp 00000000 08:05 107221                             /usr/lib32/libX11.so.6.2.0
cb848000-cb849000 ---p 000ea000 08:05 107221                             /usr/lib32/libX11.so.6.2.0
cb849000-cb84a000 r--p 000ea000 08:05 107221                             /usr/lib32/libX11.so.6.2.0
cb84a000-cb84c000 rw-p 000eb000 08:05 107221                             /usr/lib32/libX11.so.6.2.0
cb84c000-cb84d000 rw-p cb84c000 00:00 0 
cb84d000-cb85b000 r-xp 00000000 08:05 107521                             /usr/lib32/libXext.so.6.4.0
cb85b000-cb85c000 r--p 0000d000 08:05 107521                             /usr/lib32/libXext.so.6.4.0
cb85c000-cb85d000 rw-p 0000e000 08:05 107521                             /usr/lib32/libXext.so.6.4.0
cb85d000-cb861000 r-xp 00000000 08:05 107926                             /usr/lib32/libXfixes.so.3.1.0
cb861000-cb862000 rw-p 00003000 08:05 107926                             /usr/lib32/libXfixes.so.3.1.0
cb862000-cb86a000 r-xp 00000000 08:05 108487                             /usr/lib32/libXrender.so.1.3.0
cb86a000-cb86b000 r--p 00007000 08:05 108487                             /usr/lib32/libXrender.so.1.3.0
cb86b000-cb86c000 rw-p 00008000 08:05 108487                             /usr/lib32/libXrender.so.1.3.0
cb86c000-cb874000 r-xp 00000000 08:05 107272                             /usr/lib32/libXcursor.so.1.0.2
cb874000-cb875000 rw-p 00007000 08:05 107272                             /usr/lib32/libXcursor.so.1.0.2
cb875000-cb876000 r--p 00000000 08:05 75059                              /usr/share/locale-langpack/en_GB/LC_MESSAGES/libc.mo
cb876000-cb8a5000 r-xp 00000000 08:06 2556021                            /home/dave/Documents/Statistics/SPSS/bin/_jvm/lib/i386/xawt/libmawt.so
cb8a5000-cb8a8000 rw-p 0002e000 08:06 2556021                            /home/dave/Documents/Statistics/SPSS/bin/_jvm/lib/i386/xawt/libmawt.so
cb8a8000-cb8a9000 rw-p cb8a8000 00:00 0 
cb8a9000-cb96f000 r-xp 00000000 08:06 2556024                            /home/dave/Documents/Statistics/SPSS/bin/_jvm/lib/i386/libmlib_image.so
cb96f000-cb970000 rw-p 000c5000 08:06 2556024                            /home/dave/Documents/Statistics/SPSS/bin/_jvm/lib/i386/libmlib_image.so
cb970000-cb9d0000 r-xp 00000000 08:06 2556018                            /home/dave/Documents/Statistics/SPSS/bin/_jvm/lib/i386/libawt.so
cb9d0000-cb9d6000 rw-p 0005f000 08:06 2556018                            /home/dave/Documents/Statistics/SPSS/bin/_jvm/lib/i386/libawt.so
cb9d6000-cb9fa000 rw-p cb9d6000 00:00 0 
cb9fa000-cba17000 r--s 00000000 08:06 2549361                            /home/dave/Documents/Statistics/SPSS/bin/xmlrpc-2.0.1.jar
cba17000-cba36000 r--s 00000000 08:06 2549360                            /home/dave/Documents/Statistics/SPSS/bin/wsdl4j-1.5.1.jar
cba36000-cba90000 r--s 00000000 08:06 2549346                            /home/dave/Documents/Statistics/SPSS/bin/UITools.jar
cba90000-cbb09000 r--s 00000000 08:06 2549345                            /home/dave/Documents/Statistics/SPSS/bin/TreeViewerPanel.jar
cbb09000-cbb7a000 r--s 00000000 08:06 2549344                            /home/dave/Documents/Statistics/SPSS/bin/TreeViewer.jar
cbb7a000-cbb9c000 r--s 00000000 08:06 2549343                            /home/dave/Documents/Statistics/SPSS/bin/TreeModel.jar
cbb9c000-cbbca000 r--s 00000000 08:06 2549342                            /home/dave/Documents/Statistics/SPSS/bin/TreeEditor.jar
cbbca000-cbbe2000 r--s 00000000 08:06 2549408                            /home/dave/Documents/Statistics/SPSS/bin/spssexcel.jar
cbbe2000-cc54a000 r--s 00000000 08:06 2549339                            /home/dave/Documents/Statistics/SPSS/bin/SpssClientUI.jar
cc54a000-cc67a000 r--s 00000000 08:06 2549338                            /home/dave/Documents/Statistics/SPSS/bin/SpssClientCore.jar
cc67a000-cc6cc000 r--s 00000000 08:06 2549335                            /home/dave/Documents/Statistics/SPSS/bin/security-client.jar
cc6cc000-cc6d1000 r--s 00000000 08:06 2549334                            /home/dave/Documents/Statistics/SPSS/bin/saaj.jar
cc6d1000-cc743000 r--s 00000000 08:06 2549333                            /home/dave/Documents/Statistics/SPSS/bin/repository-ui.jar
cc743000-cc75a000 r--s 00000000 08:06 2549331                            /home/dave/Documents/Statistics/SPSS/bin/repository-client-application.jar
cc75a000-cc81e000 r--s 00000000 08:06 2549332                            /home/dave/Documents/Statistics/SPSS/bin/repository-client.jar
cc81e000-cc840000 r--s 00000000 08:06 2549330                            /home/dave/Documents/Statistics/SPSS/bin/RapidSpell.jar
cc840000-cc904000 r--s 00000000 08:06 2549328                            /home/dave/Documents/Statistics/SPSS/bin/poi.jar
cc904000-cc97c000 r--s 00000000 08:06 2549327                            /home/dave/Documents/Statistics/SPSS/bin/PivotTableEditor.jar
cc97c000-cc980000 r--s 00000000 08:06 2549441                            /home/dave/Documents/Statistics/SPSS/bin/pesworker.jar
cc980000-cc9d0000 r--s 00000000 08:06 2549324                            /home/dave/Documents/Statistics/SPSS/bin/mail.jar
cc9d0000-cca16000 r--s 00000000 08:06 2549323                            /home/dave/Documents/Statistics/SPSS/bin/looks-1.3.1.jar
cca16000-cca86000 r--s 00000000 08:06 2549320                            /home/dave/Documents/Statistics/SPSS/bin/JimiProClasses.zip
cca86000-cca8e000 r--s 00000000 08:06 2549319                            /home/dave/Documents/Statistics/SPSS/bin/jaxrpc.jar
cca8e000-ccbec000 r--s 00000000 08:06 2549318                            /home/dave/Documents/Statistics/SPSS/bin/jai_core.jar
ccbec000-ccc1e000 r--s 00000000 08:06 2549317                            /home/dave/Documents/Statistics/SPSS/bin/jai_codec.jar
ccc1e000-ccdd7000 r--s 00000000 08:06 2549315                            /home/dave/Documents/Statistics/SPSS/bin/itext-2.0.1.jar
ccdd7000-cce1e000 r--s 00000000 08:06 2549314                            /home/dave/Documents/Statistics/SPSS/bin/gpl.jar
cce1e000-cce30000 r--s 00000000 08:06 2549313                            /home/dave/Documents/Statistics/SPSS/bin/ExportTools.jar
cce30000-cd20d000 r--s 00000000 08:06 2549406                            /home/dave/Documents/Statistics/SPSS/bin/excel2007.jar
cd20d000-cd20f000 r--s 00000000 08:06 2549312                            /home/dave/Documents/Statistics/SPSS/bin/exacc.jar
cd20f000-cd218000 r--s 00000000 08:06 2549350                            /home/dave/Documents/Statistics/SPSS/bin/VisUtils.jar
cd218000-cd23e000 r--s 00000000 08:06 2549341                            /home/dave/Documents/Statistics/SPSS/bin/transformations.jar
cd23e000-cd574000 r--s 00000000 08:06 2549349                            /home/dave/Documents/Statistics/SPSS/bin/visualization.jar
cd574000-cd579000 r--s 00000000 08:06 2549311                            /home/dave/Documents/Statistics/SPSS/bin/emfProcessor.jar
cd579000-cd59c000 r--s 00000000 08:06 2549310                            /home/dave/Documents/Statistics/SPSS/bin/cop-client.jar
cd59c000-cd5a6000 r--s 00000000 08:06 2549309                            /home/dave/Documents/Statistics/SPSS/bin/commons-logging-1.0.4.jar
cd5a6000-cd5b8000 r--s 00000000 08:06 2549308                            /home/dave/Documents/Statistics/SPSS/bin/commons-discovery-0.2.jar
cd5b8000-cd5c4000 r--s 00000000 08:06 2549307                            /home/dave/Documents/Statistics/SPSS/bin/commons-codec-1.3.jar
cd5c4000-cd738000 r--s 00000000 08:06 2549306                            /home/dave/Documents/Statistics/SPSS/bin/ChartEditor.jar
cd738000-cd8dc000 r--s 00000000 08:06 2549305                            /home/dave/Documents/Statistics/SPSS/bin/castor-1.1.jar
cd8dc000-cda63000 r--s 00000000 08:06 2549304                            /home/dave/Documents/Statistics/SPSS/bin/axis.jar
cda63000-cda71000 r--s 00000000 08:06 2549301                            /home/dave/Documents/Statistics/SPSS/bin/activation.jar
cda71000-cdb36000 r--s 00000000 08:06 2555929                            /home/dave/Documents/Statistics/SPSS/bin/_jvm/lib/ext/localedata.jar
cdb36000-cdb61000 r--s 00000000 08:06 2555931                            /home/dave/Documents/Statistics/SPSS/bin/_jvm/lib/ext/sunpkcs11.jar
cdb61000-cdb63000 r--s 00000000 08:06 2555930                            /home/dave/Documents/Statistics/SPSS/bin/_jvm/lib/ext/dnsns.jar
cdb63000-cdb8a000 r--s 00000000 08:06 2555932                            /home/dave/Documents/Statistics/SPSS/bin/_jvm/lib/ext/sunjce_provider.jar
cdb8a000-cdb8b000 ---p cdb8a000 00:00 0 
cdb8b000-cdc0b000 rwxp cdb8b000 00:00 0 
cdc0b000-cdc0e000 ---p cdc0b000 00:00 0 
cdc0e000-cdc8c000 rwxp cdc0e000 00:00 0 
cdc8c000-cdc8f000 ---p cdc8c000 00:00 0 
cdc8f000-cdd0d000 rwxp cdc8f000 00:00 0 
cdd0d000-cdd10000 ---p cdd0d000 00:00 0 
cdd10000-cdd8e000 rwxp cdd10000 00:00 0 
cdd8e000-cdd91000 ---p cdd8e000 00:00 0 
cdd91000-cde0f000 rwxp cdd91000 00:00 0 
cde0f000-cde12000 ---p cde0f000 00:00 0 
cde12000-cde90000 rwxp cde12000 00:00 0 
cde90000-cde91000 ---p cde90000 00:00 0 
cde91000-cdf1a000 rwxp cde91000 00:00 0 
cdf1a000-cdf32000 rwxp cdf1a000 00:00 0 
cdf32000-cdf39000 rwxp cdf32000 00:00 0 
cdf39000-ce01f000 rwxp cdf39000 00:00 0 
ce01f000-ce020000 rwxp ce01f000 00:00 0 
ce020000-ce032000 rwxp ce020000 00:00 0 
ce032000-ce039000 rwxp ce032000 00:00 0 
ce039000-ce11f000 rwxp ce039000 00:00 0 
ce11f000-ce128000 rwxp ce11f000 00:00 0 
ce128000-ce13f000 rwxp ce128000 00:00 0 
ce13f000-ce250000 rwxp ce13f000 00:00 0 
ce250000-d08a0000 rwxp ce250000 00:00 0 
d08a0000-d152b000 rwxp d08a0000 00:00 0 
d152b000-ee140000 rwxp d152b000 00:00 0 
ee140000-ef280000 rwxp ee140000 00:00 0 
ef280000-f2140000 rwxp ef280000 00:00 0 
f2140000-f2145000 r--s 00000000 08:06 2549352                            /home/dave/Documents/Statistics/SPSS/bin/VizImager.jar
f2145000-f214f000 r--s 00000000 08:06 2549348                            /home/dave/Documents/Statistics/SPSS/bin/VisSupport.jar
f214f000-f2156000 rwxp f214f000 00:00 0 
f2156000-f21cf000 rwxp f2156000 00:00 0 
f21cf000-f2357000 rwxp f21cf000 00:00 0 
f2357000-f41cf000 rwxp f2357000 00:00 0 
f41cf000-f4a3e000 r--s 00000000 08:06 2549267                            /home/dave/Documents/Statistics/SPSS/bin/_jvm/lib/charsets.jar
f4a3e000-f4a53000 r--s 00000000 08:06 2549263                            /home/dave/Documents/Statistics/SPSS/bin/_jvm/lib/jce.jar
f4a53000-f4ad8000 r--s 00000000 08:06 2549282                            /home/dave/Documents/Statistics/SPSS/bin/_jvm/lib/jsse.jar
f4ad8000-f4b41000 rw-p f4ad8000 00:00 0 
f4b41000-f7150000 r--s 00000000 08:06 2549259                            /home/dave/Documents/Statistics/SPSS/bin/_jvm/lib/rt.jar
f7150000-f715f000 r-xp 00000000 08:06 2556026                            /home/dave/Documents/Statistics/SPSS/bin/_jvm/lib/i386/libzip.so
f715f000-f7161000 rw-p 0000e000 08:06 2556026                            /home/dave/Documents/Statistics/SPSS/bin/_jvm/lib/i386/libzip.so
f7161000-f7182000 r-xp 00000000 08:06 2556055                            /home/dave/Documents/Statistics/SPSS/bin/_jvm/lib/i386/libjava.so
f7182000-f7184000 rw-p 00020000 08:06 2556055                            /home/dave/Documents/Statistics/SPSS/bin/_jvm/lib/i386/libjava.so
f7184000-f718e000 r-xp 00000000 08:05 131107                             /lib32/libnss_files-2.9.so
f718e000-f718f000 r--p 00009000 08:05 131107                             /lib32/libnss_files-2.9.so
f718f000-f7190000 rw-p 0000a000 08:05 131107                             /lib32/libnss_files-2.9.so
f7190000-f7199000 r-xp 00000000 08:05 131109                             /lib32/libnss_nis-2.9.so
f7199000-f719a000 r--p 00008000 08:05 131109                             /lib32/libnss_nis-2.9.so
f719a000-f719b000 rw-p 00009000 08:05 131109                             /lib32/libnss_nis-2.9.so
f719b000-f71a2000 r-xp 00000000 08:05 131105                             /lib32/libnss_compat-2.9.so
f71a2000-f71a3000 r--p 00006000 08:05 131105                             /lib32/libnss_compat-2.9.so
f71a3000-f71a4000 rw-p 00007000 08:05 131105                             /lib32/libnss_compat-2.9.so
f71a4000-f71a6000 r-xp 00000000 08:05 107222                             /usr/lib32/libXau.so.6.0.0
f71a6000-f71a7000 r--p 00001000 08:05 107222                             /usr/lib32/libXau.so.6.0.0
f71a7000-f71a8000 rw-p 00002000 08:05 107222                             /usr/lib32/libXau.so.6.0.0
f71a8000-f71a9000 r--s 00000000 08:06 2549351                            /home/dave/Documents/Statistics/SPSS/bin/VizConverter.jar
f71a9000-f71b4000 r-xp 00000000 08:06 2556052                            /home/dave/Documents/Statistics/SPSS/bin/_jvm/lib/i386/libverify.so
f71b4000-f71b5000 rw-p 0000b000 08:06 2556052                            /home/dave/Documents/Statistics/SPSS/bin/_jvm/lib/i386/libverify.so
f71b5000-f71bd000 rw-s 00000000 08:05 6699                               /tmp/hsperfdata_dave/4578
f71bd000-f752d000 r-xp 00000000 08:06 2556035                            /home/dave/Documents/Statistics/SPSS/bin/_jvm/lib/i386/client/libjvm.so
f752d000-f754b000 rw-p 00370000 08:06 2556035                            /home/dave/Documents/Statistics/SPSS/bin/_jvm/lib/i386/client/libjvm.so
f754b000-f7962000 rw-p f754b000 00:00 0 
f7962000-f79a1000 r--p 00000000 08:05 12929                              /usr/lib/locale/en_GB.utf8/LC_CTYPE
f79a1000-f7a8c000 r--p 00000000 08:05 12928                              /usr/lib/locale/en_GB.utf8/LC_COLLATE
f7a8c000-f7a8e000 rw-p f7a8c000 00:00 0 
f7a8e000-f7bea000 r-xp 00000000 08:05 131098                             /lib32/libc-2.9.so
f7bea000-f7beb000 ---p 0015c000 08:05 131098                             /lib32/libc-2.9.so
f7beb000-f7bed000 r--p 0015c000 08:05 131098                             /lib32/libc-2.9.so
f7bed000-f7bee000 rw-p 0015e000 08:05 131098                             /lib32/libc-2.9.so
f7bee000-f7bf1000 rw-p f7bee000 00:00 0 
f7bf1000-f7c30000 r-xp 00000000 08:06 2580741                            /home/dave/Documents/Statistics/SPSS/lib/libirc.so
f7c30000-f7c32000 rw-p 0003e000 08:06 2580741                            /home/dave/Documents/Statistics/SPSS/lib/libirc.so
f7c32000-f7c33000 r-xp 00000000 08:06 2580747                            /home/dave/Documents/Statistics/SPSS/lib/libcxaguard.so.5
f7c33000-f7c34000 rw-p 00000000 08:06 2580747                            /home/dave/Documents/Statistics/SPSS/lib/libcxaguard.so.5
f7c34000-f7c41000 r-xp 00000000 08:05 56637                              /usr/lib32/libgcc_s.so.1
f7c41000-f7c42000 r--p 0000c000 08:05 56637                              /usr/lib32/libgcc_s.so.1
f7c42000-f7c43000 rw-p 0000d000 08:05 56637                              /usr/lib32/libgcc_s.so.1
f7c43000-f7cf3000 r-xp 00000000 08:05 106877                             /usr/lib32/libstdc++.so.5.0.7
f7cf3000-f7cf8000 rw-p 000af000 08:05 106877                             /usr/lib32/libstdc++.so.5.0.7
f7cf8000-f7cfe000 rw-p f7cf8000 00:00 0 
f7cfe000-f7d22000 r-xp 00000000 08:05 131102                             /lib32/libm-2.9.so
f7d22000-f7d23000 r--p 00023000 08:05 131102                             /lib32/libm-2.9.so
f7d23000-f7d24000 rw-p 00024000 08:05 131102                             /lib32/libm-2.9.so
f7d24000-f7f60000 r-xp 00000000 08:06 2581012                            /home/dave/Documents/Statistics/SPSS/lib/libimf.so
f7f60000-f7f62000 rw-p 0023b000 08:06 2581012                            /home/dave/Documents/Statistics/SPSS/lib/libimf.so
f7f62000-f7f69000 r-xp 00000000 08:05 131114                             /lib32/librt-2.9.so
f7f69000-f7f6a000 r--p 00006000 08:05 131114                             /lib32/librt-2.9.so
f7f6a000-f7f6b000 rw-p 00007000 08:05 131114                             /lib32/librt-2.9.so
f7f6b000-f7f6d000 r-xp 00000000 08:05 131101                             /lib32/libdl-2.9.so
f7f6d000-f7f6e000 r--p 00001000 08:05 131101                             /lib32/libdl-2.9.so
f7f6e000-f7f6f000 rw-p 00002000 08:05 131101                             /lib32/libdl-2.9.so
f7f6f000-f7f84000 r-xp 00000000 08:05 131112                             /lib32/libpthread-2.9.so
f7f84000-f7f85000 r--p 00014000 08:05 131112                             /lib32/libpthread-2.9.so
f7f85000-f7f86000 rw-p 00015000 08:05 131112                             /lib32/libpthread-2.9.so
f7f86000-f7f89000 rw-p f7f86000 00:00 0 
f7f89000-f7f9e000 r-xp 00000000 08:05 131104                             /lib32/libnsl-2.9.so
f7f9e000-f7f9f000 r--p 00014000 08:05 131104                             /lib32/libnsl-2.9.so
f7f9f000-f7fa0000 rw-p 00015000 08:05 131104                             /lib32/libnsl-2.9.so
f7fa0000-f7fa2000 rw-p f7fa0000 00:00 0 
f7fa2000-f7fa4000 r--s 00000000 08:06 2549347                            /home/dave/Documents/Statistics/SPSS/bin/ViewableTree.jar
f7fa4000-f7fa8000 r--s 00000000 08:06 2549316                            /home/dave/Documents/Statistics/SPSS/bin/jaguar_treemodel.jar
f7fa8000-f7fae000 r-xp 00000000 08:06 2556017                            /home/dave/Documents/Statistics/SPSS/bin/_jvm/lib/i386/native_threads/libhpi.so
f7fae000-f7faf000 rw-p 00006000 08:06 2556017                            /home/dave/Documents/Statistics/SPSS/bin/_jvm/lib/i386/native_threads/libhpi.so
f7faf000-f7fb0000 rwxp f7faf000 00:00 0 
f7fb0000-f7fb1000 r--p f7fb0000 00:00 0 
f7fb1000-f7fb2000 r--p 00000000 08:05 12934                              /usr/lib/locale/en_GB.utf8/LC_NUMERIC
f7fb2000-f7fb3000 r--p 00000000 08:05 12937                              /usr/lib/locale/en_GB.utf8/LC_TIME
f7fb3000-f7fb4000 r--p 00000000 08:05 12932                              /usr/lib/locale/en_GB.utf8/LC_MONETARY
f7fb4000-f7fb5000 r--p 00000000 08:05 12938                              /usr/lib/locale/en_GB.utf8/LC_MESSAGES/SYS_LC_MESSAGES
f7fb5000-f7fb6000 r--p 00000000 08:05 12935                              /usr/lib/locale/en_GB.utf8/LC_PAPER
f7fb6000-f7fb7000 r--p 00000000 08:05 12933                              /usr/lib/locale/en_GB.utf8/LC_NAME
f7fb7000-f7fb8000 r--p 00000000 08:05 12927                              /usr/lib/locale/en_GB.utf8/LC_ADDRESS
f7fb8000-f7fb9000 r--p 00000000 08:05 12936                              /usr/lib/locale/en_GB.utf8/LC_TELEPHONE
f7fb9000-f7fba000 r--p 00000000 08:05 12931                              /usr/lib/locale/en_GB.utf8/LC_MEASUREMENT
f7fba000-f7fbb000 r--p 00000000 08:05 12930                              /usr/lib/locale/en_GB.utf8/LC_IDENTIFICATION
f7fbb000-f7fbd000 rw-p f7fbb000 00:00 0 
f7fbd000-f7fbe000 r-xp f7fbd000 00:00 0                                  [vdso]
f7fbe000-f7fdd000 r-xp 00000000 08:05 131095                             /lib32/ld-2.9.so
f7fdd000-f7fde000 r--p 0001e000 08:05 131095                             /lib32/ld-2.9.so
f7fde000-f7fdf000 rw-p 0001f000 08:05 131095                             /lib32/ld-2.9.so
ff8dd000-ff8e0000 ---p ff8dd000 00:00 0 
ff8e0000-ffadd000 rwxp 7fffffe00000 00:00 0                              [stack]
ffadd000-ffadf000 rw-p 7fffffffd000 00:00 0 

VM Arguments:
jvm_args: -ea -client -Xmx512M -Djava.library.path=/home/dave/Documents/Statistics/SPSS/bin/_jvm/lib/i386/client:/home/dave/Documents/Statistics/SPSS/bin/_jvm/lib/i386:/home/dave/Documents/Statistics/SPSS/lib -Djava.io.tmpdir=/tmp/ -Duser.dir=/home/dave -Dapplication.home=/home/dave/Documents/Statistics/SPSS/bin -Dswing.aatext=false
java_command: <unknown>
Launcher Type: generic

Environment Variables:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
USERNAME=dave
LD_LIBRARY_PATH=/home/dave/Documents/Statistics/SPSS/lib:/home/dave/Documents/Statistics/SPSS/bin:.
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x32a000], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x32a000], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x28e010], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: [libjvm.so+0x28e010], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x28e010], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x290460], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x28fe90], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x28fe90], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x28fe90], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x28fe90], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:5.0

uname:Linux 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 22:12:12 UTC 2009 x86_64
libc:glibc 2.9 NPTL 2.9 
rlimit: STACK 8192k, CORE 0k, NPROC infinity, NOFILE 1024, AS infinity
load average:2.19 0.87 0.32

CPU:total 4 (cores per cpu 4, threads per core 1) family 31 model 2 stepping 3, cmov, cx8, fxsr, mmx, sse, sse2, sse3, mmxext, 3dnowext, 3dnow

Memory: 4k page, physical 8083528k(7011488k free), swap 1168k(1168k free)

vm_info: Java HotSpot(TM) Client VM (1.5.0_11-b03) for linux-x86, built on Dec 15 2006 02:25:41 by java_re with gcc 3.2.1-7a (J2SE release)[/b]

Some help please people!

---

### Post by davidgutu on 2011-01-20
same thing keeps happening to me. Did you find out how to solve the problem?

---

