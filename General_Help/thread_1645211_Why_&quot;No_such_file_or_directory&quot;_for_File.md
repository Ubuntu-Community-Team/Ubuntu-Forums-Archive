---
title: "Why &quot;No such file or directory&quot; for File That's There?"
date: 2010-12-14
forum: General Help
---

### Post by LaneLester on 2010-12-14
I'm running Natty 64-bit. I have a small executable that has run in all versions of Linux I've used, and that's quite a few. This is what I get now when I try to run it:

me@PC1:/opt# ./Captura
bash: ./Captura: No such file or directory

And yet it is there with permissions set at 777:

me@PC1:/opt# ls -l Ca*
-rwxrwxrwx 1 root root 1609919 2001-08-14 16:29 Captura

Why am I getting that error message?

Lane

---

### Post by a-user on 2010-12-14
what happens if you call "/opt/Captura"?

---

### Post by katykat on 2010-12-14
Perhaps an AppArmor problem???

---

### Post by oldos2er on 2010-12-14
What's ```
file /opt/Captura
``` say?

---

### Post by dcstar on 2010-12-15
> **LaneLester said:**
> I'm running Natty 64-bit. I have a small executable that has run in all versions of Linux I've used, and that's quite a few. This is what I get now when I try to run it:

me@PC1:/opt# ./Captura
bash: ./Captura: No such file or directory

And yet it is there with permissions set at 777:

me@PC1:/opt# ls -l Ca*
-rwxrwxrwx 1 root root 1609919 2001-08-14 16:29 Captura

Why am I getting that error message?


Because you are trying to run a 32-bit compiled file on a 64-bit system.

---

### Post by kullan on 2010-12-15
Because you are trying to run a 32-bit compiled file on a 64-bit system.  L)

---

### Post by LaneLester on 2010-12-15
> **kullan said:**
> Because you are trying to run a 32-bit compiled file on a 64-bit system.  L)

Yes, I am. :redface:

Thanks for the analysis. I would have thought a different error message would be generated, but at least now I know why I can't run it.

And for the earlier question, yes, I get the same thing:
me@PC1:~# /opt/Captura
bash: /opt/Captura: No such file or directory

Lane

---

### Post by oldos2er on 2010-12-15
You just need to install ia32-libs to run it.

---

### Post by LaneLester on 2010-12-16
> **oldos2er said:**
> You just need to install ia32-libs to run it.

Thanks, Phyllis... I mean, Ann!

That did the trick, and I'm glad to have it working again. Every distro has some kind of screen capture program, but this oldie-but-goodie is small, fast, and easy to use.

Lane

---

