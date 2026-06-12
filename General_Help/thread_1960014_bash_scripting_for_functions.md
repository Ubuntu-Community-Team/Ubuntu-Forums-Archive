---
title: "bash scripting for functions"
date: 2012-04-16
forum: General Help
---

### Post by sd@ksu on 2012-04-16
My problem is simple and I am sure it has a simple solution, I just do not happen to know it. :mad:
I want to write some functions which I want to type in terminal and calculate things whenever i want to. say I want to create two functions:
1) func_1: it will return x^2.
2) func_2: it will return x^3.
I want to write them in a single file, store it somewhere in my directory and whenever I call func_1 $1 or funct_2 $1 from the terminal, I want them to be available in terminal at my service.
I do not want to put them in .bashrc but in a separate file where I can keep on adding functions with my convenience. Is there a way to do it easily ?

---

### Post by papibe on 2012-04-16
Hi sd@ksu.

The best place is ~/bin (that is a personal directory called bin under your home), since when the system starts it is added to the PATH if exists.

I hope that helps. Tell us if you need more help with that.
Regards.

---

### Post by sd@ksu on 2012-06-01
Wonderful..thanks for pointing me out to that direction. Now I realize why we use bin at first place. THanks a ton.

---

### Post by Habitual on 2012-06-01
> **sd@ksu said:**
> ...I want to write them in a single file, store it somewhere in my directory and whenever I call func_1 $1 or funct_2 $1 from the terminal, I want them to be available in terminal at my service.
I do not want to put them in .bashrc...

edit your .bashrc and add "jj" will be ***your*** loginID
```
source /home/jj/.functions
``` then save and exit the editor. Reload bash with 
```
source ~/.bashrc
``` and just insert your functions in the .functions file.

HTH.

---

### Post by sd@ksu on 2012-06-01
@ habitual... I shall try your method too..but what papibe said above is working..and makes perfect sense to me...thank you both..

---

