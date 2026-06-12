---
title: "nfs and general file transfer issues..."
date: 2009-09-20
forum: General Help
---

### Post by kforum on 2009-09-20
i dont know when this started, and i dont even know if anyone in the ubuntu forums will have anything knowledgeable to say but...

first symptom:
i got nfs installed, everything setup - the exports -the host.allows -everything; it mounts just fine, but when transferring from my pc to the other it starts with speed A, lets say 30mbs and then it gets slower, and slower, and slower... maybe its something i havent gotten right?

i thought that was the case, but today i tested some large usb transfers(from the pc to the usb, 2.0 btw). And guess what? got the same situation, it starts with 10mbs and the it gets slower and slower, eventually doing 3mbs.
its funny because on the other pc in the house(2.0 too) it does an average of 5-6mbs and stays there the whole transfer.

this is really weird, and i wouldn't be surprised if it was ubuntu specific, BUT it can't hurt to ask.

maybe ill get some actual ubuntu support this time.

thanks for any input, 

cheers

---

### Post by fragos on 2009-09-20
This may in part relate to filling the buffers. Once filled the apparent transfer rate would be at device speed. When you do a large update from the repositories over the net you will notice the initial speed is faster and may drop as it proceeds. In this case there are more factors since you're sharing the network and speed can increase again based on the number of users.

---

### Post by kforum on 2009-09-20
> **fragos said:**
> This may in part relate to filling the buffers. Once filled the apparent transfer rate would be at device speed. When you do a large update from the repositories over the net you will notice the initial speed is faster and may drop as it proceeds. In this case there are more factors since you're sharing the network and speed can increase again based on the number of users.

this doesnt really help em solve the issue.
and i dont really get that speed drops 'when doing a large update'...
:( nor on any download for that matter.

i still believe its something filesystem related or whatnot.

---

### Post by kforum on 2009-09-21
bumps...

---

