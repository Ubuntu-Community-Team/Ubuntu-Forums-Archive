---
title: "FlightGear help"
date: 2006-05-02
forum: General Help
---

### Post by _simon_ on 2006-05-02
Has anyone got this running under ubuntu?

I just get this :(

```

simon@ubuntu:~$ fgfs
opening file: /usr/share/games/FlightGear/Navaids/carrier_nav.dat
/usr/share/games/FlightGear/Navaids/TACAN_freq.dat
Segmentation fault

```

---

### Post by _simon_ on 2006-05-03
anyone?

---

### Post by OzOle on 2006-06-17
Hi Simon,

I too can't get FlightGear to work and from reading the posts, we are not alone.

If I find out anything then I will mail you. Maybe you could do the same for me.

:sad: 

Cheers,

Ole

---

### Post by captrlm64 on 2006-06-21
HI,

Have you checked the  FlightGear users forum at the Flight Gear site? A thread just emerged on this topic: [Flightgear-users] Atlas-0.3.0 w/debian, and the posing person also had questions about installing in Ubuntu. I'm just up in this (Kubuntu Dapper) install and have not yet installed FlightGear.  The folks at their site have been very helpful in the past.

---

### Post by l.tambiah on 2006-06-23
Just to confirm I have flight gear running with no problems on dapper here...

---

### Post by SteinbergerNate on 2006-07-07
I'm getting the same problem except that I just get the segmentation fault. I don't get the additional information you're getting before it.
Edit: Except I see that this is in the Breezy Badger forum and I'm running Dapper.

---

### Post by SteinbergerNate on 2006-07-07
Well, I ran gdb and got this:
> bassmannate@bassmannate-laptop:~$ gdb fgfs
GNU gdb 6.4-debian
Copyright 2005 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".

(gdb) run
Starting program: /usr/games/fgfs
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
---Type <return> to continue, or q <return> to quit---
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1219709248 (LWP 18475)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread -1219709248 (LWP 18475)]
0xb793ac8f in glXGetConfig () from /usr/lib/libGL.so.1
(gdb)
Not sure if that last line in there means I have a problem with my openGL. I really hope not because it took me so long to get that up and running in Dapper.

---

