---
title: "Can't boot from CD / USB"
date: 2011-12-04
forum: General Help
---

### Post by timozattol on 2011-12-04
Hello =)

I installed Ubuntu 10.10 on a laptop and it worked fine. I used a USB stick. 

But now i'm trying to intall it on my desktop (same USB stick), and after the screen with "Ubuntu" and the dots, I have a black screen with the mouse pointer, and sometimes green lines for a very small amount of time. 

I tried with a CD (same iso), same problem.

Config : Intel i7 2600 with a GT 520

Do you thing I might install 10.04 first ? I don't know if it will work, I didn't try. 

(I'm not really experienced in Linux, so consider you're explaining to a begginer)

Thanks a lot 

Tim

---

### Post by timozattol on 2011-12-04
OH sh*t it's a 32 bit version ! =( I'm trying with the 64 bit now, hope it'll work

---

### Post by cholericfun on 2011-12-04
The 32bit install should work fine on a 64 bit computer. Sounds more like a grafics problem.

---

### Post by 2F4U on 2011-12-04
For nVidia cards, you could try to add nomodeset to the grub kernel boot parameters and see if that helps. It certainly has nothing to do with 32 bit since 32 bit works on 64 bit hardware.

---

### Post by timozattol on 2011-12-04
The 64 bit version worked fine =)

Idk where the problem was, but anyway it works. Thanks a lot =) 

I really like Ubuntu community :)

---

