---
title: "Resize partition using gparted"
date: 2009-08-29
forum: General Help
---

### Post by hardyfan on 2009-08-29
I have a dual boot setup (vista / jaunty).  I have just reduced the size of my swap partition leaving 10 gig unallocated.  When I boot off the live CD and try to resize my Ext3 partition, the maximum size on offer doesn't use the unallocated space ?  Does anyone have a suggestion ?

Thanks.

---

### Post by Elfy on 2009-08-29
Is the unallocated space next to the ext3 partition ? If it isn't then it needs to be.

---

### Post by oboedad55 on 2009-08-29
> **hardyfan said:**
> I have a dual boot setup (vista / jaunty).  I have just reduced the size of my swap partition leaving 10 gig unallocated.  When I boot off the live CD and try to resize my Ext3 partition, the maximum size on offer doesn't use the unallocated space ?  Does anyone have a suggestion ?

Thanks.

Can you upload a printscreen of GParted so we can see what you're talking about?

--Jon

---

### Post by hardyfan on 2009-08-29
The unallocated space is not next to the partition I want to increase see attached.

How can I relocate the space to have them together ?

---

### Post by Elfy on 2009-08-29
The easiest way would be to delete swap and the extended partition. Do the resize and then create a new swap. You will need to change the swap references in your install but that's not hard.

Alternatively you have to move the extended to the other side of the unallocated and then do the resize.

---

### Post by hardyfan on 2009-08-29
**[FONT="Arial Black"]Solved[/FONT]**

Thank you for your help, I'll keep learning so I can oneday repay in kind.

Love these forums, keep up the good work.

---

