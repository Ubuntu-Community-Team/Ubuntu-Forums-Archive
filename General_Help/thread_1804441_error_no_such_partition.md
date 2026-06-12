---
title: "error: no such partition"
date: 2011-07-14
forum: General Help
---

### Post by rbscairns on 2011-07-14
This morning I tried to boot my computer and was told:
> error: no such partition
grub rescue

I have AUSU eee B202, 1.6GHz CPU, 1GB RAM, 80GB HDD. First Windows XP Home was installed. I later installed Ubuntu 10.10 with dual booting. Everything has worked fine for many months (including yesterday)until this morning.

```
ls
``` returns:

(hd0) (hd0,msdos5) (hd0,msdos2) (hd0,msdos1)

```
set
``` returns:

prefix=(hd0,msdos6)/boot/grub
root=hd0,msdos6

Now I am stuck. How do I boot into XP from here?

---

### Post by matt_symes on 2011-07-14
Hi

> (hd0) (hd0,msdos5) (hd0,msdos2) (hd0,msdos1)

> prefix=(hd0,msdos6)/boot/grub
root=hd0,msdos6

Grub cannot see partition 6 or it does not exist. 

Do you have a Wubi install of Ubuntu or is it installed on its own partition ?

If you know where the grub files are stored you can change prefix and root to point to the correct partition and continue booting.

If not, it's best if we can see your set up. 

From a LiveCD/USB boot into Ubuntu and download the bootinfo script in my signature. The instructions to run it are on the download page.

Run the script and post the results back here between code tags.

Kind regards

---

### Post by rbscairns on 2011-07-14
It was over 6 months ago, so I do not remember if Ubuntu was installed on its own partition.

I have no idea where the grub files are stored.

To try and boot from my LiveCD, plugged my external DVD drive into the USB port, went into BIOS and set:
[INDENT]Hard Disk Drives:
1st Drive = HDD:PM-ST980811AS
2nd Drive = USB:HL-DT-ST DVDRA

Boot Device Priority:
1st Boot Device = ATAPI CD-ROM
2nd Boot Device = HDD:PM-ST980811AS
3rd Boot Device = USB:Generic- Multi[/INDENT]
Put the LiveCD into the DVD drive and tried to boot. Same, error: no such partition

Next,went into BIOS and set:
[INDENT]Hard Disk Drives:
1st Drive = HDD:PM-ST980811AS
2nd Drive = USB:HL-DT-ST DVDRA

Boot Device Priority:
1st Boot Device = USB:Generic- Multi
2nd Boot Device = ATAPI CD-ROM
3rd Boot Device = HDD:PM-ST980811AS[/INDENT]
Tried to boot. Same, error: no such partition

Next,went into BIOS and set:
[INDENT]Hard Disk Drives:
1st Drive = USB:HL-DT-ST DVDRA
2nd Drive = HDD:PM-ST980811AS

Boot Device Priority:
1st Boot Device = ATAPI CD-ROM
2nd Boot Device = USB:HL-DT-ST DVDRA
3rd Boot Device = USB:Generic- Multi[/INDENT]
Tried to boot. Same, error: no such partition

Next,went into BIOS and set:
[INDENT]Hard Disk Drives:
1st Drive = USB:HL-DT-ST DVDRA
2nd Drive = HDD:PM-ST980811AS

Boot Device Priority:
1st Boot Device = USB:HL-DT-ST DVDRA
2nd Boot Device = USB:Generic- Multi
3rd Boot Device = ATAPI CD-ROM[/INDENT]
Tried to boot. Same, error: no such partition

I then tried the LiveCD/DVD drive on another (XP only) computer and it boots up into Ubuntu, no problem.

It looks like booting from a LiveCD is now not an option. Where can I go from from here?

---

### Post by Rubi1200 on 2011-07-15
Are you able to boot the computer with a LiveCD (setting the device priority) without plugging in the external drive?

If yes, do so and then plug in the external drive after you are at the live desktop and then run the boot info script mentioned by Matt.

---

### Post by rbscairns on 2011-07-15
My B202 computer does not have a built-in CD drive for LiveCD. My only option was to use the USB external DVD drive.

What I have now done is swapped out the HDD from the "broken" B202 and installed another internal HDD (with Win XP only on it) from another B202 computer. The "broken" B202 now boots into XP and I can use the USB external DVD drive to boot that computer into Ubuntu using LiveCD.

I now have the "broken" HDD in an external USB enclosure. I then connected this USB external HDD to the B202. This time I was able to get the B202 to start booting from this USB extremal HDD, only I still get the error message.

I have now attached the "broken" HDD to another computer running Ubuntu 11.04. I now have access to the "broken" HDD.

Where do I go from here to try and recover use of my "broken" HDD, preferably with not having to format it and loading all my programs again?

---

