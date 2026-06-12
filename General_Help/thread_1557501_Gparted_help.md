---
title: "Gparted help"
date: 2010-08-20
forum: General Help
---

### Post by ubudog on 2010-08-20
Hi, take a look at the screenshot.  I want to resize /dev/sda1 using the unallocated space, but when I try, it doesn't let me.  Look at the resize screenshot to see what I mean.  Thanks for the help.

---

### Post by Quackers on 2010-08-20
I'm pretty sure that the partition you want to extend and the unallocated space you want to grab need to be next to each other.

---

### Post by ubudog on 2010-08-20
How would I do that?

---

### Post by Quackers on 2010-08-20
I would think you would need to move /dev/sda3 to the right, up to the end of the unallocated space (with move/resize in GParted) then you could do it. It shouldn't take too long for such a small partition. Can you back up any data first?

---

### Post by ubudog on 2010-08-21
Yeah, already got it all backed up.  I will try that later, thanks.

---

### Post by Quackers on 2010-08-21
No, problem. Good luck :-)

---

### Post by ubudog on 2010-08-21
Awesome!  It worked!  Thank you! :p:p:p:p:p

---

### Post by Quackers on 2010-08-21
Very nice :-)

---

