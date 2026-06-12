---
title: "lost encrypted drive - please help!"
date: 2010-09-08
forum: General Help
---

### Post by prisoner849 on 2010-09-08
OK, a rather bad series of problems led me to need to format my copy of ubuntu 9.10. I had 2 drives on this computer, one was the drive I installed the fresh copy of ubuntu to and the other was an encrypted drive I had all my data on. Like an idiot I didn't have a backup anywhere, but I tested out mounting this encrypted drive from the live CD without problem. I presumed then that should I format the 1 drive, I should still be able to mount the encrypted one from the fresh install. So, during the install process I simply selected for ubuntu to install entirely to the unencrypted drive. Once I got into the fresh install though, my encrypted drive was no longer recognized as a luks partition.

WTF, I need that drive. I never told the install process to touch the other drive and I felt that no harm should come to it during the install.

Is there anything I can do, I really really need this drive back?

Please help!

---

### Post by mastablasta on 2010-09-08
you probably deleted your key which could be on this drive where you installed the new version.

---

### Post by prisoner849 on 2010-09-08
Cheers for the super fast reply.

I had a bad feeling that part of the encrypted key was stored on the OS drive. I was so use to using true crypt on my windows box I didn't think there would be data stored anywhere else but the encrypted drive in question.

In any case: Is there any way to tell what the state of a drives partition table is? If it refers to my LUKS partition as just free partitioned space, is there any way to regenerate the partition table and still open it with my old key? Or is there encryption information in the partition table or sommin?

When trying to luksopen the drive, it just says it's not a luks partition.

---

