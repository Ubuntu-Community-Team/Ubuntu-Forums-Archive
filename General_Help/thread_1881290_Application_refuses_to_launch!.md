---
title: "Application refuses to launch!"
date: 2011-11-15
forum: General Help
---

### Post by oxf on 2011-11-15
OK I just installed GFax via the Software Center. However, I have  avague memory that this happened once before so I suspect it'd not specific to GFax and could apply to any application.

What happens is this. I click on GFax to open it and the little thingy whirls arround for about 10 seconds and it fails to launch and closes. Every time!

Any sugestions appreciated.

Katja

---

### Post by MG&amp;TL on 2011-11-15
Run:

```
gfax
```


in a terminal, and post the output.

---

### Post by oxf on 2011-11-15
> **MG&TL said:**
> Run:

```
gfax
```
in a terminal, and post the output.

Thanks.. Here's the output:

```
mbdb@M2000:~$ gfax

Unhandled Exception: System.UnauthorizedAccessException: Access to the path "/var/spool/gfax" is denied.
  at System.IO.Directory.CreateDirectoriesInternal (System.String path) [0x00000] in <filename unknown>:0 
  at System.IO.Directory.CreateDirectory (System.String path) [0x00000] in <filename unknown>:0 
  at System.IO.DirectoryInfo.Create () [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.IO.DirectoryInfo:Create ()
  at System.IO.Directory.CreateDirectoriesInternal (System.String path) [0x00000] in <filename unknown>:0 
  at System.IO.Directory.CreateDirectory (System.String path) [0x00000] in <filename unknown>:0 
  at gfax.gfax.Main (System.String[] args) [0x00000] in <filename unknown>:0 
```

---

### Post by MG&amp;TL on 2011-11-15
gfax-specific. It's getting 'permission denied'-run:

```
sudo gfax
```

and post output.

---

### Post by oxf on 2011-11-15
> **MG&TL said:**
> gfax-specific. It's getting 'permission denied'-run:

```
sudo gfax
```and post output.

I dont like the last part!

```
mbdb@M2000:~$ sudo gfax
[sudo] password for mbdb: 

(/usr/lib/gfax/gfax.exe:2038): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.26.1/gobject/gtype.c:2710: You forgot to call g_type_init()

(/usr/lib/gfax/gfax.exe:2038): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed

(/usr/lib/gfax/gfax.exe:2038): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed
Stacktrace:

  at (wrapper managed-to-native) GConf.Client.gconf_client_get_default () <0x00004>
  at (wrapper managed-to-native) GConf.Client.gconf_client_get_default () <0x00004>
  at GConf.Client..ctor () <0x00046>
  at gfax.Settings..cctor () <0x00021>
  at (wrapper runtime-invoke) object.runtime_invoke_void (object,intptr,intptr,intptr) <0x0003a>
  at gfax.gfax.Main (string[]) <0xffffffff>
  at gfax.gfax.Main (string[]) <0x004bb>
  at (wrapper runtime-invoke) <Module>.runtime_invoke_void_object (object,intptr,intptr,intptr) <0x00043>

Native stacktrace:

    mono() [0x80d4d0b]
    mono() [0x810ffeb]
    [0x37640c]
    /usr/lib/libgconf-2.so.4(gconf_client_get_default+0xf8) [0x8d68d8]
    [0x195826]
    [0x1956cf]
    [0x19566a]
    [0x18b25b]
    mono() [0x8061328]
    mono(mono_runtime_invoke+0x40) [0x813c890]
    mono() [0x81439c6]
    mono() [0x8097d7e]
    mono() [0x805efa8]
    mono() [0x80606bf]
    mono() [0x806123e]
    mono() [0x80d8b4e]
    [0x16c066]
    [0x18c4f4]
    mono() [0x8061328]
    mono(mono_runtime_invoke+0x40) [0x813c890]
    mono(mono_runtime_exec_main+0xde) [0x81403de]
    mono(mono_runtime_run_main+0x112) [0x81406e2]
    mono(mono_main+0x1679) [0x80b2f99]
    mono() [0x8059385]
    /lib/libc.so.6(__libc_start_main+0xe7) [0xddece7]
    mono() [0x80592c1]

Debug info from gdb:

[Thread debugging using libthread_db enabled]
[New Thread 0xa6ab70 (LWP 2040)]
[New Thread 0x1bfb70 (LWP 2039)]
0x00376416 in __kernel_vsyscall ()
  3 Thread 0x1bfb70 (LWP 2039)  0x00376416 in __kernel_vsyscall ()
  2 Thread 0xa6ab70 (LWP 2040)  0x00376416 in __kernel_vsyscall ()
* 1 Thread 0x16b6f0 (LWP 2038)  0x00376416 in __kernel_vsyscall ()

Thread 3 (Thread 0x1bfb70 (LWP 2039)):
#0  0x00376416 in __kernel_vsyscall ()
#1  0x007d7de6 in nanosleep () from /lib/libpthread.so.0
#2  0x081e5238 in ?? ()
#3  0x007cfcc9 in start_thread () from /lib/libpthread.so.0
#4  0x00e9869e in clone () from /lib/libc.so.6

Thread 2 (Thread 0xa6ab70 (LWP 2040)):
#0  0x00376416 in __kernel_vsyscall ()
#1  0x007d6895 in sem_wait@@GLIBC_2.1 () from /lib/libpthread.so.0
#2  0x08200ae8 in mono_sem_wait ()
#3  0x081163f8 in ?? ()
#4  0x081b11db in ?? ()
#5  0x081e8e4e in ?? ()
#6  0x08214f85 in ?? ()
#7  0x007cfcc9 in start_thread () from /lib/libpthread.so.0
#8  0x00e9869e in clone () from /lib/libc.so.6

Thread 1 (Thread 0x16b6f0 (LWP 2038)):
#0  0x00376416 in __kernel_vsyscall ()
#1  0x007d75cb in read () from /lib/libpthread.so.0
#2  0x080d4ede in ?? ()
#3  0x0810ffeb in ?? ()
#4  <signal handler called>
#5  0x008d3dd1 in ?? () from /usr/lib/libgconf-2.so.4
#6  0x008d68d8 in gconf_client_get_default () from /usr/lib/libgconf-2.so.4
#7  0x00195826 in ?? ()
#8  0x001956cf in ?? ()
#9  0x0019566a in ?? ()
#10 0x0018b25b in ?? ()
#11 0x08061328 in ?? ()
#12 0x0813c890 in mono_runtime_invoke ()
#13 0x081439c6 in ?? ()
#14 0x08097d7e in ?? ()
#15 0x0805efa8 in ?? ()
#16 0x080606bf in ?? ()
#17 0x0806123e in ?? ()
#18 0x080d8b4e in ?? ()
#19 0x0016c066 in ?? ()
#20 0x0018c4f4 in ?? ()
#21 0x08061328 in ?? ()
#22 0x0813c890 in mono_runtime_invoke ()
#23 0x081403de in mono_runtime_exec_main ()
#24 0x081406e2 in mono_runtime_run_main ()
#25 0x080b2f99 in mono_main ()
#26 0x08059385 in ?? ()
#27 0x00ddece7 in __libc_start_main () from /lib/libc.so.6
#28 0x080592c1 in ?? ()

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

/usr/bin/gfax: line 37:  2038 Aborted                 mono /usr/lib/gfax/gfax.exe $@

```

---

### Post by MG&amp;TL on 2011-11-15
Technical term here-that's messed-up. I suggest contacting the programmer, and finding an alternative. Short of patching the program....:confused:

---

### Post by directhex on 2011-11-17
Looks like it's broken, presumably by GConf in Oneiric

---

### Post by oxf on 2011-11-17
Wonderful, just my luck! :rolleyes: 

Well thanks anyway guys for trying.

Katja

---

