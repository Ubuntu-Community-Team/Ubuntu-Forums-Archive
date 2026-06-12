---
title: "Error with Mono"
date: 2011-09-05
forum: General Help
---

### Post by danpe on 2011-09-05
Hey i'm trying to run my C# WinForms .NET 3.5 on ubunto using Mono 2.6.7

This is the error i get:

```
ThinkPad-X201-Tablet:~/Desktop$ mono "Multiplier.exe"

** (Multiplier.exe:9156): WARNING **: Missing method .ctor in assembly /usr/lib/mono/gac/System.Windows.Forms/2.0.0.0__b77a5c561934e089/System.Windows.Forms.dll, type System.Runtime.CompilerServices.RuntimeCompatibilityAttribute

** (Multiplier.exe:9156): WARNING **: The class System.Runtime.CompilerServices.RuntimeCompatibilityAttribute could not be loaded, used in System.Windows.Forms

** (Multiplier.exe:9156): WARNING **: Can't find custom attr constructor image: /usr/lib/mono/gac/System.Windows.Forms/2.0.0.0__b77a5c561934e089/System.Windows.Forms.dll mtoken: 0x0a0007e2
**
ERROR:exception.c:60:mono_exception_from_name_domain: assertion failed: (o != NULL)
Stacktrace:

  at (wrapper managed-to-native) System.Reflection.MonoMethod.InternalInvoke (object,object[],System.Exception&) <0x00004>
  at (wrapper managed-to-native) System.Reflection.MonoMethod.InternalInvoke (object,object[],System.Exception&) <0x00004>
  at System.Reflection.MonoMethod.Invoke (object,System.Reflection.BindingFlags,System.Reflection.Binder,object[],System.Globalization.CultureInfo) <0x00110>
  at System.Reflection.MethodBase.Invoke (object,object[]) <0x00025>
  at System.Windows.Forms.Application.InitializeUIAutomation () <0x000da>
  at System.Windows.Forms.Application..cctor () <0x00088>
  at (wrapper runtime-invoke) object.runtime_invoke_void (object,intptr,intptr,intptr) <0x0003a>
  at Multiplier.Program.Main () <0xffffffff>
  at Multiplier.Program.Main () <0x0000b>
  at (wrapper runtime-invoke) object.runtime_invoke_void (object,intptr,intptr,intptr) <0x0003a>

Native stacktrace:

    mono() [0x80dbc5b]
    [0xb781a40c]
    /lib/i386-linux-gnu/libc.so.6(abort+0x17e) [0xb75a634e]
    /lib/i386-linux-gnu/libglib-2.0.so.0(g_assertion_message+0x150) [0xb778e3a0]
    /lib/i386-linux-gnu/libglib-2.0.so.0(+0x6897d) [0xb778e97d]
    mono() [0x813fa54]
    mono(mono_exception_from_name+0x28) [0x813fa88]
    mono(mono_exception_from_name_msg+0x24) [0x813fb74]
    mono() [0x8062440]
    mono() [0x8062d68]
    mono(mono_runtime_invoke+0x3e) [0x8192eee]
    mono(mono_runtime_invoke_array+0x2a0) [0x81967a0]
    mono() [0x814a098]
    [0xb58b8848]
    [0xb58b84a9]
    [0xb58b838e]
    [0xb58b770b]
    [0xb58b43a1]
    [0xb58b4283]
    mono() [0x8062bc8]
    mono(mono_runtime_invoke+0x3e) [0x8192eee]
    mono() [0x8197bba]
    mono() [0x806239f]
    mono() [0x8062ade]
    mono() [0x80dcd40]
    [0xb7807066]
    [0xb58b4283]
    mono() [0x8062bc8]
    mono(mono_runtime_invoke+0x3e) [0x8192eee]
    mono(mono_runtime_exec_main+0xe0) [0x81959e0]
    mono(mono_runtime_run_main+0x11d) [0x8195ced]
    mono(mono_main+0x1676) [0x80b7706]
    mono() [0x8059355]
    /lib/i386-linux-gnu/libc.so.6(__libc_start_main+0xe7) [0xb758ee37]
    mono() [0x8059291]

Debug info from gdb:

Could not attach to process.  If your uid matches the uid of the target
process, check the setting of /proc/sys/kernel/yama/ptrace_scope, or try
again as the root user.  For more details, see /etc/sysctl.d/10-ptrace.conf
ptrace: Operation not permitted.

=================================================================
Got a SIGABRT while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted

```

Any suggestions?

---

### Post by directhex on 2011-09-06
Looks like your Mono install is corrupted. Install apt:debsums and run "debsums -c" in a terminal. I expect some of your Mono libs have been overwritten.

---

