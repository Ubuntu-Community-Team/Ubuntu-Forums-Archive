---
title: "Running jGrasp?"
date: 2011-10-28
forum: General Help
---

### Post by Radan53 on 2011-10-28
Hello everyone. I'm pretty new to ubuntu, and I was wondering how to run jGrasp.

Yes, I have read the other threads about running it. However, when I try to run the jgrasp shell, it does nothing.

I'm using ubuntu 11.10.

Any suggestions?

Thanks.

---

### Post by Radan53 on 2011-10-28
Hello everyone. I'm pretty new to ubuntu, and I was wondering how to run jGrasp.

Yes, I have seen the other threads on this; however, when I go to run the jgrasp shell, nothing happens.

I have ubuntu 11.10 if that matters.

Any suggestions?

- Thank you.

---

### Post by mörgæs on 2011-10-28
Please don't create multiple threads on the same subject. 
Threads merged.

---

### Post by lbarowski on 2011-10-28
Recent versions of jGRASP require lsb-core. If you don't already have it installed, you can do so from the command line with:

sudo apt-get install lsb-core

The latest Beta version of jGRASP will warn you if lsb-core is not installed, then go on to run in a pure-Java mode.

If you're still having problems, run from the command line so you can see any error messages from the startup script.

---

