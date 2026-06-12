---
title: "If I install 32 bit..."
date: 2010-08-11
forum: General Help
---

### Post by J V on 2010-08-11
If I install 32bit linux on my 64bit machine will 32bit flash finally work? Can I still run 64bit applications?

---

### Post by howefield on 2010-08-11
> **J V said:**
> If I install 32bit linux on my 64bit machine will 32bit flash finally work?

Yes, 32 bit flash should be fine on a 32 bit system, (although no issues here running on a 64 bit system)

> Can I still run 64bit applications?

No.

You can get most 32 bit applications to run in a 64 bit operating system but not the other way round.

---

### Post by realzippy on 2010-08-11
Yes.
No.(why should it?)

BTW,flash (32) also works fine on 64 bit machines..

---

### Post by J V on 2010-08-11
Unfortunately, 32 bit flash doesn't work well at all on my system (Rarely responds to clicks) , and the 64 bit version was discontinued when they found the MAJOR security hole so I'm not going to use that...

So application compatibility is mainly dependant on the OS rather than the hardware? Thanks.

---

### Post by howefield on 2010-08-11
> **J V said:**
> Unfortunately, 32 bit flash doesn't work well at all on my system (Rarely responds to clicks)

Did you try this fix for button issues ?

Open a terminal and type

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

press enter, and place the following on a new line before the last line.

```
export GDK_NATIVE_WINDOWS=1
```

---

### Post by J V on 2010-08-11
Awesome! Thanks howefield, you just fixed my flash :D

---

### Post by Bachstelze on 2010-08-11
> **J V said:**
> 
So application compatibility is mainly dependant on the OS rather than the hardware? Thanks.

It is dependent on both. Normally this is not an issue because there is no discrepancy: a SPARC processor can only run SPARC programs, not PowerPC or MIPS or Alpha programs.  But because x86-64 is not a brand new architecture, but an hybrid 64-bit IA32, and still capable of running IA32 programs, is why there is such confusion.

---

