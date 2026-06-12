---
title: "Weird Disc Defect Problem"
date: 2010-09-05
forum: General Help
---

### Post by saadli on 2010-09-05
Hello,

I downloaded Ubuntu 10.4.1 LiveCD and wrote it on a DVD. I tested the downloaded ISO and the DVD manually through MD5SUM and they both passed. On my laptop (Dell Inspiron 1545), in the boot menu (at the start), when I do check disc for defects, no error is found. But interestingly, when I check for defects on one of our desktop machine, we get "error found in 1 file". 

Turns out that in our lab (I am in charge of a educational institute where we have bunch of machines), on all machines with Core 2 Duo (some with Intel Motherboard and some with Gigabyte Motherboard), "check for disc defects" gives error found in 1 file. The installation also fails.

But all older machines (with P4), check disc for defects shows no error. Even my laptop it is good.

Now, check disc for defects should just check the disc content right? If so, this is quite weird no? How is hardware profile making a difference? We changed the DVD-ROM drive and the same issue exists. 

Any help?

---

### Post by Cypress421 on 2010-09-05
Did you download the .iso via ethernet or wireless? If it was wireless, try the ethernet option. I'd also burn the .iso at 8x, and verify it with the application you use to burn the disc. I doubt different hardware should cause issues.

---

### Post by saadli on 2010-09-05
Got it. It was the DVD-ROM. 

Yes I did changed the DVD-ROM first time and it didn't work. Next I tried one of the IDE older DVD-ROM and it worked. 

By the way, I had two DVD burned, one maxed speed one on 2x. Both were giving problem before. 

Anyways, thanks for the help!

---

