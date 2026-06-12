---
title: "Mono applications claim missing System.DLL?"
date: 2009-08-29
forum: General Help
---

### Post by zvilikestv on 2009-08-29
A couple of days ago I installed a bunch of security updates that had to do with mono, but I didn't really read what the updates said, because I almost never understand them anyway.

After I installed the updates, I stopped being able to open Tomboy or Tasque. (I don't think I have any other mono apps installed. I uninstalled F-Spot when I upgraded to Jaunty, and didn't have any problems with Tomboy or Tasque.)

When I try to open Tomboy, I get the error:

> Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for Mono.Unix.Native.Stdlib ---> System.DllNotFoundException: libMonoPosixHelper.so
  at (wrapper managed-to-native) Mono.Unix.Native.Stdlib:GetDefaultSignal ()
  at Mono.Unix.Native.Stdlib..cctor () [0x00000] 
  --- End of inner exception stack trace ---
  at Mono.Unix.UnixMarshal.AllocHeap (Int64 size) [0x00000] 
  at Mono.Unix.UnixMarshal.StringToHeap (System.String s, Int32 index, Int32 count, System.Text.Encoding encoding) [0x00000] 
  at Mono.Unix.UnixMarshal.StringToHeap (System.String s, System.Text.Encoding encoding) [0x00000] 
  at Mono.Unix.UnixMarshal.StringToHeap (System.String s) [0x00000] 
  at Mono.Unix.Catalog.MarshalStrings (System.String s1, System.IntPtr& p1, System.String s2, System.IntPtr& p2, System.String s3, System.IntPtr& p3) [0x00000] 
  at Mono.Unix.Catalog.Init (System.String package, System.String localedir) [0x00000] 
  at Tomboy.Tomboy.Main (System.String[] args) [0x00000] 

Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for Mono.Unix.Native.Stdlib ---> System.DllNotFoundException: libMonoPosixHelper.so
  at (wrapper managed-to-native) Mono.Unix.Native.Stdlib:GetDefaultSignal ()
  at Mono.Unix.Native.Stdlib..cctor () [0x00000] 
  --- End of inner exception stack trace ---
  at Mono.Unix.UnixMarshal.AllocHeap (Int64 size) [0x00000] 
  at Mono.Unix.UnixMarshal.StringToHeap (System.String s, Int32 index, Int32 count, System.Text.Encoding encoding) [0x00000] 
  at Mono.Unix.UnixMarshal.StringToHeap (System.String s, System.Text.Encoding encoding) [0x00000] 
  at Mono.Unix.UnixMarshal.StringToHeap (System.String s) [0x00000] 
  at Mono.Unix.Catalog.MarshalStrings (System.String s1, System.IntPtr& p1, System.String s2, System.IntPtr& p2, System.String s3, System.IntPtr& p3) [0x00000] 
  at Mono.Unix.Catalog.Init (System.String package, System.String localedir) [0x00000] 
  at Tomboy.Tomboy.Main (System.String[] args) [0x00000] When I try to open Tasque, I get the error > [Debug]: Exception is: System.TypeInitializationException: An exception was thrown by the type initializer for Mono.Unix.Native.Stdlib ---> System.DllNotFoundException: libMonoPosixHelper.so
  at (wrapper managed-to-native) Mono.Unix.Native.Stdlib:GetDefaultSignal ()
  at Mono.Unix.Native.Stdlib..cctor () [0x00000] 
  --- End of inner exception stack trace ---
  at Mono.Unix.UnixMarshal.AllocHeap (Int64 size) [0x00000] 
  at Mono.Unix.UnixMarshal.StringToHeap (System.String s, Int32 index, Int32 count, System.Text.Encoding encoding) [0x00000] 
  at Mono.Unix.UnixMarshal.StringToHeap (System.String s, System.Text.Encoding encoding) [0x00000] 
  at Mono.Unix.UnixMarshal.StringToHeap (System.String s) [0x00000] 
  at Mono.Unix.Catalog.MarshalStrings (System.String s1, System.IntPtr& p1, System.String s2, System.IntPtr& p2, System.String s3, System.IntPtr& p3) [0x00000] 
  at Mono.Unix.Catalog.Init (System.String package, System.String localedir) [0x00000] 
  at Tasque.GnomeApplication.Initialize (System.String locale_dir, System.String display_name, System.String process_name, System.String[] args) [0x00000] 
  at Tasque.Application.Init (System.String[] args) [0x00000] 
  at Tasque.Application..ctor (System.String[] args) [0x00000] 
  at Tasque.Application.GetApplicationWithArgs (System.String[] args) [0x00000] 
  at Tasque.Application.Main (System.String[] args) [0x00000] 

Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for Mono.Unix.Native.Stdlib ---> System.DllNotFoundException: libMonoPosixHelper.so
  at (wrapper managed-to-native) Mono.Unix.Native.Stdlib:GetDefaultSignal ()
  at Mono.Unix.Native.Stdlib..cctor () [0x00000] 
  --- End of inner exception stack trace ---
  at Mono.Unix.UnixMarshal.AllocHeap (Int64 size) [0x00000] 
  at Mono.Unix.UnixMarshal.StringToHeap (System.String s, Int32 index, Int32 count, System.Text.Encoding encoding) [0x00000] 
  at Mono.Unix.UnixMarshal.StringToHeap (System.String s, System.Text.Encoding encoding) [0x00000] 
  at Mono.Unix.UnixMarshal.StringToHeap (System.String s) [0x00000] 
  at Mono.Unix.Catalog.MarshalStrings (System.String s1, System.IntPtr& p1, System.String s2, System.IntPtr& p2, System.String s3, System.IntPtr& p3) [0x00000] 
  at Mono.Unix.Catalog.Init (System.String package, System.String localedir) [0x00000] 
  at Tasque.GnomeApplication.Initialize (System.String locale_dir, System.String display_name, System.String process_name, System.String[] args) [0x00000] 
  at Tasque.Application.Init (System.String[] args) [0x00000] 
  at Tasque.Application..ctor (System.String[] args) [0x00000] 
  at Tasque.Application.GetApplicationWithArgs (System.String[] args) [0x00000] 
  at Tasque.Application.Main (System.String[] args) [0x00000] 

Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for Mono.Unix.Native.Stdlib ---> System.DllNotFoundException: libMonoPosixHelper.so
  at (wrapper managed-to-native) Mono.Unix.Native.Stdlib:GetDefaultSignal ()
  at Mono.Unix.Native.Stdlib..cctor () [0x00000] 
  --- End of inner exception stack trace ---
  at Mono.Unix.UnixMarshal.AllocHeap (Int64 size) [0x00000] 
  at Mono.Unix.UnixMarshal.StringToHeap (System.String s, Int32 index, Int32 count, System.Text.Encoding encoding) [0x00000] 
  at Mono.Unix.UnixMarshal.StringToHeap (System.String s, System.Text.Encoding encoding) [0x00000] 
  at Mono.Unix.UnixMarshal.StringToHeap (System.String s) [0x00000] 
  at Mono.Unix.Catalog.MarshalStrings (System.String s1, System.IntPtr& p1, System.String s2, System.IntPtr& p2, System.String s3, System.IntPtr& p3) [0x00000] 
  at Mono.Unix.Catalog.Init (System.String package, System.String localedir) [0x00000] 
  at Tasque.GnomeApplication.Initialize (System.String locale_dir, System.String display_name, System.String process_name, System.String[] args) [0x00000] 
  at Tasque.Application.Init (System.String[] args) [0x00000] 
  at Tasque.Application..ctor (System.String[] args) [0x00000] 
  at Tasque.Application.GetApplicationWithArgs (System.String[] args) [0x00000] 
  at Tasque.Application.Main (System.String[] args) [0x00000]I tried uninstalling and reinstalling both apps with apt, but that didn't seem to make any difference. I tried to figure out how to reinstall mono, but none of the uninstall directions included reinstall, and all of the install directions seemed to be directions for developer tools, not just the environment for running applications.

Any help would be appreciated.

---

### Post by directhex on 2009-08-30
> **zvilikestv said:**
> A couple of days ago I installed a bunch of security updates that had to do with mono, but I didn't really read what the updates said, because I almost never understand them anyway.

After I installed the updates, I stopped being able to open Tomboy or Tasque. (I don't think I have any other mono apps installed. I uninstalled F-Spot when I upgraded to Jaunty, and didn't have any problems with Tomboy or Tasque.)

When I try to open Tomboy, I get the error:

When I try to open Tasque, I get the error I tried uninstalling and reinstalling both apps with apt, but that didn't seem to make any difference. I tried to figure out how to reinstall mono, but none of the uninstall directions included reinstall, and all of the install directions seemed to be directions for developer tools, not just the environment for running applications.

Any help would be appreciated.

Can you paste the output of the following:

dpkg -l mono-common
wc -l /etc/mono/config

---

### Post by Can+~ on 2009-08-30
I had the exact same problem.

I first noticed when I did Super+Space to call gnome-do, and realized that it wasn't installed.

```
~$gnome-do

Unhandled Exception: System.DllNotFoundException: intl
  at (wrapper managed-to-native) Mono.Unix.Catalog:bindtextdomain (intptr,intptr)
  at Mono.Unix.Catalog.Init (System.String package, System.String localedir) [0x00000] 
  at Do.Do.Main (System.String[] args) [0x00000] 

Unhandled Exception: System.DllNotFoundException: msvcrt
  at (wrapper managed-to-native) Mono.Unix.Native.Stdlib:free (intptr)
  at Mono.Unix.UnixMarshal.FreeHeap (IntPtr ptr) [0x00000] 
  at Mono.Unix.Catalog.Init (System.String package, System.String localedir) [0x00000] 
  at Do.Do.Main (System.String[] args) [0x00000]
```

And the problem also started when updating mono libs.

---

### Post by directhex on 2009-08-30
> **Can+~ said:**
> I had the exact same problem.

I first noticed when I did Super+Space to call gnome-do, and realized that it wasn't installed.

```
~$gnome-do

Unhandled Exception: System.DllNotFoundException: intl
  at (wrapper managed-to-native) Mono.Unix.Catalog:bindtextdomain (intptr,intptr)
  at Mono.Unix.Catalog.Init (System.String package, System.String localedir) [0x00000] 
  at Do.Do.Main (System.String[] args) [0x00000] 

Unhandled Exception: System.DllNotFoundException: msvcrt
  at (wrapper managed-to-native) Mono.Unix.Native.Stdlib:free (intptr)
  at Mono.Unix.UnixMarshal.FreeHeap (IntPtr ptr) [0x00000] 
  at Mono.Unix.Catalog.Init (System.String package, System.String localedir) [0x00000] 
  at Do.Do.Main (System.String[] args) [0x00000]
```

And the problem also started when updating mono libs.

Sounds ENORMOUSLY like a missing /etc/mono/

Which can sometimes happen if you delete it yourself, or only do a partial update from 2.0 to 2.4

---

### Post by zvilikestv on 2009-08-30
dpkg -l mono-common > Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                              Version                           Description
+++-=================================-=================================-==================================================================================
ii  mono-common                       2.0.1-4ubuntu0.1                  common files for Mono


wc -l /etc/mono/config> 26 /etc/mono/config

---

### Post by directhex on 2009-08-30
> **zvilikestv said:**
> dpkg -l mono-common 

wc -l /etc/mono/config

and dpkg -l libmono0 ?

---

### Post by zvilikestv on 2009-08-30
dpkg -l libmono0

> 
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                              Version                           Description
+++-=================================-=================================-==================================================================================
ii  libmono0                          2.4.2.3+dfsg-1~dhx1~jaunty1       Mono JIT library


---

### Post by directhex on 2009-08-30
> **zvilikestv said:**
> dpkg -l libmono0

Partial upgrade then, as I said. You've got pieces of 2.4.2, and pieces of 2.0.1 - and libmonoposixhelper.so moved from the libmono0 package to the mono-runtime package between those releases

---

### Post by zvilikestv on 2009-08-30
How would I do a complete upgrade to 2.4? I tried adding the monoxide ppa to my repositories, but I couldn't figure out what package to get with apt ...

---

### Post by directhex on 2009-08-31
> **zvilikestv said:**
> How would I do a complete upgrade to 2.4? I tried adding the monoxide ppa to my repositories, but I couldn't figure out what package to get with apt ...

Just run an upgrade - aptitude dist-upgrade, or let update manager actually update things, or whatever.

---

