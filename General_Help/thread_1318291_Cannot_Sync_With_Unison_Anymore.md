---
title: "Cannot Sync With Unison Anymore"
date: 2009-11-07
forum: General Help
---

### Post by jlacroix on 2009-11-07
I tried to sync my laptop to my desktop (which I've been doing for the last year or so without any issues) and I get the following message:

> 
Received unexpected header from the server:
 expected "Unison 2.27\n" but received "Unison 2.32\n\000\000\000\000", 
which differs at "Unison 2.3".
This can happen because you have different versions of Unison
installed on the client and server machines, or because
your connection is failing and somebody is printing an error
message, or because your remote login shell is printing
something itself before starting Unison.

My laptop is running Kubuntu 9.10 and my desktop is running Arch. Apparently, my laptop has version 2.27 and my desktop has version 2.32, and I searched for a compiled 2.32 binary for Kubuntu but I cannot find one.

I also tried to build it, and I have a command-line version of 2.32 I can run, but no GTK front-end to go with it. 

Is there any way I can package this for Kubuntu or do I have to wait until the developers do it?

---

### Post by jlacroix on 2009-11-07
Nevermind, I figured it out. :)

---

### Post by bardill on 2012-02-26
I am having the same error. Could you please be so kind to explain your solution?
Thanks!!

---

### Post by jlacroix on 2012-02-26
Each version of Unison on each machine must match. Make sure you're installing the correct version.

---

