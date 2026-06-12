---
title: "Removing Windows partition and extending the Ubuntu one"
date: 2010-09-12
forum: General Help
---

### Post by rhoparkour on 2010-09-12
Hello there,

I've noticed that I really no longer need Windows, and would like to completely get rid of it. It would be great to delete it and be able to use the windows partition to extend the Ubuntu one.

It seems that the Disk Utility in System >> Administration could do the job, but I think it's a good idea to consult with people much more informed than I am.

Doing a clean install is not an option for me, I have some programs I paid for installed in Ubuntu and no access to the disks I need to reinstall them (in a different country) for at least a year.

As I am typing I am backing up every one of my files, thank you for your advice in advance!

P.S. Here is a screenshot of the Disk Utilty menu, the Windows partitions (the 355 and the 100 something one) are the ones to the right of the Ubuntu partition which is highlighted.

---

### Post by Lateralis on 2010-09-12
You can quite happily delete Windows and then expand your Ubuntu partition, but you can only make changes to the Ubuntu partition if it is unmounted.  That means in order to grow the Ubuntu '/' partition you will need to use the Ubuntu LiveCD.  You will need to unmount the swap partition as well.  

Personally, if it were me, I'd leave the Ubuntu partition exactly as it is and turn the Windows partition into additional Linux filespace and storage.  It will involve less faffage and means there's no chance of screwing up your Ubuntu '/' partition.  But if you did want to grow it, use the Ubuntu LiveCD, fire up Gparted (or your partition editor of choice) and expand the Ubuntu partition.  

Good luck!

---

### Post by rhoparkour on 2010-09-12
I'll just delete Windows and use it's space as data storage, since I have more than enough space in my Ubuntu partition for 2 users. 

Your suggestion sounds great, I'll post my results and mark this as solved when I've done it, but for now I have to go somewhere else.

UPDATE:

Just formatted the relevant partitions, everything is working perfectly. Will mark the thread as solved.

Thank you!

---

