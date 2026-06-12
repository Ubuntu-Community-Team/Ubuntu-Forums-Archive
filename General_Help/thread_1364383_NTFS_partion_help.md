---
title: "NTFS partion help"
date: 2009-12-25
forum: General Help
---

### Post by mathew edison on 2009-12-25
Hey all,

I was wondering if someone could help me with creating an NTFS partion for a windows 7 install USB. I have an 8GB empty USB so I can install windows 7 on my desktop but I need to make my USB a bootable NTFS type? I tried using mkntfs though I can't seem to make it bootable and NTFS is left out in gparted so that didn't work either. Hope someone can help me.

A bit late but merry christmas and a bit early happy new year :P

---

### Post by JC Cheloven on 2009-12-25
> **mathew edison said:**
> Hey all,

I was wondering if someone could help me with creating an NTFS partion for a windows 7 install USB. I have an 8GB empty USB so I can install windows 7 on my desktop but I need to make my USB a bootable NTFS type? I tried using mkntfs though I can't seem to make it bootable and NTFS is left out in gparted so that didn't work either. Hope someone can help me.

A bit late but merry christmas and a bit early happy new year :P

Perhaps not the best place to ask for that kind of help ... ;-)

---

### Post by tom.swartz07 on 2009-12-25
> **mathew edison said:**
> Hey all,

I was wondering if someone could help me with creating an NTFS partion for a windows 7 install USB. I have an 8GB empty USB so I can install windows 7 on my desktop but I need to make my USB a bootable NTFS type? I tried using mkntfs though I can't seem to make it bootable and NTFS is left out in gparted so that didn't work either. Hope someone can help me.

A bit late but merry christmas and a bit early happy new year :P
Just to clarify, youre trying to make a Windows 7 USB installer?

Theres an application that you could run through WINE to do that.

I have it attached. No worries, Its freeware downloaded from Gizmodo.

Hope this helps!

---

### Post by Marvin666 on 2009-12-25
Gparted didn't have ntfs? Did you launch it from a terminal with gksu gparted? That's how I launch it, and I just set up a 4gb thumbrive for ntfs.

---

### Post by Leppie on 2009-12-25
> **Marvin666 said:**
> Gparted didn't have ntfs?

i think you have to install ntfsprogs for (full) ntfs support in gparted.

---

### Post by mathew edison on 2009-12-26
The installer didn't work it gave me an error message.

After running gparted with gksu in stead of sudo I got the option to format it as NTFS file system and so I did. Then I tried to flag it as boot which also worked without problems. When I tried to boot from my USB stick I got the following error: "bootmgr is missing" which I've seen before but I really have no idea how I'd go about solving this. Any help would be appreciated.

---

### Post by Mark Phelps on 2009-12-26
If you're trying to make a Win7 bootable USB, you should go to the proper forum --> sevenforums.com.  

This is an Ubuntu forum, not a Windows 7 forum.

---

