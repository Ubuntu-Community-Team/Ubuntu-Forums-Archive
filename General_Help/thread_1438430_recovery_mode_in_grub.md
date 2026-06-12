---
title: "recovery mode in grub"
date: 2010-03-25
forum: General Help
---

### Post by utsav.jain on 2010-03-25
I just tried ubuntu 9.10 in recovery mode 
i came to know that i can change root passwd without knowing the password
then i can change password of every user by logging in as root 

i want to ask is there any solution to this problem 
i mean it is a flaw in ubuntu

---

### Post by bodhi.zazen on 2010-03-25
> **utsav.jain said:**
> I just tried ubuntu 9.10 in recovery mode 
i came to know that i can change root passwd without knowing the password
then i can change password of every user by logging in as root 

i want to ask is there any solution to this problem 
i mean it is a flaw in ubuntu

The only solution is to restrict physical access. This applies to ALL operating systems.

The next best option is to perform an installation with encryption.

Some people suggest things such as setting a BIOS password and/or a grub password, but those are easily defeated, although they will slow down casual intruders.

Some people also suggest setting a root password. When you do that you would need to enter a password when booting to recovery mode.

The only problem with that, you are still vulnerable to the same thing via a live CD.

---

### Post by utsav.jain on 2010-03-25
thank you for your input 
but since i am newbie to linux can you tell me how to apply passwd to enter in recovery mode
it may help me
i have used fedora earlier in my college they locked all the way to change root passwd without knowing root passwd isn't there any way to that in ubuntu also
thank you for your help again

---

