---
title: "Crash and Burn"
date: 2006-06-05
forum: General Help
---

### Post by Adanufgail on 2006-06-05
Well, following the suggestions of others in other threads (whom I don't hold responcible) I am unable to boot my computer. Please let me elaborate.

Upon booting I am presented with the GRUB console.
	-If I can get to Windows I would be happy.

I am currently using a Knoppix Boot Disk to post this, and Knoppix is unable to mount any of the partitions of my second drive.

Here are my partitions:
Disk 1:
Fat32 Windows
Disk 2:
NTFS Files
Ext3 Ubuntu
SWAP for Ubuntu

here is the output of sudo fdisk -l (in Knoppix if that matters):

```
knoppix@ttyp0[knoppix]$ sudo fdisk -l

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14593   117218241    c  W95 FAT32 (LBA)

Disk /dev/hdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   ?      116388      126889    84344761   86  NTFS volume set
Partition 1 does not end on cylinder boundary.
/dev/hdb2   ?      105915      222310   934940732+  73  Unknown
Partition 2 does not end on cylinder boundary.
/dev/hdb3   ?           1           1           0   74  Unknown
Partition 3 does not end on cylinder boundary.
/dev/hdb4               1      213826  1717556736    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```

Please help aas this is very annoying being unable to boot (as one might imagine)

[EDIT]
I should also mention that I AM able to mount /dev/hda1 (Fat 32) and that my main concern is recovering the data on the NTFS drive so I can burn it to DVD and reformat it to Fat 32.

---

### Post by gingermark on 2006-06-05
Could you please elaborate further on what advice you received in those other threads (or post links to them). Were you able to successfully boot Ubuntu previously? What have you changed? What were you trying to achieve?

Seeing how you got to where you are could well aid in figuring out a solution.

---

### Post by codypumper on 2006-06-05
What is your bios set to boot from? (Hold delete at startup)

---

### Post by Adanufgail on 2006-06-05
[http://ubuntuforums.org/showthread.php?t=186280](http://ubuntuforums.org/showthread.php?t=186280)
[http://ubuntuforums.org/showthread.php?t=188803](http://ubuntuforums.org/showthread.php?t=188803)
[http://ubuntuforums.org/showthread.php?t=187886](http://ubuntuforums.org/showthread.php?t=187886)

Not sure if those are in order.

Here is the full story:

I experienced a power outage, and upon booting neither drive was recognized by the bios. This, I believe, is irrelivant as I let it sit off for a few minutes and it worked. However, I was unable to boot. I ran the Windows Install Disk and ran fixmbr from the console. I was then able to boot normally to Windows, but not Linux. I followed the Wiki's instructions and re-installed GRUB using the Ubuntu (5.10) install disk, and the command "grub-install /dev/hda". I was then able to boot Ubuntu. A day later I realized I could not boot Windows as it wasn't in menu.lst. I added it as instructed by one of the threads I posted above, and was unable to successfully boot. I tried using grub-install again, although I mistakenly ran "grub-install /dev/hd**b1**" rather than "grub-update /dev/hd**a**." This caused Ubuntu to fail to recognize my NTFS partition. Another user suggested running fixmbr on the second drive, which has left me in my current state.

cody: my BIOS is set to boot drive 1, then drive 2, as listed in my first post.

---

### Post by Adanufgail on 2006-06-05
If you need me to be more specific I can. My dad is really pressuring me to get back to a more stable system as I have a new graphics card on the way and a Live CD can't test to make sure it's working. :(

---

