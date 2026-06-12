---
title: "How do I access second USB partition?"
date: 2009-09-06
forum: General Help
---

### Post by Stone_Soup on 2009-09-06
I just went all Linux so I'm a real nub at all of this. Any help is really appreciated. After getting my system up and tweaked the way I wanted (ATI card wasn't as bad as people said) I decided to go through this book I bought ("Ubuntu Kung-Fu") and followed the steps to install Ubuntu 9.04 x86 onto my Patriot 8G thumb drive. 

I allocated an extra 1G for reserve space to save documents and the total size it took up was 1.7G. Thus I installed gparted and partitioned the USB thumb drive to create a seperate "data" partition (sdc2) to avoid any conflicts that may occur with me just dumping files on it at work (when I'm not using the Ubuntu live partition). 

In Ubuntu however I am unable to see the "data" (5.5G) partition and I can only see the 1.7G Ubuntu partition when it is mounted. **How would I access it (the data part) in Ubuntu?** Cheers.

*Additional Info: running 9.04 x86_64 platform with two additional HD's (10k Raptor [OS] and 320Gb Caviar Blue [data]).*

---

### Post by Vishnu V on 2009-09-06
go to gpartition Editor and check that 5.5G space is allocated or not if not Allocate the space.

---

### Post by P4man on 2009-09-06
not sure I understand the question, but just be aware that windows can not see anything except for the first partition of a removable media. So that FAT32 partition will be invisible and inaccessible in windows, all it sees is the first one.

There is a hack to change that, but involves installing some drivers and registry hacking, Im not sure that is something you can or want to do on your work machine.

---

### Post by Stone_Soup on 2009-09-06
I've verified that it is allocated in gparted (as well as formated vfat).

---

### Post by Stone_Soup on 2009-09-06
P4MAN-I'm trying to access a second partition of a removable media in Ubuntu. In the first partition I have a live Ubuntu install. I partitioned the thumb drive because its too large (8G) and wanted to create a second partition for data (5.5G). My problem however is that I cannot access it (the second 5.5G partition) in Ubuntu.

---

### Post by The Cog on 2009-09-06
I think that the second partition _should_ show up in **places**. If it isn't, I wonder if it is actually formatted? You could try formatting it with gparted partition editor and see if that helps.

---

### Post by P4man on 2009-09-06
> **The Cog said:**
> I think that the second partition _should_ show up in **places**. If it isn't, I wonder if it is actually formatted? You could try formatting it with gparted partition editor and see if that helps.

edit: sorry I confused 2 threads.. I said nothing :)

---

### Post by Stone_Soup on 2009-09-06
Yea, it showed up in Places, I just had to restart and the second partition showed up. Thanks all.

---

