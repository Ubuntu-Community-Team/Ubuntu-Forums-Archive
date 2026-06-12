---
title: "Ubuntu Freezes with no reason"
date: 2010-12-15
forum: General Help
---

### Post by Masclins on 2010-12-15
I just installed Ubuntu 10.10 and I've got a problem: With no reason my computer **completely freezes**, the mouse won't work, the keybord neither (I've tried to ctrl+alt+F1 and it doesen't respond).

I have no idea what it could be, since in the /var/log/messages there's nothing ever on the time it happens.

This problem happens when the computer is doing something that requires some CPU (I think) but i've tried limiting the CPU usage per process and still freezes.

Thanks.

---

### Post by RandomQuestions on 2010-12-15
> **Masclins said:**
> I just installed Ubuntu 10.10 and I've got a problem: With no reason my computer **completely freezes**, the mouse won't work, the keybord neither (I've tried to ctrl+alt+F1 and it doesen't respond).

I have no idea what it could be, since in the /var/log/messages there's nothing ever on the time it happens.

This problem happens when the computer is doing something that requires some CPU (I think) but i've tried limiting the CPU usage per process and still freezes.

Thanks.

Maybe it is overheating? does this problem occur in Windows as well?

---

### Post by Masclins on 2010-12-15
I was using Windows XP before that and I never had this problem.
Anyway, how can I check wether it's due to overheating or not and how could I solve it if that's the case?


EDIT:  It just happened again and the computer itself was for sure not too hot.

Also, whenever I try to extract a 1.1GB .tar.gz it crashes, (also it'd crashed when doing some different stuff)

---

### Post by piquat on 2010-12-15
Why am I reading more and more about this lately?

Do you have nVidia graphics by chance?

---

### Post by Masclins on 2010-12-15
Yes, I use a nVidia Geforce 6100 nForce 405

---

### Post by Stainesy on 2010-12-15
I developed the same problem in both Ubuntu 10.10 and LinuxMint 10 using the default Nouveau graphics driver to run my Nvidia GeForce GT240 graphics card but now that I've installed and run a proprietory Nvidia driver and purged Nouveau all is well.  I also noticed that my monitor resolution wasn't recognised automatically by KMS (Kernel Mode Setting) as is supposed to happen and after considerable research I learned that this is a common problem but the Nvidia driver has negated that problem.  No more freezes.

---

