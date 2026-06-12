---
title: "Gnome-do Error [will not load]"
date: 2009-07-31
forum: General Help
---

### Post by Catdaddy on 2009-07-31
Hi there I am having trouble getting Gnome-do to load and when i load it from console it spits out this error perhaps some one could help me

```
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
  at Do.Do.Main (System.String[] args) [0x00000] 

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
  at Do.Do.Main (System.String[] args) [0x00000] 

```
I am running 9.04 ubuntu.

---

### Post by directhex on 2009-07-31
> **Catdaddy said:**
> Hi there I am having trouble getting Gnome-do to load and when i load it from console it spits out this error perhaps some one could help me

```
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
  at Do.Do.Main (System.String[] args) [0x00000] 

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
  at Do.Do.Main (System.String[] args) [0x00000] 

```
I am running 9.04 ubuntu.

Your installation is corrupt. Either the /etc/mono folder has been corrupted in some way, or (as seems more likely in this case) the libmono0 package requires reinstallation

---

### Post by Catdaddy on 2009-08-02
What would you recommend I do? 
Should I reinstall mono-lib packages and if that's the case what would be the name of those packages.

---

### Post by directhex on 2009-08-03
aptitude reinstall libmono0

---

