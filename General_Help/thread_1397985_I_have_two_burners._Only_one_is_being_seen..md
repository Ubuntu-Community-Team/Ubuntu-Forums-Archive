---
title: "I have two burners. Only one is being seen."
date: 2010-02-03
forum: General Help
---

### Post by Carlo1973 on 2010-02-03
Hi there. Have a weird issue. Only one out of the two burns I have on my system is being seen.  The primary is being seen fine, but the secondary isn't. Both are IDE. They are visable in the bios just fine. 

How would I go about getting Ubuntu to see the other drive?

thanks

Carlo

---

### Post by Carlo1973 on 2010-07-21
> **Carlo1973 said:**
> Hi there. Have a weird issue. Only one out of the two burns I have on my system is being seen.  The primary is being seen fine, but the secondary isn't. Both are IDE. They are visable in the bios just fine. 

How would I go about getting Ubuntu to see the other drive?

thanks

Carlo



This issue hasn't been resolved. I disconnected my second burner from my system since this post.

I distinctly remember both my burners being seen as seperate media devices in Ubuntu 6, 7, and I'm almost positive in 8. Can't remember if this was an issue in Ubuntu 9 series as I've not needed to use my dual burner for quite awhile.

Within windows the second burner was being seen, and it could read disks so it doesn't appear to be a problem with the hardware. It just wasn't being identified. Or if it was, it wasn't being associated to the /media/cdrom link

---

### Post by AlphaLexman on 2010-07-21
What is the output of:
```
sudo lshw
```from a terminal?

---

