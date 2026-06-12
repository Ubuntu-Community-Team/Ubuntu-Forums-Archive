---
title: "How to remove a partition in Home folder?"
date: 2012-07-19
forum: General Help
---

### Post by michaelbr on 2012-07-19
Greetings all:
I just installed Ubuntu 12.04 in dual boot with XP SP3, I'm afraid I messed up with mounting ntfs partition. This is what I did:
- mounted ntfs Data partition under /mnt/Windows (changed fstab and everything was fine), then realized that there's a /media folder with C drive already mounted, so I changed my mounting entry in fstab to /media/Data instead, but now I have 2 icons showing Data in my Home folder, under Device. The 1st one is the Data partition I wanted to mount at start up (this one has a triangle and a bar underneath it), and the 2nd one just showed Data, when I click it, it gave me an error: 
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.

How can I remove the 2nd icon from the Device on the left side of my Home folder?

Thanks for your comment/suggestion,
Michael

---

