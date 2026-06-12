---
title: "how to backup (clone) an ext4 partition"
date: 2011-12-14
forum: General Help
---

### Post by Gingalone on 2011-12-14
I am trying (before a restructuring of my internal HD) to make a backup of an ext4 partition of my ubuntu oneiric system; but: partimage doesn't work with ext4 fs AND clonezilla live does not boot my HP 6730b laptop (tried twice (2 iso download, 2 CDs burned) I saw many others had the same problem).
What about???
Thanks for any help.

---

### Post by Henkdroid on 2011-12-14
Open "Backup" select the partition (it has to be mounted) and tell it where to back it up to.
Hopefully this helps.

---

### Post by pretty_whistle on 2011-12-14
> **Gingalone said:**
> I am trying (before a restructuring of my internal HD) to make a backup of an ext4 partition of my ubuntu oneiric system; but: partimage doesn't work with ext4 fs AND clonezilla live does not boot my HP 6730b laptop (tried twice (2 iso download, 2 CDs burned) I saw many others had the same problem).
What about???
Thanks for any help.
Did you make the computer boot from the Clonezilla CD in the boot order menu?

I have a different HP laptop and its working for mine.

---

### Post by seawolf167 on 2011-12-14
> **Gingalone said:**
> clonezilla live does not boot my HP 6730b laptop (tried twice (2 iso download, 2 CDs burned) I saw many others had the same problem).

Have you changed your boot order settings in BIOS so that your cd/dvd drive is the first priority boot device? Alternatively you can hit your specific key during POST (usually [F12] or [F10]) to give you a boot menu then select to boot off the cd.

---

### Post by Gingalone on 2011-12-15
Thank you for replies!
to Henkdroid: backup can backup only folders, not an entire partition (which is my necessity)
to pretty_whistle and seawolf167: the clonezilla live CD has a strange effect on my laptop: when I boot with that cd in the optical drive it starts working and no bios options are available (the normal BIOS settings ESC key has no effect) it appears the system tries to boot from cd (noise)  but it works with no end (I waited 15 minutes) while the screen is just black... I got exactly the same behaviour with both Clonezilla cds (versions 1.2.11-23-i486 and 1.2.11-23-oneiric)...

---

### Post by seawolf167 on 2011-12-15
Can you try using a [Clonezilla Live USB ]("http://clonezilla.org/liveusb.php")instead and see if that has any other effects?

Additionally, are you able to select any screen resolutions (or "safe modes") in Clonezilla?, are you using the x86 (32 bit version) to ensure compatibility? (for the Live CD)

---

### Post by Gingalone on 2011-12-15
I have just checked the iso file with
md5sum -c 
I got:
md5sum: clonezilla-live-20111125-oneiric.iso: no properly formatted MD5 checksum lines found

so, something is wrong in the original clonezilla image file (a colleague of mine had the same result).
I'll try the USB way...

---

### Post by seawolf167 on 2011-12-15
If something is wrong with the .iso, you'll have to re-download it (the USB way won't work if the iso is corrupted)

[Here is how to MD5Sum ]("https://help.ubuntu.com/community/HowToMD5SUM")for a fresh download.
Make sure you have the correct MD5Sum for the correct download.
[Here ]("http://clonezilla.org/downloads/stable/iso-zip-files.php")are the stable builds -- [Here ]("http://clonezilla.org/downloads/stable/checksums.php")are their corresponding MD5Sums to check against

---

### Post by holycow131415 on 2011-12-15
Quoted from threads.

"GParted is useful for tasks such as: creating space for new operating systems, restructuring disk space to separate user and operating system data, and **_copying partitions_** to enable upgrading to a larger hard disk drive"

"
 I needed to migrate XP from a 60G drive to a 320G drive. Here's what I did:
[LIST=1]
[*]I installed Ubuntu Desktop Edition on a 8G USB Drive ([http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)).
[*]I put the new drive in an external drive enclosure (this one actually: [http://www.newegg.com/Product/Product.aspx?Item=N82E16817145133](http://www.newegg.com/Product/Product.aspx?Item=N82E16817145133))
[*]I backed up my old 60G drive. I shut down the PC, then powered up but upon startup entered the BIOS (by hitting F2 in my case).
[*]In the BIOS I changed the boot ordering so the the USB drive would have first priority.
[*]I saved the BIOS change and allowed the PC to boot into Ubuntu from the USB drive.
[*]From a Linux command shell I ran: sudo gparted
[*]In gparted I created a single ntfs partition on the new 320G drive.
[*]In gparted I navigated to the old 60G drive, clicked on the existing partition, and selected "Copy".
[*]In gparted I then navigated to the new 320G drive, clicked on the new partition, and selected "paste". After asking if I was sure, Gparted proceeded to copy the contents of old drive to new.
[*]In gparted I marked the new drive's partition as bootable (from menu: Partition-Manage Flags)
[*]I shutdown the PC, took out the old drive, put in the new. (Note: do not attempt to boot with both drives attached - I've read that XP doesn't like that).
[*]I powered up and it booted to an XP Chkdsk screen (presumably XP noticed that something about the drive had changed and decided to check it out). No errors were found and XP then booted up. Migration done.
[/LIST]"

Or

"My easiest way is to put in a booting NetBSD or Linux CD, boot, and tell it to

dd if=/dev/hda of=/dev/hdb
I then shutdown, unplug the first drive, and reboot. Just as my easiest way may not seem easy to you, I guarantee you that all these other easiest ways don't seem like it to me. The important thing here is:

Your system is not running off of the disk you are cloning while you clone it.
You get all of the associated data of the boot sector and the partition map.
Because both disks remain bootable, you've got to switch them about or remove one in order to get the new disk to boot.
Now granted, this copies only the exact same partition map; if you want something different, you need to ask."

---

### Post by Bobhuber on 2011-12-15
> **Gingalone said:**
> I am trying (before a restructuring of my internal HD) to make a backup of an ext4 partition of my ubuntu oneiric system; but: partimage doesn't work with ext4 fs AND clonezilla live does not boot my HP 6730b laptop (tried twice (2 iso download, 2 CDs burned) I saw many others had the same problem).
What about???
Thanks for any help.
IMHO the best and most reliable backup utility is fsarchiver that can be installed thru the synaptic package manager. You can backup your entire mounted partition as an archive file that can be restored to ANY partition no matter what the original drive size is as long as there is room on the new partition. You will need a bootable system disk to restore grub after restoring the system.The program is included with the System Rescue CD which can be downloaded here >  [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download) and also has the online documentation. As a note to others reading this post if you ever plan on installing an SSD drive and maintaining drive alignment on the new drive Clonezilla will not work.

---

### Post by Gingalone on 2011-12-16
to seawolf167: I checked the MD5Sum of the downloaded clonezilla iso file against the official md5sum code provided by clonezilla.org and tha check is OK
but I still get:
```
md5sum -c clonezilla-live-1.2.11-23-i486.iso
md5sum: clonezilla-live-1.2.11-23-i486.iso: no properly formatted MD5 checksum lines found
```

maybe it's time to look for fsarchiver as suggested by Bobhuber (even if on its website they write: "It's still under heavy development so it must not be used on critical data"... scary warning!)

so: ...problem still pending...

---

### Post by Bobhuber on 2011-12-16
> **Gingalone said:**
> to seawolf167: I checked the MD5Sum of the downloaded clonezilla iso file against the official md5sum code provided by clonezilla.org and tha check is OK
but I still get:
```
md5sum -c clonezilla-live-1.2.11-23-i486.iso
md5sum: clonezilla-live-1.2.11-23-i486.iso: no properly formatted MD5 checksum lines found
```maybe it's time to look for fsarchiver as suggested by Bobhuber (even if on its website they write: "It's still under heavy development so it must not be used on critical data"... scary warning!)

so: ...problem still pending...
I started out using clonezilla but but after a couple of failures and drive size limtations I've used Fsarchiver daily for 2/years and restored from backups more times than I can count (Screwing things up just comes naturally for me especially in the learning process) .NEVER had a failure.Just don't have any programs or browsers open when you do the backup on a mounted partition. If that worries you  boot from the CD and do the backup from there.I just transferred my entire system over the a new SSD drive wih it . But in the Linux world > Different strokes for different folks holds true.

---

