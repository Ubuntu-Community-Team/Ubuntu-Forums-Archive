---
title: "HP_RECOVERY partition is hidden despite lack of flag"
date: 2010-01-09
forum: General Help
---

### Post by J V on 2010-01-09
Little explanation:
OEM HP pcs come with an HP_RECOVERY partition which contains an installer which will wipe the HD and install vista (shivvers)

Now despite how much I looooove vista, I was wondering why the OS_TOOLS partition shows up in places and recovery doesn't... especially cause niether have a hidden flag...

(As a side note, what the hell does OS_TOOLS do? google yields no answers)

---

### Post by lisati on 2010-01-09
Beat this: My laptop came with HDDRECOVERY (the system recovery partition), TOSHIBA SYSTEM VOLUME (I've never got my head round what it's for....something to do with installation?) as well as its regular Vista partition. I've since added a complement of Ubuntu partitions.....

---

### Post by J V on 2010-01-09
Same story here, I'm just wondering wtf OS_TOOLS is for and how on earth HP_RECOVERY is hidden... theres no flag... it should just show up on the computer window...

Hidden at the BIOS level perhaps?

---

### Post by solitaire on 2010-01-09
Think it's the partition type rather than what flag it has. What does Gparted say about the partition?

OS_Tools might be specific to HP's install (it may hold the programs required to reinstall the OS from the image in the Restore partition.) Or it might just be the name that HP gave the drive in your model...

Also what's in the OS_Tools partition may give you an idea of what it was/is for...

Also I noticed that Ubuntu 9:04 saw the revovery partition in my HP laptop but when I installed 9:10 it didn't list the partition.

It might be an OS thing, It see's it's a recovery and then does not list it as a valid drive to automount or view in drive listings...

I just removed that partition with Gparted (it's not like Vista is EVER gonna get to run on this laptop EVER!!!)

---

### Post by J V on 2010-01-09
gparted palimpsest and fdisk all confirm its just your average NTFS filesystem... vista coulden't see it either when that was still on...

9.04 wubi install here coulden't see it either...

```
ls /media/OS_TOOLS
boot.sdi 
MASTER.LOG.COPY
System Volume Information (folder)
HP_WINRE
$RECYCLE.BIN (folder)
WINRE.WIM

```What kind of recovery has a recycle bin ffs?

---

### Post by solitaire on 2010-01-09
I've seen Recycle bin on some recovert partitions. Depends on how they made the inital image.

Also if they power it up to test the recovery procedures, vista automaticaly creates the recycle and SVL folders on any drive it can see. and that's then saved as an image for that range of PC's!

Basically they were LAZY when making the image... lol

---

### Post by J V on 2010-01-09
Still no idea why recovery won't show though...

---

### Post by vinnywright on 2010-01-09
dose fdisk see it?

dose grub boot it?

if it's NTFS and the fs. got corupted it wont be readabel untill it's had chkdsk run on it.......just a gess

I have a gateway 5200x with a recovery partition but it's VFAT and vewabell  along with the windows partition and bootable with grub.

VINNY

---

### Post by J V on 2010-01-10
fdisk grub etc see it but its not in the computer window by default and grub won't boot it...

---

