---
title: "Lost my admin rights"
date: 2011-12-31
forum: General Help
---

### Post by Mickers on 2011-12-31
Im a noob, and was creating another profile to see if i could do something. I made my current account a standard account at the same time, so i have 2 accounts which are both just standard account. When i try to switch my account back to an admin account, it says i need a password for root? Im running 11.10.

---

### Post by amauk on 2011-12-31
boot into the recovery mode (you may have to press and hold the shift key during bootup to get the grub menu)

Boot to a "root shell"
at the prompt, type
(replace <username> with the user you want to have access to sudo)
```
usermod -a -G admin <username>
```

then type "reboot" to reboot, and login normally

---

### Post by 0rthos on 2012-02-11
> **amauk said:**
> boot into the recovery mode (you may have to press and hold the shift key during bootup to get the grub menu)

Boot to a "root shell"
at the prompt, type
(replace <username> with the user you want to have access to sudo)
```
usermod -a -G admin <username>
```then type "reboot" to reboot, and login normally
i did this and it came back saying 
```
usermod: cannot lock /ect/passwd; try again later.
```so what do i do from there?

---

### Post by amauk on 2012-02-12
> **0rthos said:**
> i did this and it came back saying 
```
usermod: cannot lock /ect/passwd; try again later.
```so what do i do from there?
You are not root
You cannot do this as an unprivileged user

Assuming your issue is the same as the OP (which you don't say), then you need to boot into single user mode (AKA recovery mode), as per my first post

---

### Post by 0rthos on 2012-02-12
sorry for not clarifying i have the same problem i lost my admin privileges when messing around the only difference is i only have one user account instead of two 
so i restarted the computer with the ubuntu disk inside i did not boot form the disc i went to recovery mode and there came a menu i used the one that said root shell then i did the command was this correct?

---

