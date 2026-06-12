---
title: "update nightmare!"
date: 2010-05-11
forum: General Help
---

### Post by _deedeedarlene on 2010-05-11
i just installed ubuntu 10.04 last week, and i ran some updates today.

now, i can't boot into my desktop. it boots into a GRUB terminal, and i have no idea what to do from here. 

i've tried reinstalling GRUB through my ubuntu 9.04 live cd (the only cd i have.) and that didn't fix the problem.

does anyone have any advice? this is freaking me out.

---

### Post by psavva on 2010-05-11
> **_deedeedarlene said:**
> i just installed ubuntu 10.04 last week, and i ran some updates today.

now, i can't boot into my desktop. it boots into a GRUB terminal, and i have no idea what to do from here. 

i've tried reinstalling GRUB through my ubuntu 9.04 live cd (the only cd i have.) and that didn't fix the problem.

does anyone have any advice? this is freaking me out.

Have a look on how to reinstall Grub 2 Here.

[Grub2 re-installation]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

---

### Post by _deedeedarlene on 2010-05-11
all of these methods require an _ubuntu 9.10_ cd, or later.

as i've already mentioned, i only have an **ubuntu 9.04** cd. 

does anyone have a method to doing this that i can use with my **ubuntu 9.04** cd?

---

### Post by stoneage on 2010-05-11
There may be a more elegant method, but if you can get online surely you can update and upgrade. I don't know if this will upgrade grub, but if not you could try downloading from somewhere like [http://packages.ubuntu.com](http://packages.ubuntu.com) and install from your HDD. 

It may not fix your boot problem however...

---

### Post by _deedeedarlene on 2010-05-11
thanks for your help. =]]

i'm currently on my desktop, googling ways to resolve this issue, but i finally bit the bullet, and am currently downloading the iso for ubuntu 10.04. 

i remember reading that lucid lynx had some bugs with GRUB prior to being released. i wonder if this may have something to do with it. 

once i get my cd made, i'll report back! i hope this works.

---

### Post by Don1500 on 2010-05-11
> **_deedeedarlene said:**
> all of these methods require an _ubuntu 9.10_ cd, or later.

as i've already mentioned, i only have an **ubuntu 9.04** cd. 

does anyone have a method to doing this that i can use with my **ubuntu 9.04** cd?

Have you tried downloading a 10.04 CD? Or you can Download the SuperGrub2 CD, but to load grub2 you need grub2. I guess you could try to boot with Grub, but why bother? Grub2 IS better once you get used to it.

---

### Post by solwic on 2010-05-11
> **_deedeedarlene said:**
> thanks for your help. =]]

i'm currently on my desktop, googling ways to resolve this issue, but i finally bit the bullet, and am currently downloading the iso for ubuntu 10.04. 

i remember reading that lucid lynx had some bugs with GRUB prior to being released. i wonder if this may have something to do with it. 

once i get my cd made, i'll report back! i hope this works.

As long as your computer is relatively new, you're going to be blown away with 10.04.  It's super fast.  

Good luck.  ;)

---

### Post by _deedeedarlene on 2010-05-11
these are some of the errors i've been getting from GRUB:

```
Error 23: Error while parsing number

Error 8: Kernel must be loaded before booting
```

---

### Post by stoneage on 2010-05-11
Here you go:-
[http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html](http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html)

Maybe Grub can't see your kernel?

Did you sudo update grub after installing?

---

