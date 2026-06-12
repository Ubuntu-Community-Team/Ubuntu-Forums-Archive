---
title: "External hdd delete failure"
date: 2011-08-07
forum: General Help
---

### Post by Toegang on 2011-08-07
Hi,

I have an external hdd for back-up purposes. To free some space I deleted some maps for the hdd had nearly no free space. What happened was that the maps are gone, i.e. not visible nor accessible, but the free space did not chance! The hdd is ntfs formatted No difference in accessing the hdd with Ubuntu (11.04) or Windows (Vista). Yes I had the settings put to show hidden and system files & maps.
It's a 250 GB harddisk and the maps deleted where some 40 gig.

What could have happened and how can I regain my free space.

Looking forward to the help,
Thanks,

Toegang

---

### Post by haqking on 2011-08-07
> **Toegang said:**
> Hi,

I have an external hdd for back-up purposes. To free some space I deleted some maps for the hdd had nearly no free space. What happened was that the maps are gone, i.e. not visible nor accessible, but the free space did not chance! The hdd is ntfs formatted No difference in accessing the hdd with Ubuntu (11.04) or Windows (Vista). Yes I had the settings put to show hidden and system files & maps.
It's a 250 GB harddisk and the maps deleted where some 40 gig.

What could have happened and how can I regain my free space.

Looking forward to the help,
Thanks,

Toegang

emtpy trash

---

### Post by Toegang on 2011-08-07
Thanks, good point but too obvious not to do. I already had emptied the trash, even tried to delete .trash and emptied recycle bin as well in Windows, as in you never know.

Point is that if I add all the sizes (seen in properties) of the maps (& files in the root) together I'm missing about that 40 gig ...

---

### Post by Toegang on 2011-08-12
Did you have a similar problem, how did you handle this mysterious failure? :confused:

I'm anxious for the solution. Can anyone help me?

---

### Post by westie457 on 2011-08-12
> **Toegang said:**
> Did you have a similar problem, how did you handle this mysterious failure? :confused:

I'm anxious for the solution. Can anyone help me?

This might work, no guarantees but it is safe.

Boot into a LiveCD/USB, select try at the welcome screen.

From the live Desktop start Gparted, right-click on the partition that is giving the problem. Ensure it is not mounted and select Check.

If there are no errors then at least you know your partition is okay.

---

### Post by Toegang on 2011-08-21
Thanks for the tip,

Busy, busy and no time to handle the question. 

Well, I didn't exactly do a partition check, but did resolve the problem. For what it's worth I'll tell the world what I did. Performed a checkdisk in Windows, which resulted in a found.000 folder, inaccessible though. Even after altering the properties and trying to access it with administrator rights. Then in Ubuntu I could look at the folder and it contained the 'lost' 40 GB of data. Moved it to the trash, emptied the bin and there it was, the free space I was looking for.

Although I did overcome the problem, I still don't know why it happened in the first place . . . Deleting a folder, emptying the trash-bin and being deprived of the regained free space. I'll blame it on the little free space left in the first place provoking the possibilities of read and write failures.

---

