---
title: "Uninstall WIndows 7 and install Vista on partition?"
date: 2009-10-14
forum: General Help
---

### Post by ioasw on 2009-10-14
I have Ubuntu 9.04 and Windows 7 daul booted on seperate patitions using grub.  Can I uninstall the Windows 7 on my windows partition and then install Vista without any change or complications to the Ubuntu partition?  Will grub maintain focus, or will I have to modify it somehow?  Thanks in advance!

---

### Post by PrePenguin on 2009-10-14
> **ioasw said:**
> I have Ubuntu 9.04 and Windows 7 daul booted on seperate patitions using grub. Can I uninstall the Windows 7 on my windows partition and then install Vista without any change or complications to the Ubuntu partition? Will grub maintain focus, or will I have to modify it somehow? Thanks in advance!
  
 Yes but you have to reformat the windows 7 Partition because windows 7 will not allow a downgrade so you will need grub installed to maintain boot choice.

---

### Post by ioasw on 2009-10-15
Thanks, and I understand that I have to have grub installed, but I just want to make sure I don't muck anything up with my ubuntu partition if I wipe my windows 7 partition and then install vista in its place.

---

### Post by PrePenguin on 2009-10-15
> **ioasw said:**
> Thanks, and I understand that I have to have grub installed, but I just want to make sure I don't muck anything up with my ubuntu partition if I wipe my windows 7 partition and then install vista in its place.
 
 
You should be fine if windows 7 shows up in the boot choice it can be eliminated by using menu.lst very simple operation and many post on that in here. You may also have to reinstall grub to recognize the new vista not sure.

---

### Post by Sef on 2009-10-15
You could install Vista over Windows 7.

---

### Post by PrePenguin on 2009-10-15
> **Sef said:**
> You could install Vista over Windows 7.
   
 
Sef Windows 7 will not allow a Downgrade so you must reformat that partition unfortunately.. Tis just another MS thing

---

### Post by ioasw on 2009-10-15
I know that you can't downgrade.  I guess I'll just have to give it a shot.  I was hoping someone had already experienced this, and could tell me if I have to modify grub at all.  Do you know for sure if I have to modify grub PrePenguin, and is it difficult to reinstall grub?

---

### Post by PrePenguin on 2009-10-15
> **ioasw said:**
> I know that you can't downgrade. I guess I'll just have to give it a shot. I was hoping someone had already experienced this, and could tell me if I have to modify grub at all. Do you know for sure if I have to modify grub PrePenguin, and is it difficult to reinstall grub?
 
 
I am not sure if you will have to or not but is a very simple procedure and something you need to get use to anyways using menu.lst since everytime ubuntu updates the kernel you will want to eventually update grub anyways to keep tons of crap off the boot-up window OS choices. And you can just re-install grub with the installation disk.

---

