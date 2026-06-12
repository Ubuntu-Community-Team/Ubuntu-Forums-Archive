---
title: "Add Programs Window won't stay open."
date: 2010-01-21
forum: General Help
---

### Post by Attex on 2010-01-21
Why is it that the Add Remove Program Window won't stay open in 9.10?  I added a few Video Programs.  It was working fine,but now I can't remove any Programs. The Window will open for a few seconds, but then closes. :confused:

---

### Post by jamesisin on 2010-01-21
Have you tried just using Synaptic?

---

### Post by Attex on 2010-01-21
> **jamesisin said:**
> Have you tried just using Synaptic?



I'm new to Ubuntu. What's Synaptic?

---

### Post by kako13 on 2010-01-21
> **Attex said:**
> Why is it that the Add Remove Program Window won't stay open in 9.10?  I added a few Video Programs.  It was working fine,but now I can't remove any Programs. The Window will open for a few seconds, but then closes. :confused:
Hi,

This seems to be related [https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/477804](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/477804)

---

### Post by kako13 on 2010-01-21
> **Attex said:**
> I'm new to Ubuntu. What's Synaptic?


Is  an utility to manage (Install & Remove) software in Ubuntu.

Go to System>Administration>Synaptic Package Manager.

---

### Post by jamesisin on 2010-01-21
Add/Remove Programs was created as a sort of stripped down, more user friendly way to install and remove software.  You can see everything that's available to your system through Synaptic (kako13 gave instructions for opening it above).  It's much more comprehensive, but it may be slightly more intimidating as well (read: too much information).

You will likely also want to take a look at the bug report (link above also by kako13) to see if that is your exact issue.

---

### Post by Attex on 2010-01-21
> **kako13 said:**
> Is  an utility to manage (Install & Remove) software in Ubuntu.

Go to System>Administration>Synaptic Package Manager.


I did do that, but I was looking for a way to resolve the problem with the window in the Add Remove Programs from closing after a few seconds. Is this a known problem? 

Thanks

---

### Post by Attex on 2010-01-21
> **kako13 said:**
> Hi,

This seems to be related [https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/477804](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/477804)


Yeah, this is the same problem I'm having.  Their is one response, but it's all code. :confused:

---

### Post by kako13 on 2010-01-21
> **Attex said:**
> Yeah, this is the same problem I'm having.  Their is one response, but it's all code. :confused:

Did you also installed Ubuntu Tweak?

---

### Post by Attex on 2010-01-21
> **kako13 said:**
> Did you also installed Ubuntu Tweak?


No. Will that program fix the problem, or just bypass this existing problem?  

Thanks

---

### Post by rogue_0111 on 2010-01-21
Since it's a new install.

Have you done updates yet? It may have been fixed already.

---

### Post by Attex on 2010-01-21
> **rogue_0111 said:**
> Since it's a new install.

Have you done updates yet? It may have been fixed already.


Yep, did the updates, but it didn't fix the problem.

---

### Post by jamesisin on 2010-01-21
You were asked about Ubuntu Tweak because it's listed in the bug report.  You may want to take a closer look at that bug report.

---

### Post by Attex on 2010-01-21
> **jamesisin said:**
> You were asked about Ubuntu Tweak because it's listed in the bug report.  You may want to take a closer look at that bug report.


I didn't install Tweak, but still have the same problem.

---

### Post by kako13 on 2010-01-21
You might try ```
 software-center 
``` on Terminal too see if that bring any error when the software-center close automatically.

Applications > Accessories > Terminal.

---

### Post by rogue_0111 on 2010-01-23
> **Attex said:**
> Why is it that the Add Remove Program Window won't stay open in 9.10?  I added a few Video Programs.  It was working fine,but now I can't remove any Programs. The Window will open for a few seconds, but then closes. :confused:

Fresh install or upgrade?

---

