---
title: "Need help to uninstall"
date: 2006-05-13
forum: General Help
---

### Post by pittpantherfan92 on 2006-05-13
Hello, 

I have recently installed Ubuntu on my PC.

I now would like to uninstall it.

I have a 2 drive system, 1 with just linux & 1 with just windows

Any help is appreciated.

---

### Post by djroadrash on 2006-05-13
am sure there is a more classy way to uninstall but when ever i dont mind just formating a drive i use other distros or even windows to do it. if i have a floppy i use DOS to just format the drive. then just install whatever on top.
:KS

---

### Post by pittpantherfan92 on 2006-05-13
[QUOTE=djroadrash]am sure there is a more classy way to uninstall but when ever i dont mind just formating a drive i use other distros or even windows to do it. if i have a floppy i use DOS to just format the drive. then just install whatever on top.
:KS[/QUOTE]

i'm not really sure how to do that. could you please explain? thanks.

---

### Post by djroadrash on 2006-05-13
i have a floppy with DOS in it, just boot your computer and once you get a C: type format C: enter and it will erase everything and format the disk on DOS, then just install whatever. if you are planing to install an other linux distro just boot the cd and use the partitioner to erase the ubuntu partition and install the distro. am not a very good windows user and have not use xp than much but am sure there is a way that u can use the partitioner in windows to format the drive. that is why i use DOS since is so simple.

---

### Post by djroadrash on 2006-05-13
just make sure that bios is set to boot floopy and cd before hd

---

### Post by pittpantherfan92 on 2006-05-13
i went to [www.bootdisk.com](www.bootdisk.com)

should i get a DOS boot disk? or a windows xp bootdisk?

---

### Post by djroadrash on 2006-05-13
what are u planing to do with this drive?, depending on that u can choose what to do.

---

### Post by djroadrash on 2006-05-13
like i said im not a windows user so im not very good at it. but im sure u can just add from your windows drive the other drive like a data drive. maybe a more experience windows user can explain.

---

### Post by garner_nc on 2006-05-13
Are you having problems booting Windows? Do you just want the HD space back for Windows or are there other problems?

All the Best,
Doug White

---

### Post by djroadrash on 2006-05-13
a quick google seach comes up with:
> Just going into XP Control Panel->Administrative Tool->Computer Management, using the 'Disk Management' facility and formatting the slave drive would remove Ubuntu completely.

If you've got a bootloader installed on the Master drive (the thing that lets you select whether to boot to Windows or Ubuntu), just boot from the XP CD, select the 'Repair Console' option and run 'fixmbr'.

That should do it.

a boot disk is a good way to go as well. but maybe a full explanation would be good since we are just throwing info at you with no real idea of the problem u have.

---

### Post by djroadrash on 2006-05-13
just make sure u are erasing the right drive if u use DOS since C: could be your windows drive.

---

### Post by pittpantherfan92 on 2006-05-14
[QUOTE=garner_nc]Are you having problems booting Windows? Do you just want the HD space back for Windows or are there other problems?

All the Best,
Doug White[/QUOTE]

i want the HD space for windows.

how do i know if GRUB is on the master?

---

