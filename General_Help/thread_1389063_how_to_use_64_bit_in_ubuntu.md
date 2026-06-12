---
title: "how to use 64 bit in ubuntu"
date: 2010-01-23
forum: General Help
---

### Post by sushilkumar on 2010-01-23
[COLOR=Blue][SIZE=4][SIZE=1][COLOR=Black]I am not Computer literate. I have installed Ubuntu on my home PC as it will avoid any virus. [/COLOR][/SIZE]
[/SIZE][B][SIZE=4]
[/SIZE][/B][/COLOR][SIZE=2]please tell me how to use 64 bit in Ubuntu or activate it.[/SIZE]

---

### Post by cascade9 on 2010-01-23
You have to install the 64bit version to run 64bit ubuntu. You cant 'upgrade' or 'activate' it any other way. ;)

---

### Post by bobleny on 2010-01-23
You must also be running a 64bit machine. That means you need at least a dual core possessor.

---

### Post by cascade9 on 2010-01-23
> **bobleny said:**
> You must also be running a 64bit machine. That means you need at least a dual core possessor.

Yes, true, you need a 64bit capable CPU. But nope, its not the same thing as dual core. There are 64bit single core machines, and there are dual cores that are only 32bit......

---

### Post by bobleny on 2010-01-23
I did not know there where 64bit single core machines. Can you give me some names, I'm curious to read up on them. 32bit exclusive dual cores are far and few between though...

---

### Post by DGortze380 on 2010-01-23
> **bobleny said:**
> I did not know there where 64bit single core machines. Can you give me some names, I'm curious to read up on them.

AMD Athlon 64

(not be confused with the Athlon 64 X2)

---

### Post by cascade9 on 2010-01-23
[http://en.wikipedia.org/wiki/List_of_AMD_Athlon_64_microprocessors](http://en.wikipedia.org/wiki/List_of_AMD_Athlon_64_microprocessors)

All the models that are named Athlon 64 xxxx+ are single core. The dual cores are Athlon 64 X2. Also-

[http://en.wikipedia.org/wiki/List_of_Intel_Core_2_microprocessors#Single-Core_Notebook_processors](http://en.wikipedia.org/wiki/List_of_Intel_Core_2_microprocessors#Single-Core_Notebook_processors)

Core 2 Solo is single core, 64bit.

---

### Post by bobleny on 2010-01-23
Yeah, I don't know what I was thinking, certainly they had 64bit processors before that had dual core processors... Shows how much I know...

---

### Post by cascade9 on 2010-01-24
LOL, you would be amazed how often I hear that '64bit is dual core' or 'dual core is 64bit'. Sometimes from people who should know better (including a computer technician who I made $20 out of for that mistake LOL) 

At least you've got the guts to admit you were wrong. ;) Chalk it up to experience :D

---

### Post by efflandt on 2010-01-24
My Athlon64 3200+ is single core 2 GHz (circa 2004).  The only thing it lacks is the lahf_lm instruction used by 64-bit flash, so I had to use the flashplugin-lahf-fix someone here came up with.  Although, Hulu stopped working with 64-bit flash, and Hulu desktop which supposedly still works with 64-bit flash does not pick up on the flashplugin-lahf-fix, so I have switched back to flashplugin-installer.

My work PC from about the same time is Intel 3 GHz I think, with hyper-threading.  Task manager in WinXP shows 2 processors.  But Ubuntu refuses to boot 64-bit on what it says is i686.

I didn't even know that my Intel dual-core laptop from 2006 could do 64-bit until I saw something mentioned on these forums.

What I have not tried 64-bit on is a Sempron 3300+ laptop, which appears to be similar to my older Athlon, but with much smaller cache 128K vs. 1024K.  I got that back (WinXP hopelessly infected with worms/trojans) when I got someone a new laptop.

---

### Post by cascade9 on 2010-01-24
> **efflandt said:**
> My work PC from about the same time is Intel 3 GHz I think, with hyper-threading.  Task manager in WinXP shows 2 processors.  But Ubuntu refuses to boot 64-bit on what it says is i686.

What I have not tried 64-bit on is a Sempron 3300+ laptop, which appears to be similar to my older Athlon, but with much smaller cache 128K vs. 1024K.  I got that back (WinXP hopelessly infected with worms/trojans) when I got someone a new laptop.

The only P4s that were 64bit are the (very) late model Pentium 4 HT 6xx versions. The earlier 5xx and just plain 'HT' versions are 32bit only. 

[http://en.wikipedia.org/wiki/List_of_Intel_Pentium_4_microprocessors](http://en.wikipedia.org/wiki/List_of_Intel_Pentium_4_microprocessors)

As for the Sempron 3300+, its probably 32bit. There is a few 3300+ CPUs that are 64bit but they also have 32bit only models using the same name. Nice move, AMD. :|  The majority of semprons, and all the 3300+ mobile semprons are 32bit only. 

[http://en.wikipedia.org/wiki/List_of_AMD_Sempron_microprocessors](http://en.wikipedia.org/wiki/List_of_AMD_Sempron_microprocessors)

BTW, just to nit-pick, all the commercially avaible athlon models are 256K or 512K. There was an experimental 'mustang' core with 1MB, but it was never released. (unless you count the X2 models, that have 2x512K per core...but they are Athlon 64s anyway)

---

