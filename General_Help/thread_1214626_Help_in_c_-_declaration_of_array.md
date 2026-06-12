---
title: "Help in c - declaration of array"
date: 2009-07-16
forum: General Help
---

### Post by madhavhmk on 2009-07-16
I am trying to declare the following two dimensional array :

VLSS[1810672][4]

But, During run time, its showing segmentation fault......

I am exceeding the available memory for allocating 1810672*4 units I guess...What do I do...? 

Someone help me out PLease..!!!


I can declare upto VLSS[1810672]....the program works till here { well...sort of...I need VLSS[1810672][4] for it work completely....but the array declaration part is ok till VLSS[1810672]  }

when I give VLSS[1810672][2] for declaration, the program seems to have hit a 'segmentation fault'.....********

---

### Post by t4thfavor on 2009-07-16
What type is the array, it should be something like 

long VLSS[1810672][4]

But you should probably name "VLSS" "lngThisIsWhatImUsedFor[######][#]; so that you will remember what it was for 6 months from now. 

Just a thought.

---

