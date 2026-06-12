---
title: "Erasing a CD-RW using Brasero Disc Burner"
date: 2010-03-06
forum: General Help
---

### Post by craig10x on 2010-03-06
I am using Ubuntu 9.10 and have a CD-RW disc that i want to erase and do a new burn on...but when i go into Brasero, i don't see any option to erase the disc before i burn it...
How do you do it?   I'd prefer a solution that doesn't involve using the terminal...

Thanks :)

---

### Post by howefield on 2010-03-06
Try the Brasero tools menu ?

---

### Post by rnerwein on 2010-03-06
> **craig10x said:**
> I am using Ubuntu 9.10 and have a CD-RW disc that i want to erase and do a new burn on...but when i go into Brasero, i don't see any option to erase the disc before i burn it...
How do you do it?   I'd prefer a solution that doesn't involve using the terminal...

Thanks :)

hi
if it's not possible to do that in brasero in a terminal use:
 dvd+rw-format  or
 dvd+rw-format -force  /dev/dvd

for further information see: man dvd+rw-format
ciao

---

### Post by mcoleman44 on 2010-03-06
After you insert the dvd go to places>computer and right click the dvd and click erase. I think.

---

### Post by craig10x on 2010-03-06
> **howefield said:**
> Try the Brasero tools menu ?

Tools menu just offers: "blank" "eject"  "check intergrity"....no erase listed

---

### Post by craig10x on 2010-03-06
> **mcoleman44 said:**
> After you insert the dvd go to places>computer and right click the dvd and click erase. I think.

right clicking on the dvd after it is shown on desktop does not  offer "erase" as an option...

You mean the Brasero program offers no erase option?  Seems kind of weird....

Has anyone erased a cd-rw on a recent version of Brasero?

---

### Post by howefield on 2010-03-06
> **craig10x said:**
> Tools menu just offers: "blank" "eject"  "check intergrity"....no erase listed

What do you think "blank" might mean ?

I haven't erased a disk with Brasero in a long time, but it of course can do it.

---

### Post by mcoleman44 on 2010-03-06
Blank is what I meant. My bad. And i didnt say desktop, I said computer.

---

### Post by craig10x on 2010-03-06
LOL :)  I wasn't sure what they meant by "blank"....would have been easier to understand if they said "erase"...;)

Thanks for the input...have any of you guys used that before?  If so, is it fairly fast?

---

### Post by howefield on 2010-03-06
> **craig10x said:**
> LOL :)  I wasn't sure what they meant by "blank"....would have been easier to understand if they said "erase"...;)

You gotta think laterally ;)

> Thanks for the input...have any of you guys used that before?  If so, is it fairly fast?

From memory, you won't wait long for a disk to "blank"

---

### Post by efflandt on 2010-03-06
If you run Brasero from Applications > Sound & Video, you have more options than when it comes up from automatic launcher when inserting a disk.

---

### Post by craig10x on 2010-03-07
> **efflandt said:**
> If you run Brasero from Applications > Sound & Video, you have more options than when it comes up from automatic launcher when inserting a disk.

Thanks...although that IS the way i bring up Brasero....Perhaps on earlier versions they called it "erase"...now they call it "blank"....it appears under tools....

I tried it and it worked....i didn't use the fast setting and did take quite a while....i was wondering if i could use the fast setting and still get a clean wipe of the data?

---

