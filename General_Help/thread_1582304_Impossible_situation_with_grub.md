---
title: "Impossible situation with grub"
date: 2010-09-26
forum: General Help
---

### Post by Quackers on 2010-09-26
I have decided to delete all OSes and start again.
I have a Sony laptop with 2 hard drives.
Using GParted live cd I have deleted all partitions on both discs. I then reformatted both discs in NTFS. I then deleted all partitions again, so I would have both discs competely empty (ie unallocated space).
I then restored a Windows Vista backup image (for ONE programme that won't work in Wine!!!) using all available space on the first hard drive.
After rebooting I get "error: no such device: a0f9ca15-a968-4dd6-9cc8-087d4650f462
grub rescue>

How can this be? Where has grub come from? I don't understand. Grub should now be gone - no?
So now I can't boot Windows and my Ubuntu installation is gone.

Any suggestions would be much appreciated, thanks.

---

### Post by searchfgold6789 on 2010-09-26
So you have two hard disks that look pretty much like this
;;                       Vista;;
;;                       NTFS;;
and GRUB is loading?

How about you try fixing boot problems from the Vista CD (fixmbr) and see how that works.

You can do that by

[LIST]
[*]boot from the vista CD
[*]press a key when prompted
[*]select language and keyboard
[*]click Repair Your Computer
[*]select the OS you want to repair (vista)
[*]select command prompt
[*]type: ```
bootrec.exe /fixmbr
bootrec.exe /fixboot
```
[*]reboot your pc without the vista cd inside
[/LIST]
Hope that helps. If it doesn't feel free to post back.

The reason GRUB is loading is probably because, while GParted can erase your partitions, it does not erase your MBR (I think), where GRUB is stored. Restoring your Vista image does not restore the Vista MBR.

---

### Post by drs305 on 2010-09-26
Do what searchfgold6789 recommends.

The reason is that Grub is still installed on the MBR. If you ran the boot info script, you would have found no system files but it would still say that Grub2 is still installed on the MBR. 

You get the error message because as the computer boots the Grub2 information in the MBR still tells the system to look in your old Ubuntu partition for further instructions. By restoring a partition you have not yet changed the contents of the MBR.

By using the Windows disk, it will rewrite the MBR information, replacing the MBR Grub instructions with those of Windows.

---

### Post by Quackers on 2010-09-26
Thanks searchfgold6789, but I've tried bootrec /rebuildbcd and it's still the same error

---

### Post by Quackers on 2010-09-26
Thanks drs305, I will try those commands as well. I'll get back to you.

---

### Post by Quackers on 2010-09-26
Ok, thanks to you both Windows will now boot ok. (I wonder why /rebuildbcd didn't work? - nevermind that now :-))
Next question. Do I dare restore my Ubuntu OS from the Clonezilla Image or will that cause grub problems with UUID's? Or should I just re-install from the Ubuntu live cd?
Thanks again.

---

### Post by searchfgold6789 on 2010-09-26
/rebuildbcd is totally different from /fixmbr or /fixboot

---

### Post by searchfgold6789 on 2010-09-26
Reinstalling from the CD is the safest option here, I think. (from my avatar you can see I know a lot about safety)
But if you want to use the image you will have to restore the grub mbr from the liveCD.

[LIST=1]
[*]Boot into any live CD
[*]Mount you system partition (/dev/sdXY) ```
sudo mount /dev/sdXY /mnt
```
[*]Reinstall GRUB2 (do not specify a partition number here)
```
sudo grub-install --root-directory=/mnt /dev/sdX
```
[*]Unmount your system partition ```
sudo umount /dev/sdXY
```
[/LIST]
(courtesy of drs305's Grub2 guide)
Good luck,
 - search

---

### Post by Quackers on 2010-09-26
Ah I see.

---

### Post by raafaell on 2010-09-26
> **Quackers said:**
> Ok, thanks to you both Windows will now boot ok. (I wonder why /rebuildbcd didn't work? - nevermind that now :-))
Next question. Do I dare restore my Ubuntu OS from the Clonezilla Image or will that cause grub problems with UUID's? Or should I just re-install from the Ubuntu live cd?
Thanks again.

Install it from Ubuntu live cd, there shouldn't be a problem as Ubuntu will detect all you partitions.

---

### Post by drs305 on 2010-09-26
> **Quackers said:**
> Ok, thanks to you both Windows will now boot ok. ...
Next question. Do I dare restore my Ubuntu OS from the Clonezilla Image or will that cause grub problems with UUID's? Or should I just re-install from the Ubuntu live cd?


For me, it would depend on how much customization I'd made and how badly I wanted to restore those customizations. Based on your recent experiences, I'd be tempted to do a fresh installation. ;-)

If you decide to restore the image, you would probably have to chroot into the partition from the LiveCD, then reinstall Grub2. Until you do that, the MBR won't know anything about your Linux installation. Although there are less comprehensive methods to accomplish what you need, I'd completely purge and reinstall, using this guide:
[HOWTO: Purge and Reinstall Grub 2 from the Live CD ]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by Quackers on 2010-09-26
Raafaell, it's not the partitions I'm worried about so much as the UUID's of the partitions.
I wouldn't like to lose all my settings and changes made to Ubuntu so I will probably try the Clonezilla image route first. I've restored the grub mbr before using the live cd with drs305's help, so that should be ok. I'll have a think about it first.
Thanks again.

---

### Post by Quackers on 2010-09-26
> **drs305 said:**
> For me, it would depend on how much customization I'd made and how badly I wanted to restore those customizations. Based on your recent experiences, I'd be tempted to do a fresh installation. ;-)

If you decide to restore the image, you would probably have to chroot into the partition from the LiveCD, then reinstall Grub2. Until you do that, the MBR won't know anything about your Linux installation. Although there are less comprehensive methods to accomplish what you need, I'd completely purge and reinstall, using this guide:
[HOWTO: Purge and Reinstall Grub 2 from the Live CD ]("http://ubuntuforums.org/showthread.php?t=1581099")


Lol, those "recent experiences" are the reason I decided to start again :-) Thanks for the link to your guide, as I'm on a different computer at the moment so I didn't have that.

---

### Post by Quackers on 2010-09-26
I used the Clonezilla disc image and it restored ok. I then followed drs305's link and followed the instructions to purge and re-install grub2.
Yabbadabbadoo I'm back in business. Nothing lost (apart from some hair). Both systems boot ok from grub. Once again many thanks to all :-)

---

