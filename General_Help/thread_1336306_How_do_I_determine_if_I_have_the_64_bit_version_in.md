---
title: "How do I determine if I have the 64 bit version installed?"
date: 2009-11-24
forum: General Help
---

### Post by willsomebody on 2009-11-24
I feel rather foolish in that I was too lazy to label my Ubuntu CDs when I made them.  I installed from what I thought was a 64 bit CD, but the 64 bit Google Chrome package said it was the wrong architecture.  I am not sure if that was wrong because it is an unstable dev release, or if I accidentally installed the 32 bit version.  I figure there has to be an easy way to find out for sure which version of Ubuntu 9.10 I installed.  Does anyone know it?  Maybe an system information window, or a command that will tell me?

---

### Post by Darael on 2009-11-24
I realise what I'm about to do isn't polite, but, well, *really!*
[http://lmgtfy.com/?=ubuntu+determine+architecture](http://lmgtfy.com/?=ubuntu+determine+architecture)

---

### Post by Raff1 on 2009-11-24
[http://ubuntuforums.org/showthread.php?t=299625](http://ubuntuforums.org/showthread.php?t=299625)

> The command you are looking for is uname. "uname -a" will display your kernel and some additional info. Look for something like i686 or amd64. It's likely one of those. i686 => 32 bit 
amd64 => 64 bit

> **Darael said:**
> I realise what I'm about to do isn't polite, but, well, *really!*
[http://lmgtfy.com/?=ubuntu+determine+architecture](http://lmgtfy.com/?=ubuntu+determine+architecture)

You link was bad (at least here), but I still got your point :-)

---

### Post by EndPerform on 2009-11-24
```
fubar@snafu:~$ uname -a
Linux uxsnafu 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux

```

uname -a will give you what you want.  Pay attention to the last bit:

x86_64 means you're running the 64bit version.

---

### Post by howefield on 2009-11-24
> **Darael said:**
> I realise what I'm about to do isn't polite, but, well, *really!*
[http://lmgtfy.com/?=ubuntu+determine+architecture](http://lmgtfy.com/?=ubuntu+determine+architecture)

Translation = I haven't a clue...

:lolflag::lolflag:

---

### Post by Darael on 2009-11-24
> **howefield said:**
> Translation = I haven't a clue...

:lolflag::lolflag:
Quite correct - but since an answer was on the first page of the result (had I got the link right!) that really didn't matter too much.  :P.

---

### Post by willsomebody on 2009-11-24
Thanks for the quick answer.  I couldn't find it when I googled it, but I guess I wasn't using the right keywords.

---

