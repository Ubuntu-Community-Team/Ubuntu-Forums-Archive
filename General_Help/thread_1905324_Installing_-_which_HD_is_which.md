---
title: "Installing - which HD is which?"
date: 2012-01-06
forum: General Help
---

### Post by nick roto on 2012-01-06
My PC has twin 500GB SATA disks in a RAID1 array running Win7  plus a single disk of the same type,  not part of the RAID. I want to install Ubuntu Only) on the third HD. On startup I will select whether to boot into Windows or Ubuntu (i.e. treat these effectively as two different computers).
During the install I was presented with a screen as follows ([] are green and orange squares, respectively):
*Installation type*
 
 *[**] mapper/isw_bcbjjgejje_Volume0p1 (ntfs)    [**] mapper/isw_bcbjjgejje_Volume0p2 (ntfs)*
    *104.9MB                                                                                                                  500.0MB*
 
 *Device*
 */dev/mapper/isw_bcbjjgejje_Volume0*
 
 */dev/mapper/isw_bcbjjgejje_Volume0       Linux device-mapper (mirror) (500.1GB)*
 *dev/mapper/isw_bcbjjgejje_Volume0p1  Windows 7 (loader)*
 *dev/mapper/isw_bcbjjgejje_Volume0p2*
 */dev/sdc                                                                                                 ATA ST3500320NS (500.1GB)*
 */dev/sdc1*
 */dev/sda*
 
                                                                                                                                     *[Quit] [Back] [Install Now]*
 

 My guess is that the first /dev line is the drive selected by default and I can scroll to select the one I want from the following list, and that that would be /dev/sdc.
Can someone please tell me if I'm right, or, if not, what I need to do. I would prefer not to unplug my RAID disks and start again.
Thanks

---

### Post by imachavel on 2012-01-06
wait wait wait, isn't raid 1 mirroring? How can you choose which partition to install a disk to if the drives mirror each other? I wasn't aware it was possible to 'choose' which partition to install to when mirroring drives. In that case it wouldn't be raid, it'd be master 1 slave 1 slave 2 etc. each disk would be a possible boot choice from the Bios. Sorry I wouldn't know how to perform what you are asking.

---

### Post by imachavel on 2012-01-06
> **nick roto said:**
> My PC has twin 500GB SATA disks in a RAID1 array running Win7  plus a single disk of the same type,  not part of the RAID. I want to install Ubuntu Only) on the third HD. On startup I will select whether to boot into Windows or Ubuntu (i.e. treat these effectively as two different computers).
During the install I was presented with a screen as follows ([] are green and orange squares, respectively):
*Installation type*
 
 *[**] mapper/isw_bcbjjgejje_Volume0p1 (ntfs)    [**] mapper/isw_bcbjjgejje_Volume0p2 (ntfs)*
    *104.9MB                                                                                                                  500.0MB*
 
 *Device*
 */dev/mapper/isw_bcbjjgejje_Volume0*
 
 */dev/mapper/isw_bcbjjgejje_Volume0       Linux device-mapper (mirror) (500.1GB)*
 *dev/mapper/isw_bcbjjgejje_Volume0p1  Windows 7 (loader)*
 *dev/mapper/isw_bcbjjgejje_Volume0p2*
 */dev/sdc                                                                                                 ATA ST3500320NS (500.1GB)*
 */dev/sdc1*
 */dev/sda*
 
                                                                                                                                     *[Quit] [Back] [Install Now]*
 

 My guess is that the first /dev line is the drive selected by default and I can scroll to select the one I want from the following list, and that that would be /dev/sdc.
Can someone please tell me if I'm right, or, if not, what I need to do. I would prefer not to unplug my RAID disks and start again.
Thanks


ok sorry maybe you are trying to install to one drive instead of using raid array. did you install a raid controller into an expansion slot? It would probably be sda2 or sda3 but I'm not sure I've only dealt with dev1/ or dev2/

I don't want to answer any more, I might answer your question incorrectly, and I may get banned.:confused:

---

### Post by nick roto on 2012-01-06
Thanks for having a go anyway. To clarify, I have a pair of HDs in a RAID configuration which supports Win 7. I don't want any changes or interference with this.
I ALSO have a similar disk which is NOT part of the RAID. I used to use the extra disk for data backups but am now using an external drive for that so I can dedicate the spare internal HD to Ubuntu. The idea is that at bootup I will select which drive, and hence which OS, I want to use.
My problem is that I want to be certain I'm installing on the correct drive. Windows sees it as my E: drive; I *think* Ubuntu sees it as sdc but there's sdc1, sda and the mapper partitions (?) to worry about. I COULD unplug the RAID drives, install Ubuntu on the the one HD it can then see and refit the RAID but I'd rather not; plus I'd prefer to understand what I'm doing anyway.

---

### Post by QIII on 2012-01-06
... or ...

You could unplug the third drive and see what you can see from the Live CD and deduce that the one that just went missing is the one you want to aim your installation at.

But, except for the twist with the RAID, I always just unplug the other drives to install another OS.  Then just make sure that the one I want with the GRUB I want is the first in the boot order.

That avoids overriding the MBR on the Windows drive and makes it so that if you have 5 drives and 5 OSes, you can unplug any 4 drives and have the other still boot.

(For example, my primary machine has 5 2TB disks.  Each has partitions for an OS and the rest as common NTFS storage.  There is a separate OS on each.  I use Kubuntu as the first drive in the boot order and update GRUB2 there.  If I unplug 4, I can get to the last one.  After I plug them all back in, of course, I always have to stop by the BIOS to reorder the drive sequence.  Also, I help myself out by putting a sticky bit of white tape on each disk with the name of the OS it's running.)

---

### Post by nick roto on 2012-01-06
Yes, well that's my main problem, I didn't build the machine so don't know which drive is which until I start unplugging them. I had hoped it wasn't necessary and I'd see what was what during the install. If it's not clear to experienced Ubutu-ers I'll just have to do it like that.
Any more thoughts before I reach for my screwdriver?

---

### Post by QIII on 2012-01-06
It's not that it's not clear in general - just to this particular guy.
 
 It's just a matter of what is safe and relatively fool-proof.  But you  would still be left with making sure your RAID configuration was  preserved or restored -- and that GRUB could see clearly how to boot  Windows in a RAID configuration, which is not something I have fiddled  with.

My ***suspicion*** is that /sdc is the one you are interested in, but I can't say that for sure.

---

### Post by nick roto on 2012-01-06
Thanks for looking at the problem QIII. It's a little late here to start dismantling the hardware so I'll abandon the install tonight and do it the safe way tomorrow.

---

