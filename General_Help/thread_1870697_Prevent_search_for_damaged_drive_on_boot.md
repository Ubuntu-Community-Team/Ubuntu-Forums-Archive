---
title: "Prevent search for damaged drive on boot?"
date: 2011-10-27
forum: General Help
---

### Post by Irihapeti on 2011-10-27
I have an Asus EeePC 900 on which the smaller internal drive (/dev/sda) has died. I'm unlikely to get a replacement installed, and removing it would be a difficult task for me.

I'm booting successfully off either an SD card or an external HDD. The thing that's bothering me is that Ubuntu spends some considerable time during bootup trying to find /dev/sda before it gives up with an error and then continues with booting.

I'd like to be able to tell Ubuntu not to even try to do anything with /dev/sda. Is there any way of doing that?

It's not possible to disable it in the bios, because it's the master IDE drive; disabling it simply prevents the thing from booting at all.

---

### Post by ajgreeny on 2011-10-27
If it really is ubuntu that is trying to find, and presumably mount the disk, rather than the BIOS of the machine, you can probably stop this happening buy editing the /etc/fstab file with ```
gksu gedit /etc/fstab
```and comenting out the line relating to the missing partition/disk.

---

### Post by Irihapeti on 2011-10-27
Unfortunately, /dev/sda (or its equivalent UUID) isn't in /etc/fstab.

I think it's Ubuntu trying to find the disk because I get the following log entry over and over.

```

Oct 28 11:17:02 xxxxxxxx kernel: [   21.048812] ata2.00: configured for UDMA/66
Oct 28 11:17:02 xxxxxxxx kernel: [   21.063256] ata2.01: configured for UDMA/66
Oct 28 11:17:02 xxxxxxxx kernel: [   21.063279] ata2: EH complete
Oct 28 11:17:02 xxxxxxxx kernel: [   21.080360] ata2.00: configured for UDMA/66
Oct 28 11:17:02 xxxxxxxx kernel: [   21.094583] ata2.01: configured for UDMA/66
Oct 28 11:17:02 xxxxxxxx kernel: [   21.094606] ata2: EH complete
Oct 28 11:17:02 xxxxxxxx kernel: [   21.112357] ata2.00: configured for UDMA/66
Oct 28 11:17:02 xxxxxxxx kernel: [   21.124165] ata2.01: configured for UDMA/66
Oct 28 11:17:02 xxxxxxxx kernel: [   21.124187] ata2: EH complete
Oct 28 11:17:02 xxxxxxxx kernel: [   21.144424] ata2.00: configured for UDMA/66
Oct 28 11:17:02 xxxxxxxx kernel: [   21.153661] ata2.01: configured for UDMA/66
Oct 28 11:17:02 xxxxxxxx kernel: [   21.153685] ata2: EH complete
Oct 28 11:17:02 xxxxxxxx kernel: [   21.173317] ata2.00: configured for UDMA/66
Oct 28 11:17:02 xxxxxxxx kernel: [   21.181538] ata2.01: configured for UDMA/66
Oct 28 11:17:02 xxxxxxxx kernel: [   21.181567] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct 28 11:17:02 xxxxxxxx kernel: [   21.181575] sd 1:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
Oct 28 11:17:02 xxxxxxxx kernel: [   21.181586] Descriptor sense data with sense descriptors (in hex):
Oct 28 11:17:02 xxxxxxxx kernel: [   21.181591]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Oct 28 11:17:02 xxxxxxxx kernel: [   21.181612]         00 00 00 38 
Oct 28 11:17:02 xxxxxxxx kernel: [   21.181620] sd 1:0:0:0: [sda] Add. Sense: No additional sense information
Oct 28 11:17:02 xxxxxxxx kernel: [   21.181630] sd 1:0:0:0: [sda] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
Oct 28 11:17:02 xxxxxxxx kernel: [   21.181811] ata2: EH complete
```

All it seems to do is take longer to boot, and clog up the log files, but it would be nice to be able bypass it.

---

### Post by ajgreeny on 2011-10-28
Is there any way to disable the disk in your BIOS?

EDIT:  Woops!! I didn't notice that you had said you couldn't disable the drive, but if you follow dcstar's suggestion, or even simply use ```
sudo grub install /dev/sdx
``` where sdx is your "other" drive you should be good to go.

---

### Post by dcstar on 2011-10-28
> **Irihapeti said:**
> 
...........
It's not possible to disable it in the bios, because it's the master IDE drive; disabling it simply prevents the thing from booting at all.

Boot into Ubuntu from an other drive and then run this to **put the boot loader on the other drive**:

```
sudo dpkg-reconfigure grub-pc
```

Then disable the damaged drive in the BIOS and boot off that drive.

---

### Post by Irihapeti on 2011-10-28
Thanks for your suggestions.

Grub is already installed on the other drive - I take it by that you mean the replacement SD card that I'm using instead of /dev/sda.

I went back and had another play with the bios and DID manage to disable /dev/sda, or so I thought. The error still occurs on bootup and "sudo fdisk -l" still shows it to be present.

All this seems kind of odd, so maybe we have to put this down to a hardware quirk in the EeePC 900. As I don't want to pay to get the thing fixed, I may just have to live with it.

---

