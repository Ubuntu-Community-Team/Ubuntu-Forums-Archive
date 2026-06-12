---
title: "Error: No such partition(grub rescue)"
date: 2011-12-16
forum: General Help
---

### Post by drag00nslayer on 2011-12-16
When starting up my computer i went down to Windows 7
And i may have selected windows 7 recovery console (just woke up and precoffee)

When i noticed it was recovery i saw a cmd prompt popup and saying something to the extent "changing partition 0 to partition 1"

I exited recovery since i didn't need to recover

now when starting I see

error: no such partition.
grub rescue>

I tried using the cmd prompt on the recovery cd (but all the guides say bootsec.exe)
and i don't have that program in the boot folder


Any ideas on how to fix?

Currently downloading a ubuntu live cd (since i heard that can fix MBR errors)

Any other idea's incase that doesn't work?

**Solved**

Used this link to create a [bootable recovery disk (USB)]("http://neosmart.net/forums/showthread.php?t=7805")


And the post by "[talsemgeest]("http://ubuntuforums.org/member.php?u=397508")"


 >     bootrec.exe /fixboot 
     bootrec.exe /fixmbr 

Works perfectly thanks for the help :)

---

### Post by Rubi1200 on 2011-12-16
Hi and welcome to the forums :-)

We're glad you managed to find a solution and get things back to normal.

Please help the community by marking this Solved using the Thread Tools near the top of the page.

---

