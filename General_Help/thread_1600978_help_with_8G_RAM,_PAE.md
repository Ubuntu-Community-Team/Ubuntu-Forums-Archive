---
title: "help with 8G RAM, PAE?"
date: 2010-10-19
forum: General Help
---

### Post by athenaa on 2010-10-19
Hi everyone, 

I have a linux machine that is supposed to have 8 G memory, but I can only see 4 G.

some one told me :

"You can try change the kernel to a PAE version -  e.g., use synaptic to find a linux-image that ends with PAE."

but I don't know what it means and what I should do.

thanks,
Athena

---

### Post by PentaxFollower on 2010-10-19
[https://help.ubuntu.com/community/EnablingPAE]("https://help.ubuntu.com/community/EnablingPAE")

---

### Post by TBABill on 2010-10-19
Do you have the ability to reinstall the OS with 64 bit? PAE will recognize the memory but I did notice a slight improvement in overall performance with 64 bit. I have 4GB RAM and it made a difference so I would imagine if you  have 8GB RAM you also have a modern CPU?

---

### Post by athenaa on 2010-10-26
Thank,

As I found out, PAE is when you have a 32 bit OS. (Am I wrong?)

but I have a 64 bit OS. I've installed it myself.

---

### Post by efflandt on 2010-10-26
What does **free** in a terminal tell you?  This is an example of an 8 GB system in 64-bit Maverick (ignore the unused swap, this is booted from a USB drive and that is just in case it is needed for another PC):

**free**
```
             total       used       free     shared    buffers     cached
Mem:       8121512    1023752    7097760          0     112120     310256
-/+ buffers/cache:     601376    7520136
Swap:      2152704          0    2152704
```

---

### Post by dcstar on 2010-10-27
> **athenaa said:**
> Hi everyone, 

I have a linux machine that is supposed to have 8 G memory, but I can only see 4 G.
.........

Are you **100% sure** that the MB supports more the 4GB of RAM?

---

### Post by athenaa on 2010-10-28
Hi guys,

Thanks for the response, 
turns out it had only 4G on the machine. I ordered 8G, so I was pretty sure it's a OS problem, but I check bios and it just showed 4 G. I need to contact customer service.

Thanks for all the help again :)

---

