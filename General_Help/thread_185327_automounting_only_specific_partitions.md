---
title: "automounting only specific partitions"
date: 2006-05-31
forum: General Help
---

### Post by everdred on 2006-05-31
Can anyone help me figure out how to have only certain partitions of my USB harddrive automounted? For instance, this drive is separated into a large ext3, a smaller ext3 and a fat32 (for a Windows ext driver, of course :), and I'd like only the large ext3 mounted upon plugging it in.

I'm using Dapper and I usually use Xfce as my desktop, which uses gnome-volume-manager. 

Any help would be much appreciated.

---

### Post by Dr. Nick on 2006-05-31
[quote=everdred]Can anyone help me figure out how to have only certain partitions of my USB harddrive automounted? For instance, this drive is separated into a large ext3, a smaller ext3 and a fat32 (for a Windows ext driver, of course :), and I'd like only the large ext3 mounted upon plugging it in.

I'm using Dapper and I usually use Xfce as my desktop, which uses gnome-volume-manager. 

Any help would be much appreciated.[/quote]

Pull up you /etc/fstab file and look at the partitions listed. If you see the word "auto" listed next to ones you dont want to mount automatically change auto to "noauto" and see how that goes.

---

### Post by everdred on 2006-05-31
[QUOTE=Dr. Nick]Pull up you /etc/fstab file and look at the partitions listed. If you see the word "auto" listed next to ones you dont want to mount automatically change auto to "noauto" and see how that goes.[/QUOTE]

Right, that's what I would do if these weren't being automounted by gnome-volume-manager, and thus aren't in my fstab in the first place.

---

### Post by Dr. Nick on 2006-05-31
oh sorry, Didnt realize gnome-volume-manager got in the way of it. Im not sure what you could do in that case. Maybe if you made a fstab entry for it manually it would overide gnome-v-m? Just a thought

---

### Post by everdred on 2006-06-12
*bump* 

Anyone?

---

### Post by everdred on 2006-06-18
Another bump.

I found System > Admin > Disks and chose to disable the partitions I didn't want automounted, but still found that they were mounted the next time I plugged in the drive.

---

### Post by n00bWillingToLearn on 2006-06-18
Not that this really helps you any, but I know from an article I read that thier are kernel options when compiling that allow the os to 'remember' a removable drive / partition by name, size, and other information ( enough that it would be almoast impossible to get a 'false positive' and mistake one drive for another even if they share many charicteristics ) and from that information you can set specific drives / partitions to have different mount points. This is only important because it proves that what you are trying to do IS possible. Not that I have any idea how to do it...#-oThe other consideration, which I also have no idea how to implement but I am sure others do, is to set a post mounting script that checks for a file in the root directory called something like "unmount me please" and then unmounts it, although that isn't a very clean hack. I hope this gives you or others that might try to help you some ideas, sorry I can't be more helpfull](*,)

---

