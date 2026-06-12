---
title: "Memtest on Booting"
date: 2009-06-30
forum: General Help
---

### Post by 7raTEYdCql on 2009-06-30
Whenever i boot my ubuntu, i get memtest. i had commented a few lines in menu.lst the last time ubuntu was working fine. Is there any way i can recover my ubuntu without a clean format.

This is urgent. i am downloading a 9.04 iso, apart from that is there a way to manually boot ubuntu using the grub prompt.

---

### Post by colau on 2009-06-30
> **i.mehrzad said:**
> Whenever i boot my ubuntu, i get memtest. i had commented a few lines in menu.lst the last time ubuntu was working fine. Is there any way i can recover my ubuntu without a clean format.

This is urgent. i am downloading a 9.04 iso, apart from that is there a way to manually boot ubuntu using the grub prompt.
Can you post 
```

cat /boot/grub/menu.lst

```

---

### Post by 7raTEYdCql on 2009-06-30
My linux partition is not booting.Is there anyway i can get a screenshot of my boot screen, which is grub. In short, How do i post the inofrmation.

---

### Post by TeoBigusGeekus on 2009-06-30
Boot up with a live cd, find the file (menu.lst) and post us its content.

---

### Post by 7raTEYdCql on 2009-06-30
I am downloading a live cd, this might take some time.

---

### Post by mcduck on 2009-06-30
Do you have any other options than memtest in the Grub menu? (if the menu doesn't show when you start the computer you should get a message telling you to press Esc to show the menu..)

---

### Post by kmg90 on 2009-06-30
> **i.mehrzad said:**
> I am downloading a live cd, this might take some time.

How did you get ubuntu on the computer in the first place?

---

### Post by 7raTEYdCql on 2009-06-30
Everything is sorted out. I undid my menu.lst changes, and the system is working fine, with no lost data. Thanks, everyone.

---

