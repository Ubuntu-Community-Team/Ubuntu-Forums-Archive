---
title: "Segfault debugging ASP.Net projects on Ubuntu"
date: 2010-10-21
forum: General Help
---

### Post by Throctukes on 2010-10-21
I've seen a problem debugging ASP.Net projects in monodevelop specifically on Ubuntu - I've reported this as a bug over on the mono bugzilla, but since it looks very much like an Ubuntu-specific problem thought I should post something over here too.

To reproduce:
Open monodevelop, and create a new ASP.Net mvc project, put a breakpoint in the homecontroller.cs file and debug. The debugger will either segfault with no prompting (like 99% of the time) or, if it does manage to break, will segfault as soon as you hover any member variable or method.

The weird bit is that the above works fine on ubuntu 9.10, no segfaults. It seems to work fine on machines initially installed with 9.10 but subsequently upgraded. Every time I create a fresh 10.04 or 10.10 installation, however, I see this problem. For purposes of figuring out what's going on, I've been building mono from sources so it's not a problem in the mono packages themselves (though I see the same behaviour using mono from the repos and also from badgerports) but it does seem to be a specifically Ubuntu issue (I can't reproduce this on openSUSE) and seems to be caused by something that changed between 9.10 and 10.04 - though I have no idea what.

Any ideas for avenues of investigation?

---

### Post by directhex on 2010-10-21
using the hard or soft debugger?

---

### Post by Throctukes on 2010-10-21
Both. Only difference I can see is that the soft debugger fails before hitting the breakpoint, the hard debugger segfaults if you hover anything after hitting the breakpoint.

Update to the weirdness: I've just upgraded a VM from 9.10 (with debugging working) to 10.04. My plan was to compare *everything* on the system to a fresh 10.04 install... except after upgrading the debugger no longer worked.

That's probably a saner result than I originally described, but my old development machine went through the same process when 10.04 was first released, and the debugger was (and is) fine on that.

---

### Post by directhex on 2010-10-21
I can't reproduce any segfaults with the setup you describe on 10.10. It doesn't seem to actually *work* with the hard debugger, but the soft debugger works a treat.

---

### Post by Throctukes on 2010-10-21
Is that on a fresh install? As I said, my old machine which I've upgraded works fine but on both a cleanly installed physical machine and VMs I've created I see the same behaviour. I can provide a VMWare image which exhibits the problem if that would be of any use?

---

### Post by directhex on 2010-10-22
Can't duplicate it on a fresh install.

Do you have all the required parts to run the project?

* mono-xsp2
* mono-gmcs
* libmono-system-web-mvc2.0-cil

?

---

### Post by Throctukes on 2010-10-22
> **directhex said:**
> Can't duplicate it on a fresh install.

Do you have all the required parts to run the project?

* mono-xsp2
* mono-gmcs
* libmono-system-web-mvc2.0-cil

?

I've built and installed the following sources:

gdb-7.2.tar.gz
gtk-sharp-2.12.10.tar.bz2
mono-2.8.tar.bz2
mono-debugger-2.8.tar.bz2
monodevelop-debugger-gdb-2.4.tar.bz2
mono-tools-2.8.tar.bz2
gnome-sharp-2.24.1.tar.bz2
libgdiplus-2.8.tar.bz2
mono-addins-0.5.tar.bz2
monodevelop-2.4.tar.bz2
monodevelop-debugger-mdb-2.4.tar.bz2
xsp-2.8.tar.bz2

I can run (not debug) the project with no problems. The automatically generated project will even run in the debugger provided there are no breakpoints set (more complex projects still fail in the debugger even with no breakpoints).


I've also tried with the 2.6 sources and the relevant packages from repos (it wouldn't get as far as segfaulting if xsp2 or gmcs were missing, would it? I mean, it wouldn't work but it wouldn't even try to run the code).

---

### Post by Throctukes on 2010-10-25
Were you using a 32 bit install?

On a hunch, I put together two VMs, one 32-bit 10.10 and one 64-bit. 32-bit works perfectly, 64-bit segfaults. Looks like maybe it's a 64-bit specific issue?

Sorry, I never thought to test both architectures before now.

---

### Post by directhex on 2010-10-25
I only run 64-bit, so it's not that. Hm...

---

### Post by Throctukes on 2010-10-25
On the 64 bit machines I get:
```
Resolved pending breakpoint at 'HomeController.cs:16' to ActionResult Controllers.HomeController:Index ():0.
Stacktrace:

  at Controllers.HomeController.Index () [0x0001c] in /home/ubuntu/Projects/testweb/testweb/Controllers/HomeController.cs:18
  at (wrapper dynamic-method) System.Runtime.CompilerServices.ExecutionScope.lambda_method (System.Runtime.CompilerServices.ExecutionScope,System.Web.Mvc.ControllerBase,object[]) <IL 0x0000b, 0x00118>
  at System.Web.Mvc.ActionMethodDispatcher.Execute (System.Web.Mvc.ControllerBase,object[]) <IL 0x00008, 0x0004b>
  at System.Web.Mvc.ReflectedActionDescriptor.Execute (System.Web.Mvc.ControllerContext,System.Collections.Generic.IDictionary`2<string, object>) <IL 0x00080, 0x002a3>
  at System.Web.Mvc.ControllerActionInvoker.InvokeActionMethod (System.Web.Mvc.ControllerContext,System.Web.Mvc.ActionDescriptor,System.Collections.Generic.IDictionary`2<string, object>) <IL 0x00003, 0x00061>
  at System.Web.Mvc.ControllerActionInvoker/<InvokeActionMethodWithFilters>c__AnonStoreyB.<>m__E () <IL 0x0002d, 0x000cb>
  at System.Web.Mvc.ControllerActionInvoker.InvokeActionMethodFilter (System.Web.Mvc.IActionFilter,System.Web.Mvc.ActionExecutingContext,System.Func`1<System.Web.Mvc.ActionExecutedContext>) <IL 0x00034, 0x001c6>
  at System.Web.Mvc.ControllerActionInvoker/<InvokeActionMethodWithFilters>c__AnonStoreyB/<InvokeActionMethodWithFilters>c__AnonStoreyC.<>m__12 () <IL 0x00017, 0x0004f>
  at System.Web.Mvc.ControllerActionInvoker.InvokeActionMethodWithFilters (System.Web.Mvc.ControllerContext,System.Collections.Generic.IList`1<System.Web.Mvc.IActionFilter>,System.Web.Mvc.ActionDescriptor,System.Collections.Generic.IDictionary`2<string, object>) <IL 0x00067, 0x00249>
  at System.Web.Mvc.ControllerActionInvoker.InvokeAction (System.Web.Mvc.ControllerContext,string) <IL 0x000ae, 0x003f0>
  at System.Web.Mvc.Controller.ExecuteCore () <IL 0x00035, 0x000f8>
  at System.Web.Mvc.ControllerBase.Execute (System.Web.Routing.RequestContext) <IL 0x00019, 0x000b8>
  at System.Web.Mvc.ControllerBase.System.Web.Mvc.IController.Execute (System.Web.Routing.RequestContext) <IL 0x00002, 0x00045>
  at System.Web.Mvc.MvcHandler.ProcessRequest (System.Web.HttpContextBase) <IL 0x0006c, 0x00221>
  at System.Web.Mvc.MvcHandler.ProcessRequest (System.Web.HttpContext) <IL 0x00009, 0x00084>
  at System.Web.Mvc.MvcHandler.System.Web.IHttpHandler.ProcessRequest (System.Web.HttpContext) <IL 0x00002, 0x00042>
  at System.Web.HttpApplication/<Pipeline>c__Iterator2.MoveNext () [0x00ce5] in /home/ubuntu/Downloads/mono-2.8/mcs/class/System.Web/System.Web/HttpApplication.cs:1344
  at System.Web.HttpApplication.Tick () [0x00000] in /home/ubuntu/Downloads/mono-2.8/mcs/class/System.Web/System.Web/HttpApplication.cs:914
  at System.Web.HttpApplication.Start (object) [0x00093] in /home/ubuntu/Downloads/mono-2.8/mcs/class/System.Web/System.Web/HttpApplication.cs:1544
  at System.Web.HttpApplication.System.Web.IHttpHandler.ProcessRequest (System.Web.HttpContext) [0x0001a] in /home/ubuntu/Downloads/mono-2.8/mcs/class/System.Web/System.Web/HttpApplication.cs:1621
  at System.Web.HttpRuntime.Process (System.Web.HttpWorkerRequest) [0x000c5] in /home/ubuntu/Downloads/mono-2.8/mcs/class/System.Web/System.Web/HttpRuntime.cs:522
  at System.Web.HttpRuntime.RealProcessRequest (object) [0x0000e] in /home/ubuntu/Downloads/mono-2.8/mcs/class/System.Web/System.Web/HttpRuntime.cs:447
  at System.Web.HttpRuntime.ProcessRequest (System.Web.HttpWorkerRequest) [0x0002b] in /home/ubuntu/Downloads/mono-2.8/mcs/class/System.Web/System.Web/HttpRuntime.cs:553
  at Mono.WebServer.MonoWorkerRequest.ProcessRequest () [0x0000f] in /home/ubuntu/Downloads/xsp-2.8/src/Mono.WebServer/MonoWorkerRequest.cs:400
  at Mono.WebServer.BaseApplicationHost.ProcessRequest (Mono.WebServer.MonoWorkerRequest) [0x0002d] in /home/ubuntu/Downloads/xsp-2.8/src/Mono.WebServer/BaseApplicationHost.cs:121
  at Mono.WebServer.XSPApplicationHost.ProcessRequest (int,System.Net.IPEndPoint,System.Net.IPEndPoint,string,string,string,string,byte[],string,intptr,Mono.WebServer.SslInformation) [0x0015a] in /home/ubuntu/Downloads/xsp-2.8/src/Mono.WebServer.XSP/XSPApplicationHost.cs:115
  at (wrapper remoting-invoke-with-check) Mono.WebServer.XSPApplicationHost.ProcessRequest (int,System.Net.IPEndPoint,System.Net.IPEndPoint,string,string,string,string,byte[],string,intptr,Mono.WebServer.SslInformation) <IL 0x00045, 0x00407>
  at Mono.WebServer.XSPWorker.RunInternal (object) [0x00103] in /home/ubuntu/Downloads/xsp-2.8/src/Mono.WebServer.XSP/XSPWorker.cs:193
  at (wrapper runtime-invoke) <Module>.runtime_invoke_void__this___object (object,intptr,intptr,intptr) <IL 0x0001e, 0x000b8>

Native stacktrace:

	/usr/local/bin/mono() [0x489c5b]
	/usr/local/bin/mono() [0x4dd18f]
	/lib/libpthread.so.0(+0xfb40) [0x7f601a2a1b40]
	/lib/libc.so.6(+0x128e6b) [0x7f601a037e6b]
	/usr/local/bin/mono() [0x417d74]
	/usr/local/bin/mono() [0x41af1d]
	/usr/local/bin/mono() [0x41c3ef]
	/usr/local/bin/mono() [0x41cbad]
	/usr/local/bin/mono() [0x41d358]
	/usr/local/bin/mono(mono_runtime_invoke+0x4b) [0x504f4b]
	/usr/local/bin/mono() [0x4aeb84]
	/usr/local/bin/mono() [0x4af195]
	/usr/local/bin/mono() [0x4b062d]
	/usr/local/bin/mono() [0x4b21c6]
	[0x7f6017a30ea0]

Debug info from gdb:

ptrace: Operation not permitted.

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

```
which looks like the [ptrace protection]("https://wiki.ubuntu.com/SecurityTeam/Roadmap/KernelHardening#ptrace Protection") kicking in. However, if I turn that off I still get a segfault, just one that doesn't include ptrace: Operation not permitted.
```

Stacktrace:

  at Controllers.HomeController.Index () [0x0001c] in /home/ubuntu/Projects/testweb/testweb/Controllers/HomeController.cs:18
  at (wrapper dynamic-method) System.Runtime.CompilerServices.ExecutionScope.lambda_method (System.Runtime.CompilerServices.ExecutionScope,System.Web.Mvc.ControllerBase,object[]) <IL 0x0000b, 0x00126>
  at System.Web.Mvc.ActionMethodDispatcher.Execute (System.Web.Mvc.ControllerBase,object[]) <IL 0x00008, 0x0004b>
  at System.Web.Mvc.ReflectedActionDescriptor.Execute (System.Web.Mvc.ControllerContext,System.Collections.Generic.IDictionary`2<string, object>) <IL 0x00080, 0x002a3>
  at System.Web.Mvc.ControllerActionInvoker.InvokeActionMethod (System.Web.Mvc.ControllerContext,System.Web.Mvc.ActionDescriptor,System.Collections.Generic.IDictionary`2<string, object>) <IL 0x00003, 0x00061>
  at System.Web.Mvc.ControllerActionInvoker/<InvokeActionMethodWithFilters>c__AnonStoreyB.<>m__E () <IL 0x0002d, 0x000cb>
  at System.Web.Mvc.ControllerActionInvoker.InvokeActionMethodFilter (System.Web.Mvc.IActionFilter,System.Web.Mvc.ActionExecutingContext,System.Func`1<System.Web.Mvc.ActionExecutedContext>) <IL 0x00034, 0x001c6>
  at System.Web.Mvc.ControllerActionInvoker/<InvokeActionMethodWithFilters>c__AnonStoreyB/<InvokeActionMethodWithFilters>c__AnonStoreyC.<>m__12 () <IL 0x00017, 0x0004f>
  at System.Web.Mvc.ControllerActionInvoker.InvokeActionMethodWithFilters (System.Web.Mvc.ControllerContext,System.Collections.Generic.IList`1<System.Web.Mvc.IActionFilter>,System.Web.Mvc.ActionDescriptor,System.Collections.Generic.IDictionary`2<string, object>) <IL 0x00067, 0x00249>
  at System.Web.Mvc.ControllerActionInvoker.InvokeAction (System.Web.Mvc.ControllerContext,string) <IL 0x000ae, 0x003f0>
  at System.Web.Mvc.Controller.ExecuteCore () <IL 0x00035, 0x000f8>
  at System.Web.Mvc.ControllerBase.Execute (System.Web.Routing.RequestContext) <IL 0x00019, 0x000b8>
  at System.Web.Mvc.ControllerBase.System.Web.Mvc.IController.Execute (System.Web.Routing.RequestContext) <IL 0x00002, 0x00045>
  at System.Web.Mvc.MvcHandler.ProcessRequest (System.Web.HttpContextBase) <IL 0x0006c, 0x00221>
  at System.Web.Mvc.MvcHandler.ProcessRequest (System.Web.HttpContext) <IL 0x00009, 0x00084>
  at System.Web.Mvc.MvcHandler.System.Web.IHttpHandler.ProcessRequest (System.Web.HttpContext) <IL 0x00002, 0x00042>
  at System.Web.HttpApplication/<Pipeline>c__Iterator2.MoveNext () [0x00ce5] in /home/ubuntu/Downloads/mono-2.8/mcs/class/System.Web/System.Web/HttpApplication.cs:1344
  at System.Web.HttpApplication.Tick () [0x00000] in /home/ubuntu/Downloads/mono-2.8/mcs/class/System.Web/System.Web/HttpApplication.cs:914
  at System.Web.HttpApplication.Start (object) [0x00093] in /home/ubuntu/Downloads/mono-2.8/mcs/class/System.Web/System.Web/HttpApplication.cs:1544
  at System.Web.HttpApplication.System.Web.IHttpHandler.ProcessRequest (System.Web.HttpContext) [0x0001a] in /home/ubuntu/Downloads/mono-2.8/mcs/class/System.Web/System.Web/HttpApplication.cs:1621
  at System.Web.HttpRuntime.Process (System.Web.HttpWorkerRequest) [0x000c5] in /home/ubuntu/Downloads/mono-2.8/mcs/class/System.Web/System.Web/HttpRuntime.cs:522
  at System.Web.HttpRuntime.RealProcessRequest (object) [0x0000e] in /home/ubuntu/Downloads/mono-2.8/mcs/class/System.Web/System.Web/HttpRuntime.cs:447
  at System.Web.HttpRuntime.ProcessRequest (System.Web.HttpWorkerRequest) [0x0002b] in /home/ubuntu/Downloads/mono-2.8/mcs/class/System.Web/System.Web/HttpRuntime.cs:553
  at Mono.WebServer.MonoWorkerRequest.ProcessRequest () [0x0000f] in /home/ubuntu/Downloads/xsp-2.8/src/Mono.WebServer/MonoWorkerRequest.cs:400
  at Mono.WebServer.BaseApplicationHost.ProcessRequest (Mono.WebServer.MonoWorkerRequest) [0x0002d] in /home/ubuntu/Downloads/xsp-2.8/src/Mono.WebServer/BaseApplicationHost.cs:121
  at Mono.WebServer.XSPApplicationHost.ProcessRequest (int,System.Net.IPEndPoint,System.Net.IPEndPoint,string,string,string,string,byte[],string,intptr,Mono.WebServer.SslInformation) [0x0015a] in /home/ubuntu/Downloads/xsp-2.8/src/Mono.WebServer.XSP/XSPApplicationHost.cs:115
  at (wrapper remoting-invoke-with-check) Mono.WebServer.XSPApplicationHost.ProcessRequest (int,System.Net.IPEndPoint,System.Net.IPEndPoint,string,string,string,string,byte[],string,intptr,Mono.WebServer.SslInformation) <IL 0x00045, 0x00407>
  at Mono.WebServer.XSPWorker.RunInternal (object) [0x00103] in /home/ubuntu/Downloads/xsp-2.8/src/Mono.WebServer.XSP/XSPWorker.cs:193
  at (wrapper runtime-invoke) <Module>.runtime_invoke_void__this___object (object,intptr,intptr,intptr) <IL 0x0001e, 0x000b8>

Native stacktrace:

	/usr/local/bin/mono() [0x489c5b]
	/usr/local/bin/mono() [0x4dd18f]
	/lib/libpthread.so.0(+0xfb40) [0x7f25e8692b40]
	/lib/libc.so.6(+0x128e6b) [0x7f25e8428e6b]
	/usr/local/bin/mono() [0x417d74]
	/usr/local/bin/mono() [0x41af1d]
	/usr/local/bin/mono() [0x41c3ef]
	/usr/local/bin/mono() [0x41cbad]
	/usr/local/bin/mono() [0x41d358]
	/usr/local/bin/mono(mono_runtime_invoke+0x4b) [0x504f4b]
	/usr/local/bin/mono() [0x4aeb84]
	/usr/local/bin/mono() [0x4af195]
	/usr/local/bin/mono() [0x4b062d]
	/usr/local/bin/mono() [0x4b21c6]
	[0x7f25e5e146e8]

Debug info from gdb:

Mono support loaded.
[Thread debugging using libthread_db enabled]
[New Thread 0x7f25e576a710 (LWP 1989)]
[New Thread 0x7f25e5b74710 (LWP 1988)]
[New Thread 0x7f25e4f5a710 (LWP 1985)]
[New Thread 0x7f25e515b710 (LWP 1984)]
[New Thread 0x7f25e5364710 (LWP 1983)]
[New Thread 0x7f25e5565710 (LWP 1982)]
[New Thread 0x7f25e596f710 (LWP 1980)]
[New Thread 0x7f25e5bb9710 (LWP 1962)]
[New Thread 0x7f25e5dbe710 (LWP 1959)]
[New Thread 0x7f25e6d25710 (LWP 1955)]
[New Thread 0x7f25e6f26710 (LWP 1954)]
0x00007f25e868ea9c in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
  12 Thread 0x7f25e6f26710 (LWP 1954)  0x00007f25e8690da0 in sem_wait () from /lib/libpthread.so.0
  11 Thread 0x7f25e6d25710 (LWP 1955)  0x00007f25e8691f8c in recv () from /lib/libpthread.so.0
  10 Thread 0x7f25e5dbe710 (LWP 1959)  0x00007f25e869236d in nanosleep () from /lib/libpthread.so.0
  9 Thread 0x7f25e5bb9710 (LWP 1962)  0x00007f25e83e6f13 in epoll_wait () from /lib/libc.so.6
  8 Thread 0x7f25e596f710 (LWP 1980)  0x00007f25e8690e87 in sem_timedwait () from /lib/libpthread.so.0
  7 Thread 0x7f25e5565710 (LWP 1982)  0x00007f25e869236d in nanosleep () from /lib/libpthread.so.0
  6 Thread 0x7f25e5364710 (LWP 1983)  0x00007f25e8691b8d in read () from /lib/libpthread.so.0
  5 Thread 0x7f25e515b710 (LWP 1984)  0x00007f25e8690e87 in sem_timedwait () from /lib/libpthread.so.0
  4 Thread 0x7f25e4f5a710 (LWP 1985)  0x00007f25e869236d in nanosleep () from /lib/libpthread.so.0
  3 Thread 0x7f25e5b74710 (LWP 1988)  0x00007f25e868ee09 in pthread_cond_timedwait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
  2 Thread 0x7f25e576a710 (LWP 1989)  0x00007f25e8690e87 in sem_timedwait () from /lib/libpthread.so.0
* 1 Thread 0x7f25e9139740 (LWP 1952)  0x00007f25e868ea9c in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0

Thread 12 (Thread 0x7f25e6f26710 (LWP 1954)):
#0  0x00007f25e8690da0 in sem_wait () from /lib/libpthread.so.0
#1  0x00000000005c1518 in mono_sem_wait (sem=0x8df9c0, alertable=0) at mono-semaphore.c:102
#2  0x00000000004e34f2 in finalizer_thread (unused=<value optimized out>) at gc.c:1048
#3  0x00000000005421ff in start_wrapper (data=<value optimized out>) at threads.c:747
#4  0x00000000005ab914 in thread_start_routine (args=0x14207f8) at wthreads.c:285
#5  0x00000000005e1304 in GC_start_routine (arg=0x7f25e8fd4fc0) at pthread_support.c:1392
#6  0x00007f25e868a971 in start_thread () from /lib/libpthread.so.0
#7  0x00007f25e83e691d in clone () from /lib/libc.so.6
#8  0x0000000000000000 in ?? ()

Thread 11 (Thread 0x7f25e6d25710 (LWP 1955)):
#0  0x00007f25e8691f8c in recv () from /lib/libpthread.so.0
#1  0x00000000004a6fce in recv (fd=3, buf=0x7f25e6d24d20, len=11, flags=<value optimized out>) at /usr/include/bits/socket2.h:45
#2  recv_length (fd=3, buf=0x7f25e6d24d20, len=11, flags=<value optimized out>) at debugger-agent.c:949
#3  0x00000000004b4c0a in debugger_thread (arg=<value optimized out>) at debugger-agent.c:6702
#4  0x00000000005ab914 in thread_start_routine (args=0x14208c0) at wthreads.c:285
#5  0x00000000005e1304 in GC_start_routine (arg=0x7f25e8fd4fc0) at pthread_support.c:1392
#6  0x00007f25e868a971 in start_thread () from /lib/libpthread.so.0
#7  0x00007f25e83e691d in clone () from /lib/libc.so.6
#8  0x0000000000000000 in ?? ()

Thread 10 (Thread 0x7f25e5dbe710 (LWP 1959)):
#0  0x00007f25e869236d in nanosleep () from /lib/libpthread.so.0
#1  0x00000000005aa8b4 in SleepEx (ms=<value optimized out>, alertable=1) at wthreads.c:1025
#2  0x0000000000544f0e in ves_icall_System_Threading_Thread_Sleep_internal (ms=1000000) at threads.c:1259
#3  0x00000000419e0c43 in ?? ()
#4  0x00000000000f4240 in ?? ()
#5  0x00000000000f4240 in ?? ()
#6  0x000000004105b000 in ?? ()
#7  0x0000000001dd5010 in ?? ()
#8  0x00000000419e0bb7 in ?? ()
#9  0x00007f25e911f7f8 in ?? ()
#10 0x0000000000000000 in ?? ()

Thread 9 (Thread 0x7f25e5bb9710 (LWP 1962)):
#0  0x00007f25e83e6f13 in epoll_wait () from /lib/libc.so.6
#1  0x0000000000558370 in socket_io_epoll_main (p=<value optimized out>) at threadpool.c:579
#2  0x00000000005421ff in start_wrapper (data=<value optimized out>) at threads.c:747
#3  0x00000000005ab914 in thread_start_routine (args=0x1421540) at wthreads.c:285
#4  0x00000000005e1304 in GC_start_routine (arg=0x7f25e5de2fc0) at pthread_support.c:1392
#5  0x00007f25e868a971 in start_thread () from /lib/libpthread.so.0
#6  0x00007f25e83e691d in clone () from /lib/libc.so.6
#7  0x0000000000000000 in ?? ()

Thread 8 (Thread 0x7f25e596f710 (LWP 1980)):
#0  0x00007f25e8690e87 in sem_timedwait () from /lib/libpthread.so.0
#1  0x00000000005c1623 in mono_sem_timedwait (sem=0x8e08c0, timeout_ms=<value optimized out>, alertable=1) at mono-semaphore.c:72
#2  0x00000000005591f2 in async_invoke_thread (data=0x0) at threadpool.c:1904
#3  0x00000000005421ff in start_wrapper (data=<value optimized out>) at threads.c:747
#4  0x00000000005ab914 in thread_start_routine (args=0x1421860) at wthreads.c:285
#5  0x00000000005e1304 in GC_start_routine (arg=0x7f25e5de2fc0) at pthread_support.c:1392
#6  0x00007f25e868a971 in start_thread () from /lib/libpthread.so.0
#7  0x00007f25e83e691d in clone () from /lib/libc.so.6
#8  0x0000000000000000 in ?? ()

Thread 7 (Thread 0x7f25e5565710 (LWP 1982)):
#0  0x00007f25e869236d in nanosleep () from /lib/libpthread.so.0
#1  0x00000000005aa8b4 in SleepEx (ms=<value optimized out>, alertable=1) at wthreads.c:1025
#2  0x0000000000557494 in monitor_thread (data=<value optimized out>) at threadpool.c:1150
#3  0x00000000005421ff in start_wrapper (data=<value optimized out>) at threads.c:747
#4  0x00000000005ab914 in thread_start_routine (args=0x1421b80) at wthreads.c:285
#5  0x00000000005e1304 in GC_start_routine (arg=0x7f25e5de2fc0) at pthread_support.c:1392
#6  0x00007f25e868a971 in start_thread () from /lib/libpthread.so.0
#7  0x00007f25e83e691d in clone () from /lib/libc.so.6
#8  0x0000000000000000 in ?? ()

Thread 6 (Thread 0x7f25e5364710 (LWP 1983)):
#0  0x00007f25e8691b8d in read () from /lib/libpthread.so.0
#1  0x0000000000489de7 in read (signal=<value optimized out>, ctx=<value optimized out>) at /usr/include/bits/unistd.h:45
#2  mono_handle_native_sigsegv (signal=<value optimized out>, ctx=<value optimized out>) at mini-exceptions.c:1935
#3  0x00000000004dd18f in mono_arch_handle_altstack_exception (sigctx=0x7f25e515fc40, fault_addr=<value optimized out>, stack_ovf=0) at exceptions-amd64.c:926
#4  <signal handler called>
#5  0x00007f25e8428e6b in ?? () from /lib/libc.so.6
#6  0x0000000000417d74 in mono_postprocess_patches (cfg=0x26b70f0) at mini.c:3158
#7  mono_codegen (cfg=0x26b70f0) at mini.c:3434
#8  0x000000000041af1d in mini_method_compile (method=<value optimized out>, opts=<value optimized out>, domain=<value optimized out>, run_cctors=<value optimized out>, compile_aot=<value optimized out>, parts=<value optimized out>) at mini.c:4557
#9  0x000000000041c3ef in mono_jit_compile_method_inner (method="<Module>:runtime_invoke_int__this__ ()", opt=51472767, ex=0x7f25e5361d60) at mini.c:4821
#10 mono_jit_compile_method_with_opt (method="<Module>:runtime_invoke_int__this__ ()", opt=51472767, ex=0x7f25e5361d60) at mini.c:5029
#11 0x000000000041cbad in mono_jit_compile_method (method=Traceback (most recent call last):
  File "/usr/local/bin/mono-gdb.py", line 153, in to_string
    class_name = stringify_class_name (klass ["name_space"].string (), klass ["name"].string ())
RuntimeError: Cannot access memory at address 0x61765f77656e5fc1
) at mini.c:5054
#12 0x000000000041d358 in mono_jit_runtime_invoke (method="System.Collections.Generic.Dictionary`2:get_Count ()", obj=0x7f25e443aaa8, params=<value optimized out>, exc=0x7f25e5362120) at mini.c:5315
#13 0x0000000000504f4b in mono_runtime_invoke (method="System.Collections.Generic.Dictionary`2:get_Count ()", obj=0x7f25e443aaa8, params=0x7f25e5361f60, exc=0x7f25e5362120) at object.c:2709
#14 0x00000000004aeb84 in do_invoke_method (tls=<value optimized out>, buf=<value optimized out>, invoke=0x26b6e40) at debugger-agent.c:4806
#15 0x00000000004af195 in invoke_method () at debugger-agent.c:4884
#16 suspend_current () at debugger-agent.c:2276
#17 0x00000000004b062d in process_event (event=EVENT_KIND_BREAKPOINT, arg=<value optimized out>, il_offset=<value optimized out>, ctx=<value optimized out>, events=<value optimized out>, suspend_policy=2) at debugger-agent.c:2805
#18 0x00000000004b21c6 in process_breakpoint_inner () at debugger-agent.c:3618
#19 process_breakpoint () at debugger-agent.c:3636
#20 0x00007f25e5e146e8 in ?? ()
#21 0x000000004105b000 in ?? ()
#22 0x00007f25e5362560 in ?? ()
#23 0x00007f25e4372167 in ?? ()
#24 0x00007f25e4486300 in ?? ()
#25 0x00007f25e5e146e8 in ?? ()
#26 0x00007f25e60b58c0 in ?? ()
#27 0x000000004105b000 in ?? ()
#28 0x00007f25e5e146e8 in ?? ()
#29 0x00007f25e5e146e8 in ?? ()
#30 0x00007f25e5e146e8 in ?? ()
#31 0x00007f25e00b10f8 in ?? ()
#32 0x0000000000000000 in ?? ()

Thread 5 (Thread 0x7f25e515b710 (LWP 1984)):
#0  0x00007f25e8690e87 in sem_timedwait () from /lib/libpthread.so.0
#1  0x00000000005c1623 in mono_sem_timedwait (sem=0x8e08c0, timeout_ms=<value optimized out>, alertable=1) at mono-semaphore.c:72
#2  0x00000000005591f2 in async_invoke_thread (data=0x0) at threadpool.c:1904
#3  0x00000000005421ff in start_wrapper (data=<value optimized out>) at threads.c:747
#4  0x00000000005ab914 in thread_start_routine (args=0x1421f68) at wthreads.c:285
#5  0x00000000005e1304 in GC_start_routine (arg=0x7f25e602fce8) at pthread_support.c:1392
#6  0x00007f25e868a971 in start_thread () from /lib/libpthread.so.0
#7  0x00007f25e83e691d in clone () from /lib/libc.so.6
#8  0x0000000000000000 in ?? ()

Thread 4 (Thread 0x7f25e4f5a710 (LWP 1985)):
#0  0x00007f25e869236d in nanosleep () from /lib/libpthread.so.0
#1  0x00000000005aa8b4 in SleepEx (ms=<value optimized out>, alertable=1) at wthreads.c:1025
#2  0x0000000000544f0e in ves_icall_System_Threading_Thread_Sleep_internal (ms=750) at threads.c:1259
#3  0x00000000419e0c43 in ?? ()
#4  0x88cd4238c338f680 in ?? ()
#5  0x00000000000002ee in ?? ()
#6  0x000000004105b000 in ?? ()
#7  0x0000000001ea8730 in ?? ()
#8  0x00007f25e4f59a80 in ?? ()
#9  0x00007f25e5e17940 in ?? ()
#10 0x00007f25e4f59980 in ?? ()
#11 0x0000000001ded810 in ?? ()
#12 0x00007f25e4f59950 in ?? ()
#13 0x00007f25e4f598e0 in ?? ()
#14 0x00007f25e911f7f8 in ?? ()
#15 0x0000000000000000 in ?? ()

Thread 3 (Thread 0x7f25e5b74710 (LWP 1988)):
#0  0x00007f25e868ee09 in pthread_cond_timedwait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
#1  0x00000000005a590d in _wapi_handle_timedwait_signal_handle (handle=0x43b, timeout=0x7f25e5b73820, alertable=1, poll=-1) at handles.c:1636
#2  0x00000000005a65c5 in WaitForSingleObjectEx (handle=<value optimized out>, timeout=<value optimized out>, alertable=<value optimized out>) at wait.c:205
#3  0x0000000000590e33 in ves_icall_System_Threading_Monitor_Monitor_wait (obj=0x7f25e43f8bd0, ms=109986) at monitor.c:1351
#4  0x000000004168dd9b in ?? ()
#5  0x000000000001ada2 in ?? ()
#6  0x00007f25e43f8bd0 in ?? ()
#7  0x000000004105b000 in ?? ()
#8  0x0000000002200500 in ?? ()
#9  0x000000004168dd0b in ?? ()
#10 0x00007f25e911f7f8 in ?? ()
#11 0x0000000000000000 in ?? ()

Thread 2 (Thread 0x7f25e576a710 (LWP 1989)):
#0  0x00007f25e8690e87 in sem_timedwait () from /lib/libpthread.so.0
#1  0x00000000005c1623 in mono_sem_timedwait (sem=0x8e07e0, timeout_ms=<value optimized out>, alertable=1) at mono-semaphore.c:72
#2  0x00000000005591f2 in async_invoke_thread (data=0x0) at threadpool.c:1904
#3  0x00000000005421ff in start_wrapper (data=<value optimized out>) at threads.c:747
#4  0x00000000005ab914 in thread_start_routine (args=0x1423228) at wthreads.c:285
#5  0x00000000005e1304 in GC_start_routine (arg=0x7f25e602fee0) at pthread_support.c:1392
#6  0x00007f25e868a971 in start_thread () from /lib/libpthread.so.0
#7  0x00007f25e83e691d in clone () from /lib/libc.so.6
#8  0x0000000000000000 in ?? ()

Thread 1 (Thread 0x7f25e9139740 (LWP 1952)):
#0  0x00007f25e868ea9c in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
#1  0x00000000005a59c9 in _wapi_handle_timedwait_signal_handle (handle=0x400, timeout=0x0, alertable=1, poll=-1) at handles.c:1638
#2  0x00000000005a6d79 in WaitForMultipleObjectsEx (numobjects=2, handles=0x7fffb9625a60, waitall=<value optimized out>, timeout=<value optimized out>, alertable=<value optimized out>) at wait.c:722
#3  0x0000000000544c4b in wait_for_tids_or_state_change () at threads.c:2802
#4  mono_thread_manage () at threads.c:3017
#5  0x00000000004686d1 in mono_main (argc=<value optimized out>, argv=<value optimized out>) at driver.c:1837
#6  0x00007f25e831ed8e in __libc_start_main () from /lib/libc.so.6
#7  0x0000000000412449 in _start ()

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

```

I suppose that whatever is causing the problem, the ptrace thing is a symptom rather than a cause, though I haven't the foggiest what that might hint at.

---

### Post by terranim on 2010-10-26
I am seeing the exact same problem on a fresh Kubuntu 10.10 x64 (HP Laptop) with mono 2.8 built from source. 

When debugging using the default project generated by Monodevelop, as suggested by Throctukes, I get the operation not permitted problem until I disable the ptrace_scope option and then I get the full stacktrace as shown above.

Regards,
Dan

---

### Post by terranim on 2010-10-26
Based on a suggestion by Throctukes I performed the following test:

I setup a VM based on Kubuntu 10.04 (Lucid) x64 with Mono 2.8, XSP and MonoDevelop 2.4 built from sources. I created it on an external hard-disk and then ran it on two different machines:

1. Dell Vostro 1700 with an Intel Centrino Duo processor: Debugging the test project was successful, it hit the breakpoint and I could examine the local variables.

2. HP Pavilion with an i7 Quad core processor: Debugging the test project failed with the same problems described by Throctukes.

Since both machines were running the exact same VM and debugging the same project, it would suggest there is a hardware issue and since VMware Player takes advantage of processor capabilities, the processor is the most likely culprit.

Throctukes found that a Karmic machine running Mono 2.8 did not suffer from the same problem, so perhaps a kernel revision (that takes advantage of newer processor capabilities) between Karmic and Lucid has caused the problem?

Regards,
Dan

---

### Post by Throctukes on 2010-10-26
The machine I've been having trouble with is also packing an i7 processor.

Also, to broaden the problem slightly, I re-tested a console app just to make sure this really was an ASP.Net project only issue. I had already tested this, but at this point I'm beginning to question everything I've already done. And so it turns out that even console projects segfault - I just hadn't hovered on the right area before. Oops. If I hover over "Console" in Console.WriteLine("Hello World") in the simple console app monodevelop generates, I get a segfault with the same ptrace: operation not permitted message I reported above. Hover elsewhere and it seems to work fine - I can also hover ints that I add into the method.

So yeah, not *just* an issue with ASP.net projects - it seems like the soft debugger is full-on broken on this hardware.

I'm putting together another Karmic VM at the moment, and I'll try to figure out which kernel this issue begins with. I also just want to confirm to myself that Karmic even works.

---

### Post by Throctukes on 2010-10-26
Yes, karmic does work. Between a karmic and a lucid VM I've so far checked four kernels:

These work:
```
2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux
2.6.31-22-generic #67-Ubuntu SMP Sat Oct 16 18:51:35 UTC 2010 x86_64 GNU/Linux
```
These don't work:
```
2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux
2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:52:42 UTC 2010 x86_64 GNU/Linux
```

---

### Post by terranim on 2010-10-26
It doesn't appear to be a kernel specific issue. I just downgraded my Lucid VM to kernel 2.6.31-22-generic from the Karmic repositories and it still crashes!

The hunt continues...

---

### Post by Throctukes on 2010-10-26
In light of that, I took my working Karmic VM and used dpkg to force the install of libc6 and libglib2.0 from Lucid... 

...and here's the stacktrace from the ASP.net app when I try to debug:
```

Resolved pending breakpoint at 'HomeController.cs:16' to ActionResult Controllers.HomeController:Index ():0.
Stacktrace:

  at Controllers.HomeController.Index () [0x0001c] in /home/ubuntu/Projects/testweb/testweb/Controllers/HomeController.cs:18
  at (wrapper dynamic-method) System.Runtime.CompilerServices.ExecutionScope.lambda_method (System.Runtime.CompilerServices.ExecutionScope,System.Web.Mvc.ControllerBase,object[]) <IL 0x0000b, 0x00118>
  at System.Web.Mvc.ActionMethodDispatcher.Execute (System.Web.Mvc.ControllerBase,object[]) <IL 0x00008, 0x0004b>
  at System.Web.Mvc.ReflectedActionDescriptor.Execute (System.Web.Mvc.ControllerContext,System.Collections.Generic.IDictionary`2<string, object>) <IL 0x00080, 0x002a3>
  at System.Web.Mvc.ControllerActionInvoker.InvokeActionMethod (System.Web.Mvc.ControllerContext,System.Web.Mvc.ActionDescriptor,System.Collections.Generic.IDictionary`2<string, object>) <IL 0x00003, 0x00061>
  at System.Web.Mvc.ControllerActionInvoker/<InvokeActionMethodWithFilters>c__AnonStoreyB.<>m__E () <IL 0x0002d, 0x000cb>
  at System.Web.Mvc.ControllerActionInvoker.InvokeActionMethodFilter (System.Web.Mvc.IActionFilter,System.Web.Mvc.ActionExecutingContext,System.Func`1<System.Web.Mvc.ActionExecutedContext>) <IL 0x00034, 0x001c6>
  at System.Web.Mvc.ControllerActionInvoker/<InvokeActionMethodWithFilters>c__AnonStoreyB/<InvokeActionMethodWithFilters>c__AnonStoreyC.<>m__12 () <IL 0x00017, 0x0004f>
  at System.Web.Mvc.ControllerActionInvoker.InvokeActionMethodWithFilters (System.Web.Mvc.ControllerContext,System.Collections.Generic.IList`1<System.Web.Mvc.IActionFilter>,System.Web.Mvc.ActionDescriptor,System.Collections.Generic.IDictionary`2<string, object>) <IL 0x00067, 0x00249>
  at System.Web.Mvc.ControllerActionInvoker.InvokeAction (System.Web.Mvc.ControllerContext,string) <IL 0x000ae, 0x003f0>
  at System.Web.Mvc.Controller.ExecuteCore () <IL 0x00035, 0x000f8>
  at System.Web.Mvc.ControllerBase.Execute (System.Web.Routing.RequestContext) <IL 0x00019, 0x000b8>
  at System.Web.Mvc.ControllerBase.System.Web.Mvc.IController.Execute (System.Web.Routing.RequestContext) <IL 0x00002, 0x00045>
  at System.Web.Mvc.MvcHandler.ProcessRequest (System.Web.HttpContextBase) <IL 0x0006c, 0x00221>
  at System.Web.Mvc.MvcHandler.ProcessRequest (System.Web.HttpContext) <IL 0x00009, 0x00084>
  at System.Web.Mvc.MvcHandler.System.Web.IHttpHandler.ProcessRequest (System.Web.HttpContext) <IL 0x00002, 0x00042>
  at System.Web.HttpApplication/<Pipeline>c__Iterator2.MoveNext () [0x00ce5] in /home/ubuntu/Downloads/mono-2.8/mcs/class/System.Web/System.Web/HttpApplication.cs:1344
  at System.Web.HttpApplication.Tick () [0x00000] in /home/ubuntu/Downloads/mono-2.8/mcs/class/System.Web/System.Web/HttpApplication.cs:914
  at System.Web.HttpApplication.Start (object) [0x00093] in /home/ubuntu/Downloads/mono-2.8/mcs/class/System.Web/System.Web/HttpApplication.cs:1544
  at System.Web.HttpApplication.System.Web.IHttpHandler.ProcessRequest (System.Web.HttpContext) [0x0001a] in /home/ubuntu/Downloads/mono-2.8/mcs/class/System.Web/System.Web/HttpApplication.cs:1621
  at System.Web.HttpRuntime.Process (System.Web.HttpWorkerRequest) [0x000c5] in /home/ubuntu/Downloads/mono-2.8/mcs/class/System.Web/System.Web/HttpRuntime.cs:522
  at System.Web.HttpRuntime.RealProcessRequest (object) [0x0000e] in /home/ubuntu/Downloads/mono-2.8/mcs/class/System.Web/System.Web/HttpRuntime.cs:447
  at System.Web.HttpRuntime.ProcessRequest (System.Web.HttpWorkerRequest) [0x0002b] in /home/ubuntu/Downloads/mono-2.8/mcs/class/System.Web/System.Web/HttpRuntime.cs:553
  at Mono.WebServer.MonoWorkerRequest.ProcessRequest () [0x0000f] in /home/ubuntu/Downloads/xsp-2.8/src/Mono.WebServer/MonoWorkerRequest.cs:400
  at Mono.WebServer.BaseApplicationHost.ProcessRequest (Mono.WebServer.MonoWorkerRequest) [0x0002d] in /home/ubuntu/Downloads/xsp-2.8/src/Mono.WebServer/BaseApplicationHost.cs:121
  at Mono.WebServer.XSPApplicationHost.ProcessRequest (int,System.Net.IPEndPoint,System.Net.IPEndPoint,string,string,string,string,byte[],string,intptr,Mono.WebServer.SslInformation) [0x0015a] in /home/ubuntu/Downloads/xsp-2.8/src/Mono.WebServer.XSP/XSPApplicationHost.cs:115
  at (wrapper remoting-invoke-with-check) Mono.WebServer.XSPApplicationHost.ProcessRequest (int,System.Net.IPEndPoint,System.Net.IPEndPoint,string,string,string,string,byte[],string,intptr,Mono.WebServer.SslInformation) <IL 0x00045, 0x00407>
  at Mono.WebServer.XSPWorker.RunInternal (object) [0x00103] in /home/ubuntu/Downloads/xsp-2.8/src/Mono.WebServer.XSP/XSPWorker.cs:193
  at (wrapper runtime-invoke) <Module>.runtime_invoke_void__this___object (object,intptr,intptr,intptr) <IL 0x0001e, 0x000b8>

Native stacktrace:

	/usr/local/bin/mono() [0x48bd6b]
	/usr/local/bin/mono() [0x4dee2f]
	/lib/libpthread.so.0(+0xf8f0) [0x7f294c6418f0]
	/lib/libc.so.6(+0x128adb) [0x7f294c3d7adb]
	/usr/local/bin/mono() [0x41a524]
	/usr/local/bin/mono() [0x41c20d]
	/usr/local/bin/mono() [0x41d6df]
	/usr/local/bin/mono() [0x41de9d]
	/usr/local/bin/mono() [0x41e5df]
	/usr/local/bin/mono(mono_runtime_invoke+0x4b) [0x50821b]
	/usr/local/bin/mono() [0x4b200e]
	/usr/local/bin/mono() [0x4b2625]
	/usr/local/bin/mono() [0x4b31cd]
	/usr/local/bin/mono() [0x4b4386]
	[0x7f294a1791a0]

Debug info from gdb:

Thread started: 
Mono support loaded.
warning: (Internal error: pc 0xf4240 in read in psymtab, but not in symtab.)

warning: (Internal error: pc 0xf423f in read in psymtab, but not in symtab.)

warning: (Internal error: pc 0xf423f in read in psymtab, but not in symtab.)

warning: (Internal error: pc 0xf423f in read in psymtab, but not in symtab.)

warning: (Internal error: pc 0xf423f in read in psymtab, but not in symtab.)

warning: (Internal error: pc 0xf423f in read in psymtab, but not in symtab.)

warning: (Internal error: pc 0xf4240 in read in psymtab, but not in symtab.)

warning: (Internal error: pc 0xf423f in read in psymtab, but not in symtab.)

warning: (Internal error: pc 0xf423f in read in psymtab, but not in symtab.)

warning: (Internal error: pc 0xf423f in read in psymtab, but not in symtab.)

warning: (Internal error: pc 0xf423f in read in psymtab, but not in symtab.)

[Thread debugging using libthread_db enabled]
[New Thread 0x7f2949adf710 (LWP 3842)]
[New Thread 0x7f2949ee5710 (LWP 3838)]
[New Thread 0x7f29492cb710 (LWP 3835)]
[New Thread 0x7f29494d0710 (LWP 3834)]
[New Thread 0x7f29496d9710 (LWP 3833)]
[New Thread 0x7f29498da710 (LWP 3832)]
[New Thread 0x7f2949ce4710 (LWP 3830)]
[New Thread 0x7f2949f26710 (LWP 3815)]
[New Thread 0x7f294a127710 (LWP 3813)]
[New Thread 0x7f294b071710 (LWP 3808)]
[New Thread 0x7f294b272710 (LWP 3807)]
0x00007f294c63d85c in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
  12 Thread 0x7f294b272710 (LWP 3807)  0x00007f294c63fb50 in sem_wait () from /lib/libpthread.so.0
  11 Thread 0x7f294b071710 (LWP 3808)  0x00007f294c640d3c in recv () from /lib/libpthread.so.0
  10 Thread 0x7f294a127710 (LWP 3813)  0x00007f294c64111d in nanosleep () from /lib/libpthread.so.0
  9 Thread 0x7f2949f26710 (LWP 3815)  0x00007f294c395d03 in epoll_wait () from /lib/libc.so.6
  8 Thread 0x7f2949ce4710 (LWP 3830)  0x00007f294c63fc37 in sem_timedwait ()
   from /lib/libpthread.so.0
  7 Thread 0x7f29498da710 (LWP 3832)  0x00007f294c64111d in nanosleep () from /lib/libpthread.so.0
  6 Thread 0x7f29496d9710 (LWP 3833)  0x00007f294c64093d in read () from /lib/libpthread.so.0
  5 Thread 0x7f29494d0710 (LWP 3834)  0x00007f294c64111d in nanosleep () from /lib/libpthread.so.0
  4 Thread 0x7f29492cb710 (LWP 3835)  0x00007f294c63fc37 in sem_timedwait ()
   from /lib/libpthread.so.0
  3 Thread 0x7f2949ee5710 (LWP 3838)  0x00007f294c63dbc9 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
  2 Thread 0x7f2949adf710 (LWP 3842)  0x00007f294c63d85c in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
* 1 Thread 0x7f294d0e8740 (LWP 3806)  0x00007f294c63d85c in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0

Thread 12 (Thread 0x7f294b272710 (LWP 3807)):
#0  0x00007f294c63fb50 in sem_wait () from /lib/libpthread.so.0
#1  0x00000000005c57c8 in mono_sem_wait (sem=0x8e2200, alertable=0) at mono-semaphore.c:102
#2  0x00000000005370a2 in finalizer_thread (unused=<value optimized out>) at gc.c:1048
#3  0x0000000000597c1c in start_wrapper (data=<value optimized out>) at threads.c:747
#4  0x00000000005acc34 in thread_start_routine (args=0x1baa718) at wthreads.c:285
#5  0x00000000005d7ae7 in GC_start_routine (arg=0x7f294cf6afc0) at pthread_support.c:1392
#6  0x00007f294c6389ca in start_thread () from /lib/libpthread.so.0
#7  0x00007f294c39570d in clone () from /lib/libc.so.6
#8  0x0000000000000000 in ?? ()

Thread 11 (Thread 0x7f294b071710 (LWP 3808)):
#0  0x00007f294c640d3c in recv () from /lib/libpthread.so.0
#1  0x00000000004a904e in recv (fd=3, buf=0x7f294b070d20, len=11, flags=<value optimized out>)
    at /usr/include/bits/socket2.h:45
#2  recv_length (fd=3, buf=0x7f294b070d20, len=11, flags=<value optimized out>)
    at debugger-agent.c:949
#3  0x00000000004b6933 in debugger_thread (arg=<value optimized out>) at debugger-agent.c:6702
#4  0x00000000005acc34 in thread_start_routine (args=0x1baa7e0) at wthreads.c:285
#5  0x00000000005d7ae7 in GC_start_routine (arg=0x7f294cf6afc0) at pthread_support.c:1392
#6  0x00007f294c6389ca in start_thread () from /lib/libpthread.so.0
#7  0x00007f294c39570d in clone () from /lib/libc.so.6
#8  0x0000000000000000 in ?? ()

Thread 10 (Thread 0x7f294a127710 (LWP 3813)):
#0  0x00007f294c64111d in nanosleep () from /lib/libpthread.so.0
#1  0x00000000005abbd4 in SleepEx (ms=<value optimized out>, alertable=1) at wthreads.c:1025
#2  0x000000000059a8ce in ves_icall_System_Threading_Thread_Sleep_internal (ms=1000000)
    at threads.c:1259
#3  0x0000000041a0fc43 in ?? ()
#4  0x00000000000f4240 in ?? ()
#5  0x00000000000f4240 in ?? ()
#6  0x0000000041ad4000 in ?? ()
#7  0x0000000002571110 in ?? ()
#8  0x0000000041a0fbb7 in ?? ()
#9  0x00007f294cf907f8 in ?? ()
#10 0x0000000000000000 in ?? ()

Thread 9 (Thread 0x7f2949f26710 (LWP 3815)):
#0  0x00007f294c395d03 in epoll_wait () from /lib/libc.so.6
#1  0x00000000005a5a80 in socket_io_epoll_main (p=<value optimized out>) at threadpool.c:579
#2  0x0000000000597c1c in start_wrapper (data=<value optimized out>) at threads.c:747
#3  0x00000000005acc34 in thread_start_routine (args=0x1bab460) at wthreads.c:285
#4  0x00000000005d7ae7 in GC_start_routine (arg=0x7f294a14afc0) at pthread_support.c:1392
#5  0x00007f294c6389ca in start_thread () from /lib/libpthread.so.0
#6  0x00007f294c39570d in clone () from /lib/libc.so.6
#7  0x0000000000000000 in ?? ()

Thread 8 (Thread 0x7f2949ce4710 (LWP 3830)):
#0  0x00007f294c63fc37 in sem_timedwait () from /lib/libpthread.so.0
#1  0x00000000005c58d3 in mono_sem_timedwait (sem=0x8e3180, timeout_ms=<value optimized out>, 
    alertable=1) at mono-semaphore.c:72
#2  0x00000000005a3e72 in async_invoke_thread (data=0x0) at threadpool.c:1904
#3  0x0000000000597c1c in start_wrapper (data=<value optimized out>) at threads.c:747
#4  0x00000000005acc34 in thread_start_routine (args=0x1bab780) at wthreads.c:285
#5  0x00000000005d7ae7 in GC_start_routine (arg=0x7f294a14afc0) at pthread_support.c:1392
#6  0x00007f294c6389ca in start_thread () from /lib/libpthread.so.0
#7  0x00007f294c39570d in clone () from /lib/libc.so.6
#8  0x0000000000000000 in ?? ()

Thread 7 (Thread 0x7f29498da710 (LWP 3832)):
#0  0x00007f294c64111d in nanosleep () from /lib/libpthread.so.0
#1  0x00000000005abbd4 in SleepEx (ms=<value optimized out>, alertable=1) at wthreads.c:1025
#2  0x00000000005a29d4 in monitor_thread (data=<value optimized out>) at threadpool.c:1150
#3  0x0000000000597c1c in start_wrapper (data=<value optimized out>) at threads.c:747
#4  0x00000000005acc34 in thread_start_routine (args=0x1babaa0) at wthreads.c:285
#5  0x00000000005d7ae7 in GC_start_routine (arg=0x7f294a14afc0) at pthread_support.c:1392
#6  0x00007f294c6389ca in start_thread () from /lib/libpthread.so.0
#7  0x00007f294c39570d in clone () from /lib/libc.so.6
#8  0x0000000000000000 in ?? ()

Thread 6 (Thread 0x7f29496d9710 (LWP 3833)):
#0  0x00007f294c64093d in read () from /lib/libpthread.so.0
#1  0x000000000048bef7 in read (signal=<value optimized out>, ctx=<value optimized out>)
    at /usr/include/bits/unistd.h:45
#2  mono_handle_native_sigsegv (signal=<value optimized out>, ctx=<value optimized out>)
    at mini-exceptions.c:1935
#3  0x00000000004dee2f in mono_arch_handle_altstack_exception (sigctx=0x7f29494d8c40, 
    fault_addr=<value optimized out>, stack_ovf=0) at exceptions-amd64.c:926
#4  <signal handler called>
#5  0x00007f294c3d7adb in ?? () from /lib/libc.so.6
#6  0x000000000041a524 in mono_postprocess_patches (cfg=0x2ee1b60) at mini.c:3158
#7  mono_codegen (cfg=0x2ee1b60) at mini.c:3434
#8  0x000000000041c20d in mini_method_compile (method=<value optimized out>, 
    opts=<value optimized out>, domain=<value optimized out>, run_cctors=<value optimized out>, 
    compile_aot=<value optimized out>, parts=<value optimized out>) at mini.c:4557
#9  0x000000000041d6df in mono_jit_compile_method_inner (method=
    "<Module>:runtime_invoke_int__this__ ()", opt=51472767, ex=0x7f29496d6d80) at mini.c:4821
#10 mono_jit_compile_method_with_opt (method="<Module>:runtime_invoke_int__this__ ()", opt=
    51472767, ex=0x7f29496d6d80) at mini.c:5029
#11 0x000000000041de9d in mono_jit_compile_method (method=Traceback (most recent call last):
  File "/usr/local/bin/mono-gdb.py", line 153, in to_string
    class_name = stringify_class_name (klass ["name_space"].string (), klass ["name"].string ())
RuntimeError: Cannot access memory at address 0x61765f77656e5fc1
) at mini.c:5054
#12 0x000000000041e5df in mono_jit_runtime_invoke (method=
    "System.Collections.Generic.Dictionary`2:get_Count ()", obj=0x7f29487baaa8, 
    params=<value optimized out>, exc=0x7f29496d7130) at mini.c:5315
#13 0x000000000050821b in mono_runtime_invoke (method=
    "System.Collections.Generic.Dictionary`2:get_Count ()", obj=0x7f29487baaa8, params=
    0x7f29496d6f70, exc=0x7f29496d7130) at object.c:2709
#14 0x00000000004b200e in do_invoke_method (tls=<value optimized out>, buf=<value optimized out>, 
    invoke=0x2ef4530) at debugger-agent.c:4806
#15 0x00000000004b2625 in invoke_method () at debugger-agent.c:4884
#16 suspend_current () at debugger-agent.c:2276
#17 0x00000000004b31cd in process_event (event=EVENT_KIND_BREAKPOINT, arg=<value optimized out>, 
    il_offset=<value optimized out>, ctx=<value optimized out>, events=<value optimized out>, 
    suspend_policy=2) at debugger-agent.c:2805
#18 0x00000000004b4386 in process_breakpoint_inner () at debugger-agent.c:3618
#19 process_breakpoint () at debugger-agent.c:3636
#20 0x00007f294a1791a0 in ?? ()
#21 0x0000000041ad4000 in ?? ()
#22 0x00007f29496d7570 in ?? ()
#23 0x00007f29486d9159 in ?? ()
#24 0x00007f29488052e0 in ?? ()
#25 0x00007f294a1791a0 in ?? ()
#26 0x00007f294a14a770 in ?? ()
#27 0x0000000041ad4000 in ?? ()
#28 0x00007f294a1791a0 in ?? ()
#29 0x00007f294a1791a0 in ?? ()
#30 0x00007f294a1791a0 in ?? ()
#31 0x0000000002a09dd8 in ?? ()
#32 0x0000000000000000 in ?? ()

Thread 5 (Thread 0x7f29494d0710 (LWP 3834)):
#0  0x00007f294c64111d in nanosleep () from /lib/libpthread.so.0
#1  0x00000000005abbd4 in SleepEx (ms=<value optimized out>, alertable=1) at wthreads.c:1025
#2  0x000000000059a8ce in ves_icall_System_Threading_Thread_Sleep_internal (ms=750)
    at threads.c:1259
#3  0x0000000041a0fc43 in ?? ()
#4  0x88cd4300bed81080 in ?? ()
#5  0x00000000000002ee in ?? ()
#6  0x0000000041ad4000 in ?? ()
#7  0x0000000002628830 in ?? ()
#8  0x00007f29494cfa90 in ?? ()
#9  0x00007f294a17c640 in ?? ()
#10 0x00007f29494cf990 in ?? ()
#11 0x000000000255ddb0 in ?? ()
#12 0x00007f29494cf960 in ?? ()
#13 0x00007f29494cf8f0 in ?? ()
#14 0x00007f294cf907f8 in ?? ()
#15 0x0000000000000000 in ?? ()

Thread 4 (Thread 0x7f29492cb710 (LWP 3835)):
#0  0x00007f294c63fc37 in sem_timedwait () from /lib/libpthread.so.0
#1  0x00000000005c58d3 in mono_sem_timedwait (sem=0x8e3180, timeout_ms=<value optimized out>, 
    alertable=1) at mono-semaphore.c:72
#2  0x00000000005a3e72 in async_invoke_thread (data=0x0) at threadpool.c:1904
#3  0x0000000000597c1c in start_wrapper (data=<value optimized out>) at threads.c:747
#4  0x00000000005acc34 in thread_start_routine (args=0x1bac338) at wthreads.c:285
#5  0x00000000005d7ae7 in GC_start_routine (arg=0x7f294a1286c8) at pthread_support.c:1392
#6  0x00007f294c6389ca in start_thread () from /lib/libpthread.so.0
#7  0x00007f294c39570d in clone () from /lib/libc.so.6
#8  0x0000000000000000 in ?? ()

Thread 3 (Thread 0x7f2949ee5710 (LWP 3838)):
#0  0x00007f294c63dbc9 in pthread_cond_timedwait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
#1  0x00000000005aa375 in _wapi_handle_timedwait_signal_handle (handle=0x43a, timeout=
    0x7f2949ee4830, alertable=1, poll=-1) at handles.c:1636
#2  0x00000000005af721 in WaitForSingleObjectEx (handle=<value optimized out>, 
    timeout=<value optimized out>, alertable=<value optimized out>) at wait.c:205
#3  0x0000000000522543 in ves_icall_System_Threading_Monitor_Monitor_wait (obj=0x7f2948778ba0, ms=
    109994) at monitor.c:1351
#4  0x00000000401d780b in ?? ()
#5  0x000000000001adaa in ?? ()
#6  0x00007f2948778ba0 in ?? ()
#7  0x0000000041ad4000 in ?? ()
#8  0x0000000002a52550 in ?? ()
#9  0x00000000401d777b in ?? ()
#10 0x00007f294cf907f8 in ?? ()
#11 0x0000000000000000 in ?? ()

Thread 2 (Thread 0x7f2949adf710 (LWP 3842)):
#0  0x00007f294c63d85c in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
#1  0x00000000004b249f in suspend_current () at debugger-agent.c:2257
#2  0x00000000004b31cd in process_event (event=EVENT_KIND_THREAD_START, arg=<value optimized out>, 
    il_offset=<value optimized out>, ctx=<value optimized out>, events=<value optimized out>, 
    suspend_policy=2) at debugger-agent.c:2805
#3  0x00000000004b356d in process_profiler_event (event=EVENT_KIND_THREAD_START, arg=0x7f294a1942e0)
    at debugger-agent.c:2825
#4  0x00000000004b4eee in thread_startup (prof=<value optimized out>, tid=139815306524432)
    at debugger-agent.c:2896
#5  0x0000000000510b33 in mono_profiler_thread_start (tid=139815306524432) at profiler.c:529
#6  0x0000000000597c0b in start_wrapper (data=<value optimized out>) at threads.c:743
#7  0x00000000005acc34 in thread_start_routine (args=0x1bad080) at wthreads.c:285
#8  0x00000000005d7ae7 in GC_start_routine (arg=0x7f294a128a80) at pthread_support.c:1392
#9  0x00007f294c6389ca in start_thread () from /lib/libpthread.so.0
#10 0x00007f294c39570d in clone () from /lib/libc.so.6
#11 0x0000000000000000 in ?? ()

Thread 1 (Thread 0x7f294d0e8740 (LWP 3806)):
#0  0x00007f294c63d85c in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
#1  0x00000000005aa3e8 in _wapi_handle_timedwait_signal_handle (handle=0x400, timeout=0x0, 
    alertable=1, poll=-1) at handles.c:1638
#2  0x00000000005afee9 in WaitForMultipleObjectsEx (numobjects=2, handles=0x7fffefbc8360, 
    waitall=<value optimized out>, timeout=<value optimized out>, alertable=<value optimized out>)
    at wait.c:722
#3  0x000000000059a60b in wait_for_tids_or_state_change () at threads.c:2802
#4  mono_thread_manage () at threads.c:3017
#5  0x0000000000469941 in mono_main (argc=<value optimized out>, argv=<value optimized out>)
    at driver.c:1837
#6  0x00007f294c2cdc4d in __libc_start_main () from /lib/libc.so.6
#7  0x00000000004146a9 in _start () at ../sysdeps/x86_64/elf/start.S:113
Thread started: 

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

```

...obviously that's a horrible, horrible hack so maybe should be taken with a pinch of salt but perhaps something in libc6 is at fault?

---

### Post by terranim on 2010-10-26
Following on from that, I considered the differences in the hardware alongside changes to libc6 between karmic and lucid.

The major difference with the newer processor is the addition of the SSE4 instruction set. Taking a look at libc6, there were some additions in the lucid version that included some functions optimised for SSE4.

As an experiment, I took my lucid VM, downloaded the libc6 source package and spent a while trying to get it to build, but included a hack to the configuration that disabled the SSE4 extension functions. I eventually got it to build and installed it to the system, then I ran Monodevelop and suddenly I was able to debug again!

Conclusion:
Either there is a bug in one of the SSE4 extensions in libc6, that is still present today, or mono is making a call into libc6 incorrectly but happens to only segfault when the SSE4 version of the function is used.

Further investigation is required!

---

### Post by terranim on 2010-10-27
With a debug version of mono built and some crazy attaching of gdb to the running process that Monodevelop is trying to debug, I managed to find the thread responsible and get a more helpful stacktrace:

```
Thread 26 (Thread 0x7ff5ba99e710 (LWP 31880)):
#0  0x00007ff5c1284b8d in read () at ../sysdeps/unix/syscall-template.S:82
#1  0x00000000004d9956 in mono_handle_native_sigsegv (signal=11, ctx=0x7ff5ba799c40) at mini-exceptions.c:1935
#2  0x0000000000567a1d in mono_arch_handle_altstack_exception (sigctx=0x7ff5ba799c40, fault_addr=0x0, stack_ovf=0) at exceptions-amd64.c:926
#3  0x000000000041ffd6 in mono_sigsegv_signal_handler (_dummy=11, info=0x7ff5ba799d70, context=0x7ff5ba799c40) at mini.c:5500
#4  <signal handler called>
#5  0x00007ff5c101be6b in __strstr_sse42 (s1=0x6d9be8 "mono_thread_force_interruption_checkpoint", s2=0x6d8cd4 "ves_array_new_va_") at ../sysdeps/x86_64/multiarch/strstr.c:286
#6  0x00000000004193dc in mono_postprocess_patches (cfg=0x7ff5ac3063a0) at mini.c:3160
#7  0x000000000041a2df in mono_codegen (cfg=0x7ff5ac3063a0) at mini.c:3436
#8  0x000000000041d483 in mini_method_compile (method="<Module>:runtime_invoke_int__this__ ()", opts=51472767, domain=0x7ff5bd41e7f8, run_cctors=1, compile_aot=0, parts=0) at mini.c:4559
#9  0x000000000041e113 in mono_jit_compile_method_inner (method="<Module>:runtime_invoke_int__this__ ()", target_domain=0x7ff5bd41e7f8, opt=51472767, jit_ex=0x7ff5ba99bcf0) at mini.c:4823
#10 0x000000000041eb71 in mono_jit_compile_method_with_opt (method="<Module>:runtime_invoke_int__this__ ()", opt=51472767, ex=0x7ff5ba99bcf0) at mini.c:5031
#11 0x000000000041ecc8 in mono_jit_compile_method (method="<Module>:runtime_invoke_int__this__ ()") at mini.c:5056
#12 0x000000000041f75e in mono_jit_runtime_invoke (method="System.Collections.Generic.Dictionary`2:get_Count ()", obj=0x7ff5bb47d478, params=0x7ff5ba99bf30, exc=0x7ff5ba99c068) at mini.c:5317
#13 0x00000000005c9c4f in mono_runtime_invoke (method="System.Collections.Generic.Dictionary`2:get_Count ()", obj=0x7ff5bb47d478, params=0x7ff5ba99bf30, exc=0x7ff5ba99c068) at object.c:2709
#14 0x000000000050a48b in do_invoke_method (tls=0x13badf0, buf=0x7ff5ba99c158, invoke=0x183ad00) at debugger-agent.c:4806
#15 0x000000000050a7b5 in invoke_method () at debugger-agent.c:4884
#16 0x0000000000504b0d in suspend_current () at debugger-agent.c:2276
#17 0x0000000000505e1d in process_event (event=EVENT_KIND_BREAKPOINT, arg=0x7ff5ac039d68, il_offset=0, ctx=0x7ff5ba99c348, events=0x0, suspend_policy=2) at debugger-agent.c:2805
#18 0x0000000000507ade in process_breakpoint_inner (tls=0x13badf0, ctx=0x7ff5ba99c348) at debugger-agent.c:3618
#19 0x0000000000507b90 in process_breakpoint () at debugger-agent.c:3636
#20 0x00007ff5bb4463a8 in ?? ()
#21 0x000000004095b000 in ?? ()
#22 0x00007ff5ba99c430 in ?? ()
#23 0x00007ff5b300c167 in ?? ()
#24 0x00007ff5b3025fe0 in ?? ()
#25 0x00007ff5bb4463a8 in ?? ()
#26 0x00007ff5bb4c5c78 in ?? ()
#27 0x000000004095b000 in ?? ()
#28 0x00007ff5bb4463a8 in ?? ()
#29 0x00007ff5bb4463a8 in ?? ()
#30 0x00007ff5bb4463a8 in ?? ()
#31 0x00007ff5ac039b08 in ?? ()
#32 0x0000000000000000 in ?? ()
```

I also wrote a little test application that forces the strstr function to crash so that we can determine (via gdb and the libc6 debugging symbols) which implementation of strstr is being used:

Ubuntu x64 on i7 processor: __strstr_sse42 is called.
openSUSE x64 on i7 processor: strstr is called.

This suggests that in the latest openSUSE, libc6 is built without the additional SSE4 optimised functions, hence why Throctukes was able to debug successfully in a SUSE VM running on an i7 core.

It is highly unlikely that the __strstr_sse42 implementation in libc6 is buggy since that would render the entire Ubuntu system completely unstable on an i7-based machine, but that is not the case. It only appears to show up as a problem with the mono debugger and so is more likely to be something to do with how the function is used in mono.

---

### Post by terranim on 2010-10-27
With an extremely horrible hack to the mono-2.8/mono/mini/mini.c file around line 3158 I've forced it to not bother using the strstr function if the info->name is either "mono_thread_force_interruption_checkpoint" or "mono_object_new_specific". 

Hack in place, the debugger in MonoDevelop now appears to be working. There is nothing wrong with the strings themselves, since I tried invoking strstr with those strings in my native test app. Perhaps there is something wrong with the info->name member at this point in the threaded code which causes the SSE4 implementation of strstr to crash?

At this point I don't think I can go any further, I wouldn't really know where to start debugging the mini.c implementation.

---

### Post by Throctukes on 2010-10-27
Digging further, the problem seems to come from line 286 in x86_64/multiarch/strstr.c

```

280  /* p1 > 1 byte long.  Load up to 16 bytes of fragment.  */
281  __m128i frag1 = strloadu (p1);
282
283  __m128i frag2;
284  if (p2[1] != '\0')
285    /* p2 is > 1 byte long.  */
286    frag2 = strloadu (p2); 
287  else
288    frag2 = _mm_insert_epi8 (_mm_setzero_si128 (), LOADBYTE (p2[0]), 0);

```

- oddly, p2 is the constant argument called from mini.c by mono. I'd have thought that if p2 were invalid, the stacktrace would've directed us inside strloadu, though perhaps it's the conditional check on 284 that's failing.

*how* a constant string has become invalid is a good question.

Interestingly, I've found another report of this problem from a totally different source - [http://developer.nvidia.com/forums/index.php?showtopic=4926](http://developer.nvidia.com/forums/index.php?showtopic=4926) which suggests that there really is a problem in this implementation. If that were the case, though, given how much strstr is used how come we're not seeing massive system-wide instability?

---

### Post by directhex on 2010-10-27
I think there's something else at play, something about your system which differs from mine (i7, x64 Maverick). Sticking a breakpoint on something in HomeController.cs, it just works as it should with the soft debugger.

---

### Post by terranim on 2010-10-28
By following the same process of debugging/disassembly as found at [http://sourceware.org/bugzilla/show_bug.cgi?id=12123]("http://sourceware.org/bugzilla/show_bug.cgi?id=12123") we can see that the byte alignment looks incorrect on what is probably the p2 parameter in the __strstr_sse42 function.

I do not know if this is a bug in the strstr implementation itself, or is due to a misalignment in the calling library (mono/mini), or maybe even a bug in gcc!

Results:
```
Program received signal SIGSEGV, Segmentation fault.
0x00007f85b165ee6b in __strstr_sse42 (s1=0x6d5280 "mono_create_corlib_exception_1", s2=0x6d3f05 "ves_array_new_va_") at ../sysdeps/x86_64/multiarch/strstr.c:286
286     ../sysdeps/x86_64/multiarch/strstr.c: No such file or directory.
        in ../sysdeps/x86_64/multiarch/strstr.c
(gdb) bt
#0  0x00007f85b165ee6b in __strstr_sse42 (s1=0x6d5280 "mono_create_corlib_exception_1", s2=0x6d3f05 "ves_array_new_va_") at ../sysdeps/x86_64/multiarch/strstr.c:286
#1  0x0000000000417e34 in mono_postprocess_patches (cfg=0x291c550) at mini.c:3177
#2  mono_codegen (cfg=0x291c550) at mini.c:3453
#3  0x000000000041afdd in mini_method_compile (method=<value optimised out>, opts=<value optimised out>, domain=<value optimised out>, run_cctors=<value optimised out>, 
    compile_aot=<value optimised out>, parts=<value optimised out>) at mini.c:4576
#4  0x000000000041c4af in mono_jit_compile_method_inner (method="System.Type:GetType ()", opt=51472767, ex=0x7fff82976d50) at mini.c:4840
#5  mono_jit_compile_method_with_opt (method="System.Type:GetType ()", opt=51472767, ex=0x7fff82976d50) at mini.c:5048
#6  0x000000000041d0a9 in mono_jit_runtime_invoke (method="System.Type:GetType ()", obj=0x0, params=<value optimised out>, exc=0x7fff82977058) at mini.c:5246
#7  0x00000000005c5217 in mono_runtime_invoke (method="System.Type:GetType ()", obj=0x0, params=0x7fff82976f00, exc=0x7fff82977058) at object.c:2709
#8  0x0000000000505a53 in do_invoke_method (tls=0x28f3290, buf=0x7fff82977148, invoke=0x291c240) at debugger-agent.c:4806
#9  0x0000000000505d7d in invoke_method () at debugger-agent.c:4884
#10 0x00000000005000d5 in suspend_current () at debugger-agent.c:2276
#11 0x00000000005013e5 in process_event (event=EVENT_KIND_BREAKPOINT, arg=0x2887a10, il_offset=0, ctx=0x7fff82977338, events=0x0, suspend_policy=2)
    at debugger-agent.c:2805
#12 0x00000000005030a6 in process_breakpoint_inner (tls=0x28f3290, ctx=0x7fff82977338) at debugger-agent.c:3618
#13 0x0000000000503158 in process_breakpoint () at debugger-agent.c:3636
#14 0x00007f85b222ffa0 in ?? ()
#15 0x0000000040692000 in ?? ()
#16 0x00007fff82977430 in ?? ()
#17 0x0000000040e2b099 in ?? ()
#18 0x0000000002887a10 in ?? ()
#19 0x0000000040e2aea0 in ?? ()
#20 0x0000000000000000 in ?? ()
(gdb) disassemble

...

   0x00007f85b165edf8 <+776>:   test   %eax,%eax
   0x00007f85b165edfa <+778>:   jne    0x7f85b165eb62 <__strstr_sse42+114>
   0x00007f85b165ee00 <+784>:   add    $0x10,%rbx
   0x00007f85b165ee04 <+788>:   mov    %rbx,%rdi
   0x00007f85b165ee07 <+791>:   callq  0x7f85b165e9b0 <__m128i_strloadu>
   0x00007f85b165ee0c <+796>:   movdqa 0x10(%rsp),%xmm1
   0x00007f85b165ee12 <+802>:   xor    %edx,%edx
   0x00007f85b165ee14 <+804>:   xor    %eax,%eax
   0x00007f85b165ee16 <+806>:   pcmpistri $0xc,%xmm0,%xmm1
   0x00007f85b165ee1c <+812>:   mov    %ecx,%ebp
   0x00007f85b165ee1e <+814>:   setb   %dl
   0x00007f85b165ee21 <+817>:   sete   %al
   0x00007f85b165ee24 <+820>:   jmpq   0x7f85b165ec30 <__strstr_sse42+320>
   0x00007f85b165ee29 <+825>:   test   %eax,%eax
   0x00007f85b165ee2b <+827>:   je     0x7f85b165eb62 <__strstr_sse42+114>
   0x00007f85b165ee31 <+833>:   pxor   %xmm1,%xmm1
   0x00007f85b165ee35 <+837>:   pxor   %xmm0,%xmm0
   0x00007f85b165ee39 <+841>:   pcmpeqb 0x10(%rsp),%xmm1
   0x00007f85b165ee3f <+847>:   pcmpeqb %xmm3,%xmm0
   0x00007f85b165ee43 <+851>:   pmovmskb %xmm1,%edx
   0x00007f85b165ee47 <+855>:   pmovmskb %xmm0,%eax
   0x00007f85b165ee4b <+859>:   bsf    %edx,%edx
   0x00007f85b165ee4e <+862>:   bsf    %eax,%eax
   0x00007f85b165ee51 <+865>:   cmp    %eax,%edx
   0x00007f85b165ee53 <+867>:   jl     0x7f85b165ecf1 <__strstr_sse42+513>
   0x00007f85b165ee59 <+873>:   xor    %eax,%eax
   0x00007f85b165ee5b <+875>:   jmpq   0x7f85b165eb22 <__strstr_sse42+50>
   0x00007f85b165ee60 <+880>:   mov    %rbx,%rax
   0x00007f85b165ee63 <+883>:   jmpq   0x7f85b165eb22 <__strstr_sse42+50>
   0x00007f85b165ee68 <+888>:   mov    %r13,%rdi
=> 0x00007f85b165ee6b <+891>:   movdqa %xmm0,(%rsp)
   0x00007f85b165ee70 <+896>:   callq  0x7f85b165e9b0 <__m128i_strloadu>
   0x00007f85b165ee75 <+901>:   movdqa %xmm0,0x10(%rsp)
   0x00007f85b165ee7b <+907>:   movdqa (%rsp),%xmm1
   0x00007f85b165ee80 <+912>:   jmpq   0x7f85b165eb98 <__strstr_sse42+168>
   0x00007f85b165ee85 <+917>:   movslq %ecx,%rax
   0x00007f85b165ee88 <+920>:   lea    (%rbx,%rax,1),%rax
   0x00007f85b165ee8c <+924>:   jmpq   0x7f85b165eb22 <__strstr_sse42+50>
   0x00007f85b165ee91 <+929>:   test   %edx,%edx
   0x00007f85b165ee93 <+931>:   je     0x7f85b165eb62 <__strstr_sse42+114>
   0x00007f85b165ee99 <+937>:   movslq %ebp,%rax
   0x00007f85b165ee9c <+940>:   jmpq   0x7f85b165edd5 <__strstr_sse42+741>

...

(gdb) p $rsp
$1 = (void *) 0x7fff829769e8
```

---

### Post by Throctukes on 2010-11-25
This is a bug in mono. The patch on this bug report fixes it: [https://bugzilla.novell.com/show_bug.cgi?id=647464#c7](https://bugzilla.novell.com/show_bug.cgi?id=647464#c7)

---

### Post by directhex on 2010-11-25
> **Throctukes said:**
> This is a bug in mono. The patch on this bug report fixes it: [https://bugzilla.novell.com/show_bug.cgi?id=647464#c7](https://bugzilla.novell.com/show_bug.cgi?id=647464#c7)

Committed to a patch branch on git.debian.org, this should be in mono 2.6.7-4

---

