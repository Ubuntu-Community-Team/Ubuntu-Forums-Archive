---
title: "Boot troubleshoot"
date: 2010-01-28
forum: General Help
---

### Post by YesSir on 2010-01-28
Hello all,

Recently I installed Ubuntu at work and experienced some boot troubles. Finally I recovered and everything is up and running. In case something like this happens at home, I have time to figure it out. But at work I can not lose time looking for solutions.

So, in your opinion, is Ubuntu likely to boot every time without problems? 

If not, could you indicate some troubleshooting ideas, so next time my system won't boot, I can quickly recover and continue working?

Thanks everybody :)

---

### Post by rnerwein on 2010-01-28
hi
have look here - and print it out ( did it too )
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
ciao

sorry i forgot - are you using grub2 ( in a commandline type: grub-install -v )

---

### Post by YesSir on 2010-01-28
Thanks, will read it! (It says grub 0.97).

---

### Post by drs305 on 2010-01-28
> **YesSir said:**
> Thanks, will read it! (It says grub 0.97).

That means you are still using Grub legacy. The community doc link is for Grub 2, although there are sections for installing Grub 2 and also for reverting to Grub legacy.

---

### Post by oldfred on 2010-01-28
Anytime one has boot issues the best tool is the latest copy of this as it runs multiple commands and outputs a nice listing of the results.

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

I run it on my own system to understand what is where and it shows the MBR and PBR as well.

---

### Post by YesSir on 2010-01-29
Thanks guys, more material to read this weekend ;)

---

