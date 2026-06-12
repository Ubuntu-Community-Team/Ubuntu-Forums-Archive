---
title: "(Nasty?) Problem with initialization"
date: 2011-09-03
forum: General Help
---

### Post by bororeh on 2011-09-03
Hello everyone!

First of all, if this is not the place to post this, I'm sorry.

My girlfriend needs Windows on her machine. As it is a netbook and it came with Win 7, it is very very slow, so we created a new partition and installed Ubuntu on it. She liked her "new pc" and have been used Ubuntu for months now. But she still needs windows sometimes (for an english course that she does that requires IE7 and windows) and yesterday I tried to install Win XP. :(

Now, the pc wont even start. The black screen tells me that

[I]Windows can't start due to a hardware configuration disk problem.
Can't read the selected initialization disk.
Check the initialization pathway and the disk hardware.[/I]

Also acuses hal.dll file to be missing or corrupted.

I've tried to fix the boot to initialize in the Ubuntu partition that remains there installed (I hope!! hehe), but I really suck trying to fix this kind of stuff.

Here is a copy of my diskpartitions (dunno if it helps):

[I]Disk 0 with 240 GB [MBR]
G: Partition1 <Recovery> [NTFS]
C: Partition2 <SYSTEM> [NTFS]
F: Partition3 [NTFS]                           <-- the one I formatted (previous 7) and installed XP.
E: Partition4 [NTFS]
H: Partition5 [Unknown]                     <-- Ubuntu (I hope!)
I: Partition6 [Unknown]                      [/I]*<-- Ubuntu (I hope!)*
[I]
Disk with 16GB in disk [MBR]
D: Partition1 [FAT32][/I]



Again, I'm sorry if I should not be here asking for win support, but you guys from the forum were the only ones that really helped me last time I needed (that time with Ubuntu problems).

Thanks a lot!

---

### Post by bororeh on 2011-09-03
Well, I was able to restore Grub!!  [IMG]http://ubuntuforum-br.org/Smileys/default/cheesy.gif[/IMG]

Now the pc starts properly as before I messed it up, presenting options to start either on Ubuntu or Windows 7 (which is odd because I've formatted that partition and installed XP on it, and even the Grub Customizer program shows me the Win 7 option and not XP).

My question now is if is there a way to clean up the windows partition and agregate it to Linux's so I do not have all this huge dead space on the HD, without reinstalling Ubuntu because its working just fine now.

Thanks!!

---

### Post by Sin@Sin-Sacrifice on 2011-09-03
Yeah, try gparted. It's a great partition editor. If you're using KDE I don't know the name but there is an equivalent partition editor. Inside either program you'll see there's options to resize them.

---

### Post by bororeh on 2011-09-04
OK, thanks a lot, man!

---

