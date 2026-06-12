---
title: "Odd error message after GRUB"
date: 2012-08-12
forum: General Help
---

### Post by TXbirder on 2012-08-12
I have two hard drives in my PC- one with Win7 and one Ubuntu 12.04.   I just cloned the Win7 drive onto a larger-capacity one and swapped them.   I disconnected the Ubuntu drive while doing this so I wouldn't accidentally screw it up.  

When I first restarted the PC, GRUB worked fine and Ubuntu opened OK.   I restarted and selected Win7 to start.  After I selected Win7 the purple screen stayed on for about 10 seconds and then at the top popped up :   error:  no such device: 6250DB7450DB4D83.     press any key to continue...

(See attachment)

I pressed a key and Win7 started. 
 Both Win7 and Ubuntu seem to work fine.  What is this error message that GRUB displays?

I Googled 6250DB7450DB4D83 and got no hits.


John

---

### Post by oldfred on 2012-08-12
How did you copy to new drive? The long number was probably the UUID of the old Windows partition and it now is a new UUID.

Run this:

sudo update-grub

That should reset the grub menu entry.

---

### Post by TXbirder on 2012-08-12
That did it.  Thanks.
John

---

