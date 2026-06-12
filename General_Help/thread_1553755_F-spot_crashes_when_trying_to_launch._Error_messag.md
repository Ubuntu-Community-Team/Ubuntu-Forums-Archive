---
title: "F-spot crashes when trying to launch. Error message displays"
date: 2010-08-15
forum: General Help
---

### Post by finny388 on 2010-08-15
I don't use F-spot regularly. I don't think I've used it for a few months. But when I tried to open it recently and every time since it crashes showing the following error:

> [B]F-Spot Encountered a Fatal Error
[/B]
Could not read add-in description

**-Error Details**

An unhandled exception was thrown: Could not read add-in description

  at Mono.Addins.Addin.get_Description () [0x00000] 
  at Mono.Addins.AddinSessionService.CheckHostAssembly (System.Reflection.Assembly asm) [0x00000] 
  at Mono.Addins.AddinSessionService.ActivateRoots () [0x00000] 
  at Mono.Addins.AddinSessionService.Initialize () [0x00000] 
  at Mono.Addins.AddinManager.Initialize (System.String configDir) [0x00000] 
  at FSpot.Driver.Main (System.String[] args) [0x00000] 
.NET Version: 2.0.50727.1433

Assembly Version Information:

System.Core (3.5.0.0)
System.Xml (2.0.0.0)
NDesk.DBus.Proxies (0.0.0.0)
gconf-sharp (2.24.0.0)
System.Data (2.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
FSpot.Query (0.0.0.0)
FSpot.JobScheduler (0.0.0.0)
gdk-sharp (2.12.0.0)
NDesk.DBus.GLib (1.0.0.0)
NDesk.DBus (1.0.0.0)
gnome-vfs-sharp (2.24.0.0)
Cms (0.0.0.0)
FSpot.Core (0.0.0.0)
FSpot.Platform (0.0.0.0)
Mono.Posix (2.0.0.0)
FSpot.Utils (0.0.0.0)
atk-sharp (2.12.0.0)
gtk-sharp (2.12.0.0)
Mono.Addins (0.4.0.0)
System (2.0.0.0)
Mono.Addins.Setup (0.4.0.0)
glib-sharp (2.12.0.0)
f-spot (0.6.1.5)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.32-24-generic-pae i686 unknown GNU/Linux

Distribution Information:

[/etc/debian_version]
squeeze/sid

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

I removed F-Spot and reinstalled in Synaptic but it didn't fix anything.

Any ideas?

thanks

---

### Post by mike555 on 2010-08-15
dang mono, you might want to try " Shotwell" I like it better (and no mono)

---

### Post by finny388 on 2010-08-15
hmm, no idea what mono is.

I found Phatch and used it to resize multiple photos at once.

What a great tool for applying a number of edits to a group of images in one go.

I don't know if F-spot (or shotwell) do that but that was my goal.

F-spot should be stable if Canonical installs it by default.

Thanks for the suggestion though Mike555.

---

### Post by finny388 on 2010-08-18
can anyone shed some light?

I'm hoping to buy a dig camera and get back into photos again.

---

### Post by fishtoprecords on 2010-08-19
I can get it to launch, but it blows up when I try to open a file to look at.


f-spot --version
F-Spot  0.6.1.5 - (c)2003-2009, Novell Inc
Personal photo management for the GNOME Desktop

Error message:


```
f-spot:2527): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
Stacktrace:

  at (wrapper managed-to-native) GdkGlx.Context.glXChooseVisual (intptr,int,int[]) <0x00004>
  at (wrapper managed-to-native) GdkGlx.Context.glXChooseVisual (intptr,int,int[]) <0xffffffff>
  at GdkGlx.Context..ctor (Gdk.Screen,GdkGlx.Context,int[]) <0x000b1>
  at GdkGlx.Context..ctor (Gdk.Screen,int[]) <0x00015>
  at FSpot.Widgets.PhotoImageView.OnRealized () <0x0007c>
  at Gtk.Widget.realized_cb (intptr) <0x0004b>
  at (wrapper native-to-managed) Gtk.Widget.realized_cb (intptr) <0xffffffff>
  at (wrapper managed-to-native) Gtk.Widget.gtk_widget_show (intptr) <0x00004>
  at (wrapper managed-to-native) Gtk.Widget.gtk_widget_show (intptr) <0xffffffff>
  at Gtk.Widget.Show () <0x00016>
  at ImportCommand.ImportFromFile (PhotoStore,string) <0x005d1>
  at MainWindow.HandleImportCommand (object,System.EventArgs) <0x00060>
  at (wrapper runtime-invoke) MainWindow.runtime_invoke_void__this___object_object (object,intptr,intptr,intptr) <0xffffffff>
  at (wrapper managed-to-native) System.Reflection.MonoMethod.InternalInvoke (object,object[],System.Exception&) <0x00004>
  at (wrapper managed-to-native) System.Reflection.MonoMethod.InternalInvoke (object,object[],System.Exception&) <0xffffffff>
  at System.Reflection.MonoMethod.Invoke (object,System.Reflection.BindingFlags,System.Reflection.Binder,object[],System.Globalization.CultureInfo) <0x000a4>
  at System.Reflection.MethodBase.Invoke (object,object[]) <0x00025>
  at System.Delegate.DynamicInvokeImpl (object[]) <0x0018a>
  at System.MulticastDelegate.DynamicInvokeImpl (object[]) <0x00034>
  at System.Delegate.DynamicInvoke (object[]) <0x00019>
  at GLib.Signal.ClosureInvokedCB (object,GLib.ClosureInvokedArgs) <0x00120>
  at GLib.SignalClosure.Invoke (GLib.ClosureInvokedArgs) <0x00023>
  at GLib.SignalClosure.MarshalCallback (intptr,intptr,uint,intptr,intptr,intptr) <0x00216>
  at (wrapper native-to-managed) GLib.SignalClosure.MarshalCallback (intptr,intptr,uint,intptr,intptr,intptr) <0xffffffff>
  at (wrapper managed-to-native) Gtk.Application.gtk_main () <0x00004>
  at (wrapper managed-to-native) Gtk.Application.gtk_main () <0xffffffff>
  at Gtk.Application.Run () <0x0000a>
  at FSpot.Driver.Main (string[]) <0x01b58>
  at (wrapper runtime-invoke) FSpot.Driver.runtime_invoke_int_object (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

	f-spot() [0x80ca6e4]
	f-spot() [0x80f6893]
	[0xd74410]
	[0x8956ad0]

Debug info from gdb:

[Thread debugging using libthread_db enabled]
[New Thread 0x2a7eb70 (LWP 2541)]
[New Thread 0x2638b70 (LWP 2534)]
[New Thread 0x2153b70 (LWP 2533)]
[New Thread 0x1708b70 (LWP 2531)]
[New Thread 0xd24b70 (LWP 2529)]
[New Thread 0x2b3b70 (LWP 2528)]
0x00d74422 in __kernel_vsyscall ()
  7 Thread 0x2b3b70 (LWP 2528)  0x00d74422 in __kernel_vsyscall ()
  6 Thread 0xd24b70 (LWP 2529)  0x00d74422 in __kernel_vsyscall ()
  5 Thread 0x1708b70 (LWP 2531)  0x00d74422 in __kernel_vsyscall ()
  4 Thread 0x2153b70 (LWP 2533)  0x00d74422 in __kernel_vsyscall ()
  3 Thread 0x2638b70 (LWP 2534)  0x00d74422 in __kernel_vsyscall ()
  2 Thread 0x2a7eb70 (LWP 2541)  0x00d74422 in __kernel_vsyscall ()
* 1 Thread 0xdd16f0 (LWP 2527)  0x00d74422 in __kernel_vsyscall ()

Thread 7 (Thread 0x2b3b70 (LWP 2528)):
#0  0x00d74422 in __kernel_vsyscall ()
#1  0x00aed736 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081a6af8 in ?? ()
#3  0x00ae596e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0x00203a4e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 6 (Thread 0xd24b70 (LWP 2529)):
#0  0x00d74422 in __kernel_vsyscall ()
#1  0x00aec245 in sem_wait@@GLIBC_2.1 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0812e199 in ?? ()
#3  0x081527ea in ?? ()
#4  0x081c3062 in ?? ()
#5  0x081e1925 in ?? ()
#6  0x00ae596e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#7  0x00203a4e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 5 (Thread 0x1708b70 (LWP 2531)):
#0  0x00d74422 in __kernel_vsyscall ()
#1  0x00aea015 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081ac841 in ?? ()
#3  0x081ac8b4 in ?? ()
#4  0x081c742f in ?? ()
#5  0x0814f763 in ?? ()
#6  0x00f9c8cd in ?? ()
#7  0x00f9c504 in ?? ()
#8  0x00f9c409 in ?? ()
#9  0x0039c739 in ?? ()
#10 0x08110ef4 in mono_runtime_delegate_invoke ()
#11 0x0815285b in ?? ()
#12 0x081c3062 in ?? ()
#13 0x081e1925 in ?? ()
#14 0x00ae596e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#15 0x00203a4e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 4 (Thread 0x2153b70 (LWP 2533)):
#0  0x00d74422 in __kernel_vsyscall ()
#1  0x00aea015 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081ac841 in ?? ()
#3  0x081ac8b4 in ?? ()
#4  0x081c742f in ?? ()
#5  0x0814dfc9 in ?? ()
#6  0x03740fa0 in ?? ()
#7  0x03740e13 in ?? ()
#8  0x03740c34 in ?? ()
#9  0x0039c739 in ?? ()
#10 0x08110ef4 in mono_runtime_delegate_invoke ()
#11 0x0815285b in ?? ()
#12 0x081c3062 in ?? ()
#13 0x081e1925 in ?? ()
#14 0x00ae596e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#15 0x00203a4e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 3 (Thread 0x2638b70 (LWP 2534)):
#0  0x00d74422 in __kernel_vsyscall ()
#1  0x00aea015 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081ac841 in ?? ()
#3  0x081ac8b4 in ?? ()
#4  0x081c742f in ?? ()
#5  0x0814dfc9 in ?? ()
#6  0x03740fa0 in ?? ()
#7  0x03740e13 in ?? ()
#8  0x03741892 in ?? ()
#9  0x0039c739 in ?? ()
#10 0x08110ef4 in mono_runtime_delegate_invoke ()
#11 0x0815285b in ?? ()
#12 0x081c3062 in ?? ()
#13 0x081e1925 in ?? ()
#14 0x00ae596e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#15 0x00203a4e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0x2a7eb70 (LWP 2541)):
#0  0x00d74422 in __kernel_vsyscall ()
#1  0x00aea015 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081ac841 in ?? ()
#3  0x081ac8b4 in ?? ()
#4  0x081c742f in ?? ()
#5  0x0814dfc9 in ?? ()
#6  0x03740fa0 in ?? ()
#7  0x03740e13 in ?? ()
#8  0x03741892 in ?? ()
#9  0x0039c739 in ?? ()
#10 0x08110ef4 in mono_runtime_delegate_invoke ()
#11 0x0815285b in ?? ()
#12 0x081c3062 in ?? ()
#13 0x081e1925 in ?? ()
#14 0x00ae596e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#15 0x00203a4e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xdd16f0 (LWP 2527)):
#0  0x00d74422 in __kernel_vsyscall ()
#1  0x00aecf5b in read () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x080ca87e in ?? ()
#3  0x080f6893 in ?? ()
#4  <signal handler called>
#5  0x02ccbef6 in XF86DRIQueryExtension () from /usr/lib/fglrx/libGL.so.1
#6  0x0000000d in ?? ()
#7  0x00000078 in ?? ()
#8  0xbfa13f18 in ?? ()
Backtrace stopped: previous frame inner to this frame (corrupt stack?)

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted

```

---

### Post by mike555 on 2010-08-19
Mono is Microsofts .NET   in a so-called open source form    ,   [http://www.mono-project.com/ASP.NET](http://www.mono-project.com/ASP.NET)

---

