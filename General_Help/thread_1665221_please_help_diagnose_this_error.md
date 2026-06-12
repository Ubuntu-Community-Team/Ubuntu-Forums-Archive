---
title: "please help diagnose this error"
date: 2011-01-12
forum: General Help
---

### Post by koven on 2011-01-12
cant get HFM.exe to run.... can someone plz diagnose this error msg and tell me what ican do to fix it?

> koven@ubuntu:~/Desktop/HFM$ mono HFM.exe

```
** (HFM.exe:11003): WARNING **: The following assembly referenced from /home/koven/Desktop/HFM/protobuf-net.dll could not be loaded:
     Assembly:   System.Runtime.Serialization    (assemblyref_index=2)
     Version:    3.0.0.0
     Public Key: b77a5c561934e089
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/koven/Desktop/HFM/).


** (HFM.exe:11003): WARNING **: Could not load file or assembly 'System.Runtime.Serialization, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.

** (HFM.exe:11003): WARNING **: Could not load file or assembly 'System.Runtime.Serialization, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.
Stacktrace:

  at ProtoBuf.Serializer.TryGetTag (System.Reflection.MemberInfo,int&,string&,ProtoBuf.DataFormat&,ProtoBuf.MemberSerializationOptions&) <0xffffffff>
  at ProtoBuf.Serializer.TryGetTag (System.Reflection.MemberInfo,int&,string&,ProtoBuf.DataFormat&,ProtoBuf.MemberSerializationOptions&) <0x00030>
  at ProtoBuf.Serializer`1<object>.Build () <0x00373>
  at ProtoBuf.Serializer`1<object>.SerializeChecked (object,ProtoBuf.SerializationContext) <0x0004f>
  at ProtoBuf.SerializerItemProxy`2<HFM.Framework.XmlStatsData, HFM.Framework.XmlStatsData>.Serialize (HFM.Framework.XmlStatsData,ProtoBuf.SerializationContext) <0x0004b>
  at ProtoBuf.SerializerProxy`1<object>.Serialize (object,System.IO.Stream) <0x00057>
  at ProtoBuf.Serializer.Serialize<object> (System.IO.Stream,object) <0x0006b>
  at HFM.Framework.XmlStatsDataContainer.Serialize (HFM.Framework.XmlStatsData,string) <0x000b3>
  at HFM.Framework.XmlStatsDataContainer.Write () <0x00057>
  at HFM.Framework.XmlStatsDataContainer.GetEocXmlData (bool) <0x001b7>
  at HFM.Forms.frmMain.RefreshUserStatsData (bool) <0x0002a>
  at HFM.Forms.frmMain.UserStatsEnabledChanged () <0x00053>
  at HFM.Forms.frmMain.Initialize () <0x00037>
  at (wrapper remoting-invoke-with-check) HFM.Forms.frmMain.Initialize () <0xffffffff>
  at HFM.Program.Main (string[]) <0x00527>
  at (wrapper runtime-invoke) HFM.Program.runtime_invoke_void_object (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

    mono() [0x47b77f]
    mono() [0x4aef3f]
    /lib/libpthread.so.0(+0xf8f0) [0x7f488a3258f0]
    mono(mono_object_new_specific+0x16) [0x4caa86]
    mono(mono_exception_from_name_domain+0x1d) [0x50e1ed]
    mono(mono_exception_from_name_msg+0xe) [0x50e4de]
    mono() [0x41eb36]
    mono() [0x483521]
    [0x41fc4168]

Debug info from gdb:

[Thread debugging using libthread_db enabled]
[New Thread 0x7f487853a700 (LWP 11014)]
[New Thread 0x7f4878d96700 (LWP 11011)]
[New Thread 0x7f4878f97700 (LWP 11010)]
[New Thread 0x7f48795a1700 (LWP 11009)]
[New Thread 0x7f48797a2700 (LWP 11008)]
[New Thread 0x7f4888b76700 (LWP 11005)]
[New Thread 0x7f488b02d700 (LWP 11004)]
0x00007f488a32493d in read () from /lib/libpthread.so.0
  8 Thread 0x7f488b02d700 (LWP 11004)  0x00007f488a32511d in nanosleep ()
   from /lib/libpthread.so.0
  7 Thread 0x7f4888b76700 (LWP 11005)  0x00007f488a323b50 in sem_wait ()
   from /lib/libpthread.so.0
  6 Thread 0x7f48797a2700 (LWP 11008)  0x00007f488a32511d in nanosleep ()
   from /lib/libpthread.so.0
  5 Thread 0x7f48795a1700 (LWP 11009)  0x00007f488a321bc9 in pthread_cond_timedwait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
  4 Thread 0x7f4878f97700 (LWP 11010)  0x00007f4889df6d03 in epoll_wait ()
   from /lib/libc.so.6
  3 Thread 0x7f4878d96700 (LWP 11011)  0x00007f488a321bc9 in pthread_cond_timedwait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
  2 Thread 0x7f487853a700 (LWP 11014)  0x00007f488a321bc9 in pthread_cond_timedwait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
* 1 Thread 0x7f488b022740 (LWP 11003)  0x00007f488a32493d in read ()
   from /lib/libpthread.so.0

Thread 8 (Thread 0x7f488b02d700 (LWP 11004)):
#0  0x00007f488a32511d in nanosleep () from /lib/libpthread.so.0
#1  0x0000000000556342 in ?? ()
#2  0x00007f488a31c9ca in start_thread () from /lib/libpthread.so.0
#3  0x00007f4889df670d in clone () from /lib/libc.so.6
#4  0x0000000000000000 in ?? ()

Thread 7 (Thread 0x7f4888b76700 (LWP 11005)):
#0  0x00007f488a323b50 in sem_wait () from /lib/libpthread.so.0
#1  0x00000000004e4aaa in ?? ()
#2  0x0000000000505035 in ?? ()
#3  0x0000000000570073 in ?? ()
#4  0x000000000058de21 in ?? ()
#5  0x00007f488a31c9ca in start_thread () from /lib/libpthread.so.0
#6  0x00007f4889df670d in clone () from /lib/libc.so.6
#7  0x0000000000000000 in ?? ()

Thread 6 (Thread 0x7f48797a2700 (LWP 11008)):
#0  0x00007f488a32511d in nanosleep () from /lib/libpthread.so.0
#1  0x000000000056f134 in ?? ()
#2  0x0000000000507d21 in ?? ()
#3  0x0000000000505035 in ?? ()
#4  0x0000000000570073 in ?? ()
#5  0x000000000058de21 in ?? ()
#6  0x00007f488a31c9ca in start_thread () from /lib/libpthread.so.0
#7  0x00007f4889df670d in clone () from /lib/libc.so.6
#8  0x0000000000000000 in ?? ()

Thread 5 (Thread 0x7f48795a1700 (LWP 11009)):
#0  0x00007f488a321bc9 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
#1  0x000000000055b45d in ?? ()
#2  0x00000000005736d6 in ?? ()
#3  0x00000000005078b4 in ?? ()
#4  0x0000000000505035 in ?? ()
#5  0x0000000000570073 in ?? ()
#6  0x000000000058de21 in ?? ()
#7  0x00007f488a31c9ca in start_thread () from /lib/libpthread.so.0
#8  0x00007f4889df670d in clone () from /lib/libc.so.6
#9  0x0000000000000000 in ?? ()

Thread 4 (Thread 0x7f4878f97700 (LWP 11010)):
#0  0x00007f4889df6d03 in epoll_wait () from /lib/libc.so.6
#1  0x00000000005084f7 in ?? ()
#2  0x0000000000505035 in ?? ()
#3  0x0000000000570073 in ?? ()
#4  0x000000000058de21 in ?? ()
#5  0x00007f488a31c9ca in start_thread () from /lib/libpthread.so.0
#6  0x00007f4889df670d in clone () from /lib/libc.so.6
#7  0x0000000000000000 in ?? ()

Thread 3 (Thread 0x7f4878d96700 (LWP 11011)):
#0  0x00007f488a321bc9 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
#1  0x000000000055b45d in ?? ()
#2  0x00000000005736d6 in ?? ()
#3  0x0000000000508903 in ?? ()
#4  0x0000000000505035 in ?? ()
#5  0x0000000000570073 in ?? ()
#6  0x000000000058de21 in ?? ()
#7  0x00007f488a31c9ca in start_thread () from /lib/libpthread.so.0
#8  0x00007f4889df670d in clone () from /lib/libc.so.6
#9  0x0000000000000000 in ?? ()

Thread 2 (Thread 0x7f487853a700 (LWP 11014)):
#0  0x00007f488a321bc9 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
#1  0x000000000055b45d in ?? ()
#2  0x00000000005736d6 in ?? ()
#3  0x00000000005078b4 in ?? ()
#4  0x0000000000505035 in ?? ()
#5  0x0000000000570073 in ?? ()
#6  0x000000000058de21 in ?? ()
#7  0x00007f488a31c9ca in start_thread () from /lib/libpthread.so.0
#8  0x00007f4889df670d in clone () from /lib/libc.so.6
#9  0x0000000000000000 in ?? ()

Thread 1 (Thread 0x7f488b022740 (LWP 11003)):
#0  0x00007f488a32493d in read () from /lib/libpthread.so.0
#1  0x000000000047b8f4 in ?? ()
#2  0x00000000004aef3f in ?? ()
#3  <signal handler called>
#4  0x00000000004caa86 in mono_object_new_specific ()
#5  0x000000000050e1ed in mono_exception_from_name_domain ()
#6  0x000000000050e4de in mono_exception_from_name_msg ()
#7  0x000000000041eb36 in ?? ()
#8  0x0000000000483521 in ?? ()
#9  0x0000000041fc4168 in ?? ()
#10 0x0000000000000000 in ?? ()

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted

```

i'm running 10.4..

---

### Post by koven on 2011-01-12
i realize it's a very specific issue but how do i get started on fixing it?

---

### Post by Sef on 2011-01-12
> mono HFM.exe

.exe files do not work on Linux. If you want to try to get it to work, you would need to download WINE from the repositories. However, WINE does not work with .exe files all the time.

---

### Post by LightningCrash on 2011-06-04
Op you need you install the package `libmono-wcf3.0-cil`


> **Sef said:**
> .exe files do not work on Linux. If you want to try to get it to work, you would need to download WINE from the repositories. However, WINE does not work with .exe files all the time.

He doesn't, because he has the mono CLR package installed and this app is made to work with mono.
LOL!

---

