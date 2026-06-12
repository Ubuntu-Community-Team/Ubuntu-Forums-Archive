---
title: "just uninstalled vmware w/xp - reclaim space?"
date: 2006-03-14
forum: General Help
---

### Post by ImplicitProcrastination on 2006-03-14
Hi all,

I remember somehow setting aside about 7 gigs of my hard drive for the windows installation i did not to long ago through VMWare player. (Not sure how this process worked).

I just uninstalled VMWare, I was wondering if there was a way to reclaim that extra 7 gigs of hard drive space or if the uninstall program with VMWare already free'd that up (sure doesn't seem like it).

Thanks.

---

### Post by Aewheros on 2006-03-14
You can remove or reformat undesired partitions using partition editors such as gparted or kparted. You can even resize an adjacent partition to take up the freed up space.

It is usually recommended to backup important data first, though.

---

### Post by ImplicitProcrastination on 2006-03-14
I tried that but I didn't see anything like that... I'm not sure that it was even a new partition.

So I guess my question is essentially does VMWare uninstall do that for you? If so then where on earth could all my hard drive space have gone? (The second one is kinda rhetorical).

---

### Post by patrixl on 2006-03-14
There is probably a directory if your Home Folder that contains all the vmware data... If you can't see it, it's probably hidden (starts with a .  )

---

### Post by ImplicitProcrastination on 2006-03-14
I don't think so, I done got rid of all those things...

It might just be that I've downloaded more than I thought in the past few days, thats why I was wondering if somebody knew for sure how the VMWare works.

---

### Post by JavaJoe on 2006-03-15
If you installed a Virtual XP then that installation will be in the form of a .vmx file.  It is either the total 7gigs(if you sized the partition completly from the beginning), or it's about 3-7gig(if you selected to let VMware "span" the disk size).  Either way, to clear up the space given to your virtual machine, just delete the .vmx file wherever you put it.

Hope that helps!

---

### Post by ImplicitProcrastination on 2006-03-15
ohh ok, I thought that was just some kind of symbolic link or something.

that does help

---

### Post by JavaJoe on 2006-03-16
One other thing you might want to do, is make sure all instances of VMware is truely uninstalled.  When I put it on my laptop it slowed it down so bad that I uninstalled it.  However, after I uninstalled it I noticed there were still some files left over.  So you might want to comb your system for any vestigal parts.

---

### Post by Putztzu on 2006-03-16
The VMWare application hardly takes any space. Uninstalling the application will only recover a few megabytes, hardly more.

The VMs though will take up gigabytes of space. When you created your VM for XP, it sounds like you created a virtual disk file which might have been totally allocated from the beginning (all 7gb) or self-growing (probably is about 2gigs if you didn't install anything else in your XP VM). This virtual disk file is the "hard drive" for the VM you created.

You can locate your VMs a few different ways... But the easiest is probably to do a search for any files with a "VMDK" extension. Delete the entire folder containing that file to remove all the files related to your VMs.

Good Luck,
Putztzu

---

