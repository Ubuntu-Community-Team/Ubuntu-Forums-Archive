---
title: "Regaining system"
date: 2006-04-18
forum: General Help
---

### Post by Viorus on 2006-04-18
On my labtop I had ubuntu depper drake.
yesterday i descided to remove it to make a duelbot (by first installing win and then depper again)

well, now I have this problem:
my teacher wants me to resend an important document Ive saved on my labtop, all Ive done so far is formating the linux part and installing win (not full install yet, just till the 2nd reboot). is there any way to find my lost file? or even regaining the old deppar system I had?

---

### Post by pwrstick on 2006-04-18
Sorry, I'm not sure I understand.  Is the file on the partition that you formatted?  (I.e. did you format the file)

Or: what OS was the file created under and where is it?  If you've killed the file via format, some programs will let you get the file back.  I know of some for Windows, but I'm new to linux, though I wouldn't be surprised if you get a few suggestions here.

---

### Post by louis_nichols on 2006-04-18
I think it's a pretty tough situation you're in. Not that I want to discourage you...

But, in order to help you, one needs a few more details about the configuration of your HDD: how many partitions and what fstype each of them is/was both before and after installing windows.

As a side-note, you REALLY don't need to go through all that trouble to do a dual-boot. Having had Dapper installed, you could have just installed win on a separate partition, and then restoring GRUB to dual-boot would have been a simple enough operation.

---

### Post by Viorus on 2006-04-18
[QUOTE=louis_nichols]I think it's a pretty tough situation you're in. Not that I want to discourage you...

But, in order to help you, one needs a few more details about the configuration of your HDD: how many partitions and what fstype each of them is/was both before and after installing windows.

As a side-note, you REALLY don't need to go through all that trouble to do a dual-boot. Having had Dapper installed, you could have just installed win on a separate partition, and then restoring GRUB to dual-boot would have been a simple enough operation.[/QUOTE]



first i had a windows xp partition on my comp (a school labtop) till i sound another unused partition, but after i install ubuntu i couldnt duelboot it cuz of some problems with the superblock (if i remember right). so the win was on hda1 and i installed ubuntu at hda2 (root) and hda3 (for swap).

the file i need is at hda2, thats why i wonder if there is a way to rebuild the system as i was before (i formated those partition in the windows install, so i dont know if they're all delated or just "hidden")

---

### Post by Viorus on 2006-04-18
btw, sorry for my bad spelling, i just had one cup coffe and this "teacher" really pissed me off :???:

---

### Post by louis_nichols on 2006-04-18
ok, but did you do anything explicit to hda2? Did you tell win to "format it as... (fat 32 or ntfs)"? Do you see it as D or smth from win? Cuz if you didn't explicitly format it, it might actually be unchanged, in which case nothing is lost and you'll just have to restore grub in the MBR and make it read menu.lst from hda2. I can give you more details on how to do it, if this the case.

On the other hand, if you formatted hda2 as fat32 or ntfs, it's more complicated and might be a lost cause. You might try [Active@ Partition Recovery]("http://www.partition-recovery.com/") or maybe another tool from [UBCD]("http://www.ultimatebootcd.com/") (which also contains Active@ Partition Recovery).

I guess the important thing to (not) do right now is to stop making any more changes to the partitions till we establish exactly what is going on.

---

### Post by Viorus on 2006-04-18
[QUOTE=louis_nichols]ok, but did you do anything explicit to hda2? Did you tell win to "format it as... (fat 32 or ntfs)"? Do you see it as D or smth from win? Cuz if you didn't explicitly format it, it might actually be unchanged, in which case nothing is lost and you'll just have to restore grub in the MBR and make it read menu.lst from hda2. I can give you more details on how to do it, if this the case.

On the other hand, if you formatted hda2 as fat32 or ntfs, it's more complicated and might be a lost cause. You might try [Active@ Partition Recovery]("http://www.partition-recovery.com/") or maybe another tool from [UBCD]("http://www.ultimatebootcd.com/") (which also contains Active@ Partition Recovery).

I guess the important thing to (not) do right now is to stop making any more changes to the partitions till we establish exactly what is going on.[/QUOTE]

No
When you install win youll see all partition, and the fstab showed me the old win part and those two linux part with was marked as "unknown". all i did was pressing the D and delating those part, so they're now "unused space".

---

### Post by louis_nichols on 2006-04-19
[QUOTE=Viorus]No
When you install win youll see all partition, and the fstab showed me the old win part and those two linux part with was marked as "unknown". all i did was pressing the D and delating those part, so they're now "unused space".[/QUOTE]

well, it ain't that bad, then. the data is still there (and safe! - as long as you don't do a format - there is a pretty big difference between formatting a partition and simply deleting the info about it from the partition table) UBCD has at least one tool that recovers unused space that used to be a partition and returns it to the partition table.

I did exactly that once. Unfortunatelly, that was some time ago, so I can't give you many details about exactly how to do it, but its definitely doable.

look: go here: [http://www.partition-recovery.com/quest1.htm](http://www.partition-recovery.com/quest1.htm)
that should do the trick

EDIT: some completions

---

### Post by Viorus on 2006-04-19
[QUOTE=louis_nichols]well, it ain't that bad, then. UBCD has at least one tool that recovers unused space that used to be a partition and returns it to the partition table.

I did exactly that once. Unfortunatelly, that was some time ago, so I can't give you many details about exactly how to do it, but its definitely doable.[/QUOTE]


sounds good=)
I may be a noob at linux yet, just know they basics (iam more in everything that was with the internet to do), but for me its pretty easy to learn stuff, so teach me;)

---

### Post by louis_nichols on 2006-04-19
[QUOTE=Viorus]sounds good=)
I may be a noob at linux yet, just know they basics (iam more in everything that was with the internet to do), but for me its pretty easy to learn stuff, so teach me;)[/QUOTE]

please re-read my previous post. the link I posted might be exactly what you need. ;)

---

### Post by Viorus on 2006-04-19
[QUOTE=louis_nichols]please re-read my previous post. the link I posted might be exactly what you need. ;)[/QUOTE]


looks perfect=) thx:mrgreen:

---

### Post by louis_nichols on 2006-04-19
ok.

please, let me know how this turns out.

---

