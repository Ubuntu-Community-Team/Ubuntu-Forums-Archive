---
title: "Does the CONFIG_NR_CPUS for Ubuntu 11.10 only have 8?"
date: 2012-05-30
forum: General Help
---

### Post by dkzhaos on 2012-05-30
Hi,
 
I use grep CONFIG_NR_CPUS /boot/config-`uname-r`,and got CONFIG_NR_CPUS = 8. Does this mean my Ubuntu kernel only support 8 cpus? I think that is too little. Is there any way to change this number? Thanks for any replies!

---

### Post by Cheesemill on 2012-05-30
Are you using 32-bit or 64-bit?

I'm using 64-bit and I get a result of 256.

---

### Post by dkzhaos on 2012-05-30
> **Cheesemill said:**
> Are you using 32-bit or 64-bit?
 
I'm using 64-bit and I get a result of 256.
 
Thanks for your reply! I'm using 32-bit version of Ubuntu 11.10. The cpu I'm using is 6-core Xeon , but I can only use 4 cores. Many people said that is because of the 32-bit OS. Now, I'm thinking that is because of the 32-bit Ubuntu!

---

### Post by Cheesemill on 2012-05-30
You could either switch to 64-bit, re-compile your current kernel having changed the option, or try and find a pre-compiled custom kernel that already has the options you need.

Although why you are running 32-bit on a machine with a 6 core Xeon is beyond me :) How much RAM do you have?

---

