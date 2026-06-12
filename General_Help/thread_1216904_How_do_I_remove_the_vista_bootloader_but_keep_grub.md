---
title: "How do I remove the vista bootloader but keep grub?"
date: 2009-07-18
forum: General Help
---

### Post by theWrkncacnter on 2009-07-18
Hi -- I'd like to remove the "vista" bootloader from my windows partition so that when I access it from grub, it goes straight to XP. I've seen methods of removing the bootloader, but they all seem to write over the MBR, and that's where GRUB is, so I don't think that's right.

Right now, if I choose "Windows XP" from GRUB, it sends me via chainloader to the vista bootloader, because I installed Windows 7 on a spare partition. I've deleted that partition now, but the bootloader is still there. How do I remove it, without messing up Grub and Ubuntu?

Any help would be appreciated. I hope this is the right forum.

---

### Post by CrusaderAD on 2009-07-18
Are you saying it still asks which OS to boot into? Even tho the Windows partition is deleted?

---

### Post by wcutrombonekid on 2009-07-18
i think thats what hes asking. 

I know theres a way to access what it shows in the terminal but i have no clue what it was

---

### Post by CrusaderAD on 2009-07-18
> **wcutrombonekid said:**
> i think thats what hes asking. 

I know theres a way to access what it shows in the terminal but i have no clue what it was

I know you can use the Startup Manager to set this stuff up in a GUI. You can install it from Add/Remove Programs.

---

### Post by hibliss on 2009-07-18
This is more complicated thanks to Microsoft switching from a boot.ini to BCD to handle the boot menu. To add on top of this, the standard solution which uses the XP disc to FixMBR will not work because it will overwrite grub.

You don't have a lot of good options. If you really want to get rid of the secondary boot options menu, you are going to have to apply the standard fix of allowing Windows to overwrite the MBR and restore the boot.ini for XP, then go through the headache of restoring grub.

You can try doing the Windows part, then using SuperGrubDisc, but if this does not work, it becomes a real pain to fix, there are many threads of people pulling out their hair because they installed Windows after Linux and it overwrote the MBR.

My advice would be to leave it as is, but if it is really important to you to change it, than you will most likely be posting back asking for more help to restore grub.

---

### Post by mdurham on 2009-07-18
restoring grub is easy using a live CD

---

### Post by theWrkncacnter on 2009-07-19
Ok, so the best solution is to overwrite the MBR with windows, and then restore grub again with the Live CD. I can  do that.

Its not absolutely necessary to change, it's just annoying to click on XP in grub, and then have to choose it again in the windows bootloader.

Thanks for your help, I'll get back to you if there are any problems restoring grub

---

### Post by wcutrombonekid on 2009-07-21
> **raptormanad said:**
> I know you can use the Startup Manager to set this stuff up in a GUI. You can install it from Add/Remove Programs.

thanks!

i didn't even know that existed!

---

