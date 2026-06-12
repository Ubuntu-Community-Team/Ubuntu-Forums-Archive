---
title: "Software to manage iPod Nano 5th Gen"
date: 2009-10-22
forum: General Help
---

### Post by Gosport on 2009-10-22
Is there any method for managing the new iPod Nano 5th Gen for Linux users?  What is the best way to do this?  Gtkpod only supports 4th Gen, and my attempt at running iTunes under Wine was unsuccessful.   How do _you_ do it?

---

### Post by Gosport on 2009-10-22
bump

---

### Post by Simian Man on 2009-10-22
So Apple has ****** over its users once again...I got a 4th gen soon after it came out and had to wait around a month until libgpod supported it.  Just run Windows in a VM / dual boot until the clever guys working on libgpod figure it out.

---

### Post by vinutux on 2009-10-22
Try songbird or banshee ..........

---

### Post by Gosport on 2009-10-22
A month doesn't seem too bad.  I tried Banshee, but then again, I'm not familiar with iPods, and that may have been half my problem.

Has anyone been successful managing the new 5th Gen iPod Nano with Banshee or Songbird?

---

### Post by vinutux on 2009-10-22
Apple try to block third party apps accessing their products in every releases.............

---

### Post by Gosport on 2009-10-23
Don't both Songbird and Banshee depend on libgpod?

---

### Post by vinutux on 2009-10-23
Check Rockbox **[http://www.rockbox.org/]("http://www.rockbox.org/")**

---

### Post by Simian Man on 2009-10-26
> **Gosport said:**
> Don't both Songbird and Banshee depend on libgpod?
Songbird does so if Rhythmbox, Exaile etc. don't support your iPod, then Songbird won't either.  Banshee uses its own library for managing iPods, but I have found that it doesn't work nearly as well as libgpod.  Also IIRC it will not support *any* ipods under the next version of Ubuntu do the deprecation of HAL.  It is probably worth a try though.

Another program that uses its own software for managing your ipod is Floola but, judging from their download page, they are having the same problems as libgpod.

> **vinutux said:**
> Check Rockbox **[http://www.rockbox.org/]("http://www.rockbox.org/")**

Rockbox does not run on *any* iPod nanos let alone the latest one.

Like I said before, you will have to use Windows in some fashion for the time being.  Hopefully someone will fix this before too long :\

---

### Post by Gosport on 2009-10-26
Thanks for the info Simian Man!

---

### Post by MauritsMB on 2009-11-27
We'll just wait and see...

---

### Post by Chronon on 2009-11-27
> **Simian Man said:**
> 
Rockbox does not run on *any* iPod nanos let alone the latest one.

Actually, Rockbox runs on 1st and 2nd generation Nanos.

---

