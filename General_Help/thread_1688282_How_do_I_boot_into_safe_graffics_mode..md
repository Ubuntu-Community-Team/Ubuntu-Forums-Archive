---
title: "How do I boot into safe graffics mode."
date: 2011-02-15
forum: General Help
---

### Post by schwabdale on 2011-02-15
I installed 10.04 and want to do this. Is there a hot key? Also, Fyi, Im dual booting with windows

---

### Post by Kirboosy on 2011-02-15
Press the 'e' key on the kernel you want when your GRUB appears

Add the option ```
-***xforcevesa***
```****
Let me know if that fixes it

---

### Post by schwabdale on 2011-02-15
How do I add the option...I can type after I hit control x..
It comes up with a "Grub" then I type -xforcevesa and it says no such command
Please give me a step by step
> **Caboose885 said:**
> Press the 'e' key on the kernel you want when your GRUB appears

Add the option ```
-***xforcevesa***
```
Let me know if that fixes it

---

### Post by Kirboosy on 2011-02-15
It appears to have worked for me...

Simply hit 'e' on the kernel you use.

add ```

-***xforcevesa***
```to the end of the  bottom line. Should look something like ```
initrd /boot/initrd.img-2.6.35-25-generic -xforcevesa
```Then press control + x to boot

If that doesn't work substitute the command to this one
 ```
initrd /boot/initrd.img-2.6.35-25-generic nomodeset
```

---

### Post by schwabdale on 2011-02-15
It worked!

Thanks

---

