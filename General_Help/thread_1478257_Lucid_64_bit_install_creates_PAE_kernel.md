---
title: "Lucid 64 bit install creates PAE kernel?"
date: 2010-05-09
forum: General Help
---

### Post by at both ends on 2010-05-09
I have been running 64 bit Koala on an HP desktop with 8 GB for a few months. Now that Lucid is out and the kernel has stopped changing every three days, I thought I would do a clean install of 64 bit Lucid. Backed everything up, verified the .iso I downloaded a few days ago and burned a CD, and away we go. Everything seems clean, finds the old /home, asks for a restart.  I say go.

Suddenly there are way more options on my grub menu. Every Linux option has an alternate with PAE, and the PAE option is the default boot.  I didn't even think about it and let it take the default. The reboot hangs. I had to pull the plug to turn the machine off.

I reboot again with PAE. It hangs again. Pull the plug. Reboot without PAE and I'm golden. Google soon turns up all sorts of old advice to add noapic to the boot parameters on a PAE kernel. Instead I sat back and started thinking.

WTF am I doing with a kernel marked PAE in the first place? This is a 64 bit install. It doesn't need PAE. I look again at the .iso and it's 64 bit.

```
$ uname -a
Linux ####### 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux
```Looks like 64 bit to me.

Can someone tell me why I have PAE options that will not boot?

---

### Post by dino99 on 2010-05-09
"pae" offer tthe advantages of 64 bits to a 32 bits (able to use the maximum ram), note that there are less problems with 32 bits (sound, java, chipset, printer, ...)

---

### Post by jerome1232 on 2010-05-09
> **dino99 said:**
> "pae" offer tthe advantages of 64 bits to a 32 bits (able to use the maximum ram), note that there are less problems with 32 bits (sound, java, chipset, printer, ...)

Did you read the OP?

That mystifies me as well, I did also install from a 64 bit cd and did not have this problem.

my uname -a is the 64 bit kernel and everything is right with this world here.

```
Linux main 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux

```

---

### Post by dino99 on 2010-05-09
> **jerome1232 said:**
> Did you read the OP?

That mystifies me as well, I did also install from a 64 bit cd and did not have this problem.

my uname -a is the 64 bit kernel and everything is right with this world here.

```
Linux main 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux

```

sorry i've not send the codec :confused:

---

### Post by howefield on 2010-05-09
> **at both ends said:**
> ....Now that Lucid is out and the kernel has stopped changing every three days, I thought I would do a clean install of 64 bit Lucid.

Actually, there is another kernel waiting in updates for you ;)

```
Linux lucid 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
```

---

### Post by dcstar on 2010-05-10
> **at both ends said:**
> I have been running 64 bit Koala on an HP desktop with 8 GB for a few months. Now that Lucid is out and the kernel has stopped changing every three days, I thought I would do a clean install of 64 bit Lucid. Backed everything up, verified the .iso I downloaded a few days ago and burned a CD, and away we go. Everything seems clean, finds the old /home, asks for a restart.  I say go.

Suddenly there are way more options on my grub menu. Every Linux option has an alternate with PAE, and the PAE option is the default boot.
.........
Can someone tell me why I have PAE options that will not boot?

update-grub searches ALL of the available hard drive partitions for any bootable systems, update-grub is run when new kernels are installed.

What did you have plugged into the machine when the last update occurred?

---

