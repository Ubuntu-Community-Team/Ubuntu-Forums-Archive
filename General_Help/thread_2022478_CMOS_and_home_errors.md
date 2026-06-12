---
title: "CMOS and /home errors"
date: 2012-07-11
forum: General Help
---

### Post by satya ub on 2012-07-11
Hi,
   The first time i boot up my PC i have to press the start button in combination with the Reset button 5-6 times then my PC boots up. 

Then it tells me its a CMOS error. I read that happens if the CMOS battery is an old one.

But since two days the see this error while Ubuntu is booting up: 
"errors found while checking disk drive for home
Press F to fix it, I to ignore, S to skip, M to manually fix"

I have read couple of threads here and on other sites but i dont understand a word of why i have two issues at the same time.

I would like to give couple of screenshots. It may help you in understanding my issues.

After i installed a clean 12.04 OS i am facing this issues.

---

### Post by MG&amp;TL on 2012-07-11
Well, they're almost certainly separate issues.

About the BIOS battery: if you read that it is an issue with old batteries, then I would get a new battery. I recall them being quite cheap...

About the /home partition:

That error usually (in my limited experience) means the disk/partition is failing. **Backup your stuff**, and then investigate further. You could try viewing the SMART data on the disk, or running a disk check from the "Disk Utility" program.

---

### Post by satya ub on 2012-07-11
I don't know my PC won't boot. Add to that my Home directory is encrypted. There are not many Linux geeks to help :(
So much precious data at stake. My HDD is 4yrs old. 
Thanks for your words. Will update if anything comes up.

---

