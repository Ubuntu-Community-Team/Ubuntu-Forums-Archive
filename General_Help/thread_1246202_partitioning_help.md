---
title: "partitioning help"
date: 2009-08-21
forum: General Help
---

### Post by evanm457 on 2009-08-21
I am trying to partition my c drive so that i can run ubuntu along side vista but have there system files seperated. I am doing this in a vista application (pic attached) It only lets me use 37mb of the hard drive which is tiny to what ubuntu needs ie. 10gb or *10000mb. But I do have about 18gb free of the system drive. how can I locate this to ubuntu.

---

### Post by Soapy.Illusions on 2009-08-21
Have you tried shrinking your current drive (because it is in NTFS) and you need to later format that into ext3.
 
So you will need to shrink your current C partition to 10 gigs left, you will then have 10 gigs of unused space, which Ubuntu will format into ext3 for you after.
 
Be careful before you shrink a partition you should backup everything.
 
And if you are having trouble shrinking just send screenshots like you did
 
 
-Soapy

---

