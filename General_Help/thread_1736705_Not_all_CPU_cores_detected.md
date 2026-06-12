---
title: "Not all CPU cores detected"
date: 2011-04-22
forum: General Help
---

### Post by Kazulik on 2011-04-22
Hello, I am attempting to Run Ubuntu 10.10 on a system with 128 CPU cores (64 dual core processors), but Ubuntu is only detecting 32 cores. I've looked and looked and cannot find any information on this topic; is there a core limitation in the kernel configuration that  I missed? Currently I am using Ubuntu 10.10 Desktop, would I have more luck with 10.10 Server or another version?

Thanks in advance.

---

### Post by Yellow Pasque on 2011-04-22
What are you doing with this machine? Are you using 64-bit or 32-bit Ubuntu? Looking at 64-bit natty's kernel config, I see:
> CONFIG_NR_CPUS=256

So I don't think the stock kernel is limiting you in that way.

---

### Post by SavageWolf on 2011-04-22
What is this sytem doing? If it's a server, you don't need to waste power on a GUI.

---

### Post by ChrisWells on 2011-04-22
Did you not research in advance before you acquired this machine? lol

---

### Post by KegHead on 2011-04-22
Hi!

Could you check:

system...administration..system monitor...resources

And advise?

Thanks!

KegHead

---

### Post by tgm4883 on 2011-04-22
> **KegHead said:**
> Hi!

Could you check:

system...administration..system monitor...resources

And advise?

Thanks!

KegHead

Or try 

```
cat /proc/cpuinfo | grep -i processor | wc -l
```

---

### Post by KegHead on 2011-04-22
Hi!

You know what's weird?

I'm running a crappy atom based desktop.

jim@jim:~$ cat /proc/cpuinfo | grep -i processor | wc -l
4
jim@jim:~$ 

KegHead

---

### Post by Kazulik on 2011-04-22
A lesson in using your brain before posting. About 10 minutes after posting this, I checked the cpu info manually and it lists all 64 physical CPU cores... the Desktop GUI just seems to only list 32 of them. Shouldn't be a problem.

As to wasting resources on the GUI... it was requested by some non-linux savvy people to have it GUI based. It shouldn't have a major impact on what we are attempting to accomplish.

---

### Post by tgm4883 on 2011-04-22
> **KegHead said:**
> Hi!

You know what's weird?

I'm running a crappy atom based desktop.

jim@jim:~$ cat /proc/cpuinfo | grep -i processor | wc -l
4
jim@jim:~$ 

KegHead

Interesting, what about

```
cat /proc/cpuinfo | grep -i processor -A 4
```

---

### Post by KegHead on 2011-04-22
jim@jim:~$ cat /proc/cpuinfo | grep -i processor -A 4
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU  330   @ 1.60GHz
--
processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU  330   @ 1.60GHz
--
processor	: 2
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU  330   @ 1.60GHz
--
processor	: 3
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU  330   @ 1.60GHz
jim@jim:~$

---

### Post by Yellow Pasque on 2011-04-22
> **KegHead said:**
> jim@jim:~$ cat /proc/cpuinfo | grep -i processor -A 4
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU  330   @ 1.60GHz
--
processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU  330   @ 1.60GHz
--
processor	: 2
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU  330   @ 1.60GHz
--
processor	: 3
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU  330   @ 1.60GHz
jim@jim:~$
Yeah, you have a dual-core Atom with Hyperthreading, so it presents itself as 4 virtual cores. This is normal..

---

### Post by KegHead on 2011-04-22
Hi!

Got it!

Thanks!

KegHead

---

