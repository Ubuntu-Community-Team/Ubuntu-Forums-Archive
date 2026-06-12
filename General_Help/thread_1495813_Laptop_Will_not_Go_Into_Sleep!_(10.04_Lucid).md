---
title: "Laptop Will not Go Into Sleep! (10.04 Lucid)"
date: 2010-05-28
forum: General Help
---

### Post by Johnnyftw on 2010-05-28
Hi, I've noticed my laptop will not sleep and In Powertop, it's showing a VERY high wake ups from idle, I could use some help. I've also noticed my fan is always on. It never shut's off. It's not a heating problem cause it runs fine with Windows 7.

My laptop is a Lenovo G530.

---

### Post by MichealH on 2010-05-28
Yeah mine sleeps but never starts up again it just keeps on going through an evil bootup loop.

HELP!

---

### Post by mike555 on 2010-05-28
Do you have a big enough swap file (bigger that your RAM ) . for the fan you might try "thinkfan".

---

### Post by Johnnyftw on 2010-05-28
> **mike555 said:**
> Do you have a big enough swap file (bigger that your RAM ) . for the fan you might try "thinkfan".

Hi, I'm using a Wubi Install. Not a clean install.

---

### Post by mike555 on 2010-05-28
Not sure a wubi install is much different , you still need swap file ......

---

### Post by Johnnyftw on 2010-05-28
> **mike555 said:**
> Not sure a wubi install is much different , you still need swap file ......

Well How do i figure out the swap file? and what would that have to do with my computer never sleeping and powertop having a high wake up from idle count? it's suppose to be in the hundreds.

---

### Post by mike555 on 2010-05-28
To see how much swap is being used you can click on System > Administration > System monitor .. it will display CPU usage and swap usage (and tell you swap size)

---

### Post by amadeijohn on 2010-05-28
> **mike555 said:**
> To see how much swap is being used you can click on System > Administration > System monitor .. it will display CPU usage and swap usage (and tell you swap size)

Hi, I've attached a picture.. Not sure what exactly is causing all of this..

---

### Post by mike555 on 2010-05-29
looks like your swap file is too small, a rule of thumb is at least as big as your RAM , so your computer can sleep by putting what's in your RAM into swap ...

---

### Post by Johnnyftw on 2010-05-29
> **mike555 said:**
> looks like your swap file is too small, a rule of thumb is at least as big as your RAM , so your computer can sleep by putting what's in your RAM into swap ...

Ok, I updated to a newer stable kernel, 2.6.34 from Kernel.org and I noticed it's now in the 700-1,000's (Wake ups from idle) and my brightness fkeys work now.

---

### Post by vinaysetty on 2010-07-05
I have the same problem too, I am using HP dv6000 and I have 3GB RAM and 3.8GB swap partition. Suspend and hibernate options were working like a charm on my laptop until the recent update of kernel to 2.6.32-23-generic. Any ideas? I am tired of hard resetting my laptop and my laptop heats of up big time, when I leave it....

---

