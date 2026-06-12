---
title: "Hard Drive Problem"
date: 2010-08-01
forum: General Help
---

### Post by pippin418 on 2010-08-01
I'm running on Ubuntu x86 32 bit with a somewhat old 80G hard drive (ATA). I was watching a movie when Ubuntu told me "DISK FAILURE IS IMMINENT" and to back up all my data and replace the disk. The SMART logs (which is weird since it didn't use SMART before, at least that's what the SMART section said) say 

ID: 5
Attribute: Reallocated Sector Count
FAILED
Normalized: 32
Worst: 32
Threshold: 36
Value: 2741 sectors

Is my hard drive pretty much trash now?

---

### Post by prodigy_ on 2010-08-01
Most probably yes but sometimes SMART reading tools show false positives. To be certain, you should probably download a diagnostics tool from your HDD vendor website and check your drive with it.

---

### Post by pippin418 on 2010-08-01
Disk Utility doesn't show my vendor, is there a way to tell without me pulling out my hard drive again?

---

### Post by prodigy_ on 2010-08-01
You can try to use ```
sudo lshw
``` command in Terminal. It will output a long list of devices. Look for ***-disk** entries closer to the end of the list.

---

### Post by pippin418 on 2010-08-01
Erm... Seagate only offers Windows/DOS tools. I'd rather run it from Ubuntu (I have an XP Pro partition for gaming), but I don't want to restart to switch in fear that the hard drive will screw up.

---

### Post by prodigy_ on 2010-08-01
"For DOS" is their bootable CD version. You'll need this one.

However, if you're using this drive right now, I'd recommend to try to make a backup first (unless you have a recent backup already). Because if the drive is really failing, you risk losing your data.

---

### Post by pippin418 on 2010-08-01
Right.. Does Lucid have a backup program? Or should I use Deja Dup?

---

### Post by jerenept on 2010-08-01
Try BackInTime. It will backup your files to an external disk or network location.

---

### Post by pippin418 on 2010-08-01
BackInTime looks like it just makes hard links.

--EDIT--
Which it does. I want something to actually copy the files/folders.

---

### Post by prodigy_ on 2010-08-01
You can backup the whole partition using **dd** command. For example, assuming that the source partition is **sda1**: ```
dd if=/dev/sda1 of=/media/<another_partition>/sda1-backup.dd
```

If you have several partitions on the source drive just repeat this for all of them. And of course make sure that you create backups on a different physical drive.

---

### Post by pippin418 on 2010-08-01
Right I'm backing up to my external two fifty gig hard drive. Then I burn the DOS Hard Disk Checker and boot from that?

---

### Post by prodigy_ on 2010-08-01
Yes. BTW, don't forget to check your warranty status. It's usually good for 3-5 years, so if your drive isn't very old you might be able to RMA it.

---

### Post by pippin418 on 2010-08-01
Erm I think we're edging on 6+ years here.. I don't know the computer wasn't originally mine.

---

### Post by pippin418 on 2010-08-02
Okay, well SeaTools (DOS Text, not GUI.. GUI doesn't work for me) says it can't find a disk, but I'm still using the computer, both the Windows XP Pro partition and the Ubuntu 10.04 LTS Lucid Lynx are functioning fine, but it still says IMMINENT FAILURE is coming.

---

