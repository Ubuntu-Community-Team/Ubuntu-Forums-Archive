---
title: "help with partitions &amp; installing"
date: 2009-08-02
forum: General Help
---

### Post by davewickett on 2009-08-02
Ive been thinking of a number of things that i could do but this is what i want to do now

Its ok i have about 9 gb on my d drive with my recovery on it. So i want to do is put backtrack on it .And with my c drive that as Ubuntu & Vista on i want to just give that all to Ubuntu.What would i do install backtrack on my d drive first then wipe out Vista with Gparted iso & how do i go about it please i just dont want to mess up if there is smoeone who could help me on how to go about this please
& would 9gb be ok to put backtrack on or not if not i could go for something smaller.

problem im having with my partitions dont want to lose anything.   

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6e8499e1

Device Boot Start End Blocks Id System
/dev/sda1 * 1 27154 218114473+ 7 HPFS/NTFS
/dev/sda2 29182 30401 9797632 7 HPFS/NTFS
/dev/sda3 27155 29181 16281877+ 5 Extended
/dev/sda5 28856 29159 2441848+ 83 Linux
/dev/sda6 29160 29181 176683+ 82 Linux swap / Solaris
/dev/sda7 27155 28777 13036684+ 83 Linux
/dev/sda8 28778 28855 626503+ 82 Linux swap / Solaris
thanks,
[ATTACH]123331[/ATTACH]
Dont know why i have linux & linux swap 2 times i installed ubuntu from live iso.                                                                                                                                  [IMG]http://forums.remote-exploit.org/images/backtrack4/misc/progress.gif[/IMG]

---

### Post by merlinus on 2009-08-02
What is backtrack?  And notice that linux does not use drive letters as does windows, so are you referring to sda2?

---

### Post by credobyte on 2009-08-02
> **merlinus said:**
> What is backtrack?  And notice that linux does not use drive letters as does windows, so are you referring to sda2?

[http://www.remote-exploit.org/backtrack.html](http://www.remote-exploit.org/backtrack.html) ;)

---

### Post by davewickett on 2009-08-02
> **merlinus said:**
> What is backtrack?  And notice that linux does not use drive letters as does windows, so are you referring to sda2?


yes i am referring to sda2 & i dont mind what i put on it fedora or open suse or something just need some help like i said i want ubuntu all on sda1 & wipe out vista but when i add the other os on sda2 (my d drive) how do i get them in one bootloader

---

### Post by merlinus on 2009-08-02
That is still not going to fix the situation with sda5 and sda6, however.  And sda2 is the recovery partition, so you will not be able to put an os on it.

So if you can create install cds for windows from the recovery partition, do that, and then back up personal data, if any, from ubuntu and do a fresh install using the entire disk.

Afterwards you can use gparted to create a partition for another os, as long as it is not windows.

---

### Post by davewickett on 2009-08-02
> **merlinus said:**
> That is still not going to fix the situation with sda5 and sda6, however.  And sda2 is the recovery partition, so you will not be able to put an os on it.

So if you can create install cds for windows from the recovery partition, do that, and then back up personal data, if any, from ubuntu and do a fresh install using the entire disk.

Afterwards you can use gparted to create a partition for another os, as long as it is not windows.

but as i dont want vista on sda1 anymore can i not just delete sda5 & sda6 & then give it all to ubuntu  & with sda2 recovery drive what if i format it as i wont need it anymore or is there no way at all i can install a other os on it

---

### Post by merlinus on 2009-08-02
As I first explained, sda5 and sda6 reside in an extended partition, so you cannot simply add that space to sda1.  I gave you step-by-step instructions for getting rid of those, etc.

If you want to get rid of sda2, then you can format it, but you cannot add space to it, or sda1, from sda5 and sda6 for the aforementioned reason.

You would have to delete sda5 and sda6, and then shrink the extended partition.  This would free up space that you could then add to sda2.

You can delete sda2 and give that space to sda1, and then the freed-up space from the previous steps as well.

But all this is complicated and time-consuming, compared to a fresh install.

---

### Post by davewickett on 2009-08-02
> **merlinus said:**
> As I first explained, sda5 and sda6 reside in an extended partition, so you cannot simply add that space to sda1.  I gave you step-by-step instructions for getting rid of those, etc.

If you want to get rid of sda2, then you can format it, but you cannot add space to it, or sda1, from sda5 and sda6 for the aforementioned reason.

You would have to delete sda5 and sda6, and then shrink the extended partition.  This would free up space that you could then add to sda2.

You can delete sda2 and give that space to sda1, and then the freed-up space from the previous steps as well.

But all this is complicated and time-consuming, compared to a fresh install.





ok looks like ill have to do a fresh install whats the best way with a ubuntu cd again put it all on sda1 vista will be gone then but what about sda2 i do want a other os & that drive would be just sitting there

---

### Post by merlinus on 2009-08-02
The easiest solution is to install ubuntu on the entire hdd.  That will solve the problems of sda5, sda6, and so on.

Then you can use gparted on the live cd to shrink the ubuntu partition and make another.

Another option is to choose manual at the partitioning menu, and create whatever partitions you want.

---

### Post by davewickett on 2009-08-02
yes thats all ok but still what about sda2 do i just leave it then or can i put my other os on there once ive done a fresh install with ubuntu on all of sda1

---

### Post by merlinus on 2009-08-02
If you choose use entire disk, sda2 will be gone along with everything else.  As I said in my last post, afterwards you can create another partition for whatever after installing.

Otherwise choose manual method at the partitioning screen, but you will still have to deal with sda5 and sda6.

My suggestion at this point is to figure out a plan for how you want to set up your hdd first.

---

