---
title: "xp/7/ubuntu mixed up"
date: 2009-11-28
forum: General Help
---

### Post by wirate on 2009-11-28
xp used to be the only OS on my system (so it was on drive 0,0 I don know) then I put in Windows 7 which managed to keep xp in its place and make a dual boot. Then I installed ubuntu on the xp partition (the primary partition?) and now my system boots straight into ubuntu. what can I do to dual boot ubuntu with 7? (its there on a seperate partition but i guess the bootloader is gone)

---

### Post by carl.davis on 2009-11-28
You can change the default boot options of grub and cause Windows 7 or XP to boot by default.

---

### Post by wirate on 2009-11-28
how?

---

### Post by carl.davis on 2009-11-28
Open a terminal window and type:

```
gksudo gedit /boot/grub/menu.lst
```

Enter your password and then change the line that says "default         0" to be the list number of whatever you are wanting to boot first (the list is located at the end of the file). The numbering of course starts at 0, so the second one listed is actually 1. 

If you need more help paste the list below "## ## End Default Options ##".

---

### Post by wirate on 2009-11-30
bump. I aint clear

---

### Post by louieb on 2009-11-30
> **waqar said:**
> then I put in Windows 7 which managed to keep xp in its place and make a dual boot. 
The Windows default way of setting up dual boot with another MS OS - only one install has a boot loader.  Tech stuff: [Multibooters]("http://www.multibooters.co.uk/multiboot.html")
> Then I installed Ubuntu on the xp partition

If the Windows boot loader was in the XP install -  GRUB will not be able to boot Win 7. -  GRUB chainloads the windows boot loader. GRUB cannot directly boot windows.

To know for sure follow the [Boot Info Script: How to]("http://ubuntuforums.org/showthread.php?t=1291280") and put the results.txt file in your next post.

---

### Post by wirate on 2009-11-30
Thanks for the follow-up. I was too eager. I ran Windows fixmbr which restored Windows 7 and re-installed Ubuntu and win7 was automatically detected :D

---

