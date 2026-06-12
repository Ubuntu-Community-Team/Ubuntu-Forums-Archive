---
title: "grub menu"
date: 2006-05-09
forum: General Help
---

### Post by gos1 on 2006-05-09
hi ; 
 i first installed ubuntu and then bought a nother hard drive for win xp and installed xp on it but i cannot see that partition on grubs menu does anyone knows what changes should I do in /boot/grub/menu.lst  ??? 
(1 harddisk is pri master and the other one is 2 master if it changes anything ?  )

---

### Post by DOtSlaSHuCantCME on 2006-05-09
[QUOTE=gos1]hi ; 
 i first installed ubuntu and then bought a nother hard drive for win xp and installed xp on it but i cannot see that partition on grubs menu does anyone knows what changes should I do in /boot/grub/menu.lst  ??? 
(1 harddisk is pri master and the other one is 2 master if it changes anything ?  )[/QUOTE]

Add this to your grub/menulist,(**but change the root section to match your setup.** )"see arrow below pointing to where you should put your partition info".
[I]grub will have to be installed in your windows MBR.Then Grub will( give you 
the options in menu.lst[/I]

                                            **Add bellow entry in your menu.lst**

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


title		Microsoft Windows XP Home Edition
root		(hd0,0) # <---- (to remind you, to use your partition info here.)
savedefault
makeactive
chainloader	+1



Edit:i believe you might have to make windows drive primary(hda),and Ubuntu (hdb).So its just a matter of switching your slave/master on your drives,_and  editing your fstab tab ,if Ubuntu was hda, change all your Ubuntu partitions to read hdb. **i would edit my fstab first, then do the (physical)changes to harddrives,so when you reboot everthing is set.**_

---

### Post by gos1 on 2006-05-09
thanks a lot for your help but I am a newbie and I dont know in what device win is installed in. and also where can I find the linux file structure. Things I learned here is hda1 is the place I put my datas hda0 is the MBR of harddisk. So my win is in hdb1 
and MBR is hdb0 is this right ?

---

