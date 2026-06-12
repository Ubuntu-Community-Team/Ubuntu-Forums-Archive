---
title: "Bus error in apt: What happened, and how I debugged it."
date: 2010-12-04
forum: General Help
---

### Post by jjpcexpert on 2010-12-04
For the purpose of the debugging, I was trying to install or update metacity.

So I had two terminals open. I was trying to find out why Software Center wasn't starting. I was trying to find out why Synaptic crashed on load.

I opened one terminal. sudo apt-get install metacity
```
Reading package lists... Done
Bus errordependency tree 0%
```
which apt-get
```
/usr/bin/apt-get
```
So, at the $, I typed gdb /usr/bin/apt-get .
```
<truncated output of command 4readability purposes />
<a few commands to get a grip on gdb for now>
(gdb) run install metacity
Reading package lists... Done
Building dependency tree 0%
Program received signal SIGBUS, Bus error.
0x0017c319 in pkgDepCache::Init(OpProgress*) ()
   from /usr/lib/libapt-pkg.so.4.10
```
Weird. I have no debug symbols. But I run backtrace anyway.
First time I ran it:
```
#0  0x0017c319 in pkgDepCache::Init(OpProgress*) ()
   from /usr/lib/libapt-pkg.so.4.10
#1  0x001a35c0 in pkgCacheFile::BuildDepCache(OpProgress*) ()
   from /usr/lib/libapt-pkg.so.4.10
#2  0x001a3bc4 in pkgCacheFile::Open(OpProgress*, bool) ()
   from /usr/lib/libapt-pkg.so.4.10
#3  0x0805a547 in ?? ()
#4  0x0015cae0 in CommandLine::DispatchArg(CommandLine::Dispatch*, bool) ()
   from /usr/lib/libapt-pkg.so.4.10
#5  0x080534fb in ?? ()
#6  0x00372ce7 in __libc_start_main () from /lib/libc.so.6
#7  0x0804e9c1 in ?? ()
```

Second time:
```
#0  0x0017c319 in pkgDepCache::Init(OpProgress*) ()
   from /usr/lib/libapt-pkg.so.4.10
#1  0x001a35c0 in pkgCacheFile::BuildDepCache(OpProgress*) ()
   from /usr/lib/libapt-pkg.so.4.10
#2  0x001a3bc4 in pkgCacheFile::Open(OpProgress*, bool) ()
   from /usr/lib/libapt-pkg.so.4.10
#3  0x0805a547 in ?? ()
#4  0x0015cae0 in CommandLine::DispatchArg(CommandLine::Dispatch*, bool) ()
   from /usr/lib/libapt-pkg.so.4.10
#5  0x080534fb in ?? ()
#6  0x00372ce7 in __libc_start_main () from /lib/libc.so.6
#7  0x0804e9c1 in ?? ()
```

So I am baffled.
I also have no available.bak.

---

### Post by wojox on 2010-12-04
```
sudo rm /var/cache/apt/*.bin
```

[Source...]("https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/192567")

---

### Post by jjpcexpert on 2010-12-04
> **jjpcexpert said:**
> For the purpose of the debugging, I was trying to install or update metacity.
 
So I had two terminals open. I was trying to find out why Software Center wasn't starting. I was trying to find out why Synaptic crashed on load.
 
I opened one terminal. sudo apt-get install metacity
```
Reading package lists... Done
Bus errordependency tree 0%
```
which apt-get
```
/usr/bin/apt-get
```
So, at the $, I typed gdb /usr/bin/apt-get .
```
<truncated output of command 4readability purposes />
<a few commands to get a grip on gdb for now>
(gdb) run install metacity
Reading package lists... Done
Building dependency tree 0%
Program received signal SIGBUS, Bus error.
0x0017c319 in pkgDepCache::Init(OpProgress*) ()
   from /usr/lib/libapt-pkg.so.4.10
```
Weird. I have no debug symbols. But I run backtrace anyway.
First time I ran it:
```
#0  0x0017c319 in pkgDepCache::Init(OpProgress*) ()
   from /usr/lib/libapt-pkg.so.4.10
#1  0x001a35c0 in pkgCacheFile::BuildDepCache(OpProgress*) ()
   from /usr/lib/libapt-pkg.so.4.10
#2  0x001a3bc4 in pkgCacheFile::Open(OpProgress*, bool) ()
   from /usr/lib/libapt-pkg.so.4.10
#3  0x0805a547 in ?? ()
#4  0x0015cae0 in CommandLine::DispatchArg(CommandLine::Dispatch*, bool) ()
   from /usr/lib/libapt-pkg.so.4.10
#5  0x080534fb in ?? ()
#6  0x00372ce7 in __libc_start_main () from /lib/libc.so.6
#7  0x0804e9c1 in ?? ()
```
 
Second time:
```
#0  0x0017c319 in pkgDepCache::Init(OpProgress*) ()
   from /usr/lib/libapt-pkg.so.4.10
#1  0x001a35c0 in pkgCacheFile::BuildDepCache(OpProgress*) ()
   from /usr/lib/libapt-pkg.so.4.10
#2  0x001a3bc4 in pkgCacheFile::Open(OpProgress*, bool) ()
   from /usr/lib/libapt-pkg.so.4.10
#3  0x0805a547 in ?? ()
#4  0x0015cae0 in CommandLine::DispatchArg(CommandLine::Dispatch*, bool) ()
   from /usr/lib/libapt-pkg.so.4.10
#5  0x080534fb in ?? ()
#6  0x00372ce7 in __libc_start_main () from /lib/libc.so.6
#7  0x0804e9c1 in ?? ()
```
 
So I am baffled.
I also have no available.bak.
 
> **wojox said:**
> ```
sudo rm /var/cache/apt/*.bin
```
 
[Source...]("https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/192567")
 
I had an unrecovered read error. My hard drive is only 7 mths old, and I have an eczema-style scratching rash on my left wrist if that's relevant!!£"£T%£$^£%^&£"$%^£^"$£^%%%$^^&^^%&^&%&^%£"${{{}@{@{@

---

