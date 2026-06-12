---
title: "Add a hard drive?"
date: 2011-02-11
forum: General Help
---

### Post by pme 72 on 2011-02-11
I have been considering different backup solutions like external hard drives. My desktop has the capacity to add a second hard drive. Would it be possible to add a second internal hard drive and use it as though it were an external backup device?

---

### Post by jerrrys on 2011-02-11
an internal hdd will transfer faster

---

### Post by Devon64327 on 2011-02-11
Well usually backup drives are to prevent losing your data from a disaster like a flood or burglary, so an internal backup sort of defeats the purpose. Unless your hard drive is prone to failure which is pretty uncommon these days. Yes you can use another internal drive and it will be faster, but it's often a hassle as Ubuntu may not always recognize the second drive. Also most external backup drives come with software that automatically saves updated files to it rather than you having to do it yourself, and they will be much more convenient to carry around, and hotswap.

---

### Post by Hakunka-Matata on 2011-02-11
Have a look at the Rsync app.  That's what it does, and it's good.  It will backup to any location (hdd) you wish.

[https://help.ubuntu.com/community/rsync]("https://help.ubuntu.com/community/rsync")

---

### Post by pme 72 on 2011-02-11
Reviews of smaller external "portable" USB powered drives seem to indicate they can be fragile. The sturdier ones require a separate power connection and take up valuable space on the desk.

My HDD is 5+ years old and has undergone several clean wipes and countless Ubuntu installations.

---

### Post by jerrrys on 2011-02-11
> **Devon64327 said:**
> it's often a hassle as Ubuntu may not always recognize the second drive.

been running six hdd's and ubuntu for a couple of years

---

### Post by Bitrate on 2011-02-11
Setting up Ubuntu to use an additional internal hard drive is not a hassle provided one knows what they're doing. Simply install the additional drive in a spare drive bay and connect it up to either a PATA or SATA port (depending on the type of drive). Verify that the BIOS detects the drive and reboot.

Next, run GParted (or a similar program) to partition and format the drive with a file system of your choice. Lastly, you will have to mount the drive and set permissions for it.

---

### Post by pme 72 on 2011-02-12
Devon64327, you make a good point. An external solution makes more sense. I do not feel comfortable adding a drive just yet. I have read posts from multiple hard drive owners who have run into issues with Grub and upgrading. An external resource seems to be a simpler solution.

Thank you to everyone who contributed.

---

### Post by Nixarter on 2011-02-12
I couldn't help but address Devon64327's post (quotes in bold) to make sure people don't get confused...

**Well usually backup drives are to prevent losing your data from a disaster like a flood or burglary...** Based on what?  I strongly doubt this is true, but I also do not have data on the subject, so that is only my opinion.  However, the only reasons I've ever come across are stolen data (digitally, not from burgled drives) and hardware failure (mostly from common drive failures from normal use, but also from shock and damage from impacts).  Though it does happen, I would be willing to bet that flood-killed and burgled drives are exceedingly rare relative to lost data due to shock (electric), shock (physical), and digitally stolen data, and hardware failure due to normal use.  The only practical way (IMO) to protect your data from burglary or being digitally stolen is by using TrueCrypt or similar software.

**so an internal backup sort of defeats the purpose.**  Also not true.  Many people use internal drives for backing up their data because of the speed.  Everyone I've ever known backs up their data, then stores the drive until their next backup update.  So using an internal drive to backup does not have that disadvantage, even if either of those situations occur.  If the backup drive was left in the computer, then Yes, it would not offer protection against events like floods and burglaries (though, unless encrypted, your data is unprotected regardless).  But, just with an external USB drive, leaving the backed up data at the computer is bad practice and ill-advised.  This does does not change simply based upon where the drive happens to be while in the process of backing up the data (hooked up to the mobo, or through a usb port).

**Unless your hard drive is prone to failure which is pretty uncommon these days.**  Failed drives are very common, regardless of manufacturer or model.  There are factors that contribute to lower longevity (that can be adjusted to increase drive life), but assuming that drives last forever as long as they aren't stolen or flooded is simply unfounded.  The vast majority of hard drive failures I've seen or heard of are from normal wear-and-tear on the drives during normal use.  The next most common cause of failure are accidental drops.  Lastly, I've seen a couple fail from improper handling (electric shock).  That's it.  But yeah, normal use makes up about 90% of failures I've seen.  All drives will fail eventually.  There is simply no avoiding that fact.  Be prepared.

**Yes you can use another internal drive and it will be faster, but it's often a hassle as Ubuntu may not always recognize the second drive.**   Perhaps, but I've never come across this issue, and I've used many different models and brands of drives without ever having come across any issue.

**Also most external backup drives come with software that automatically saves updated files to it rather than you having to do it yourself, and they will be much more convenient to carry around, and hotswap.**  Well, I have seen drives that come with backup software.  But, there are two things to consider: 1.  I don't know of any that come with software the runs on linux (though it might exist), and 2.  All the software I've read about on those drives are basic "syncing" software.  It is useful to backup folders of files, like music or documents, but not system files.  So, if your main drive is for whatever reason inaccessible, you'd still have to go and get all the software again, and put your settings back... which takes forever.  There is much better programs out there that are FOSS for nix.  IMO, those "backup" programs that come with drives are little more than marketing gimmicks, and I wouldn't have any of it on a computer of mine.

All that being said, "internal" hard drives and "external" hard drives are the exact same thing.  The only difference is that "external" hard drives happen to have an extra adapter... and that's it.  The fact is, those adapters suck horribly.  If you decide on an external drive, I strongly recommend that you buy the drive and adapter separately.  That way you can choose the quality of the drive, and get a good adapter ("external drive enclosure") as well.

some notes:  I recommend a SATA II or III (AKA SATA 3.0 and SATA 6.0) drive.  As long as the enclosure is SATA I II or III it will work with any SATA drive version.  USB is slower than SATA I, so you won't get any difference in performance with a SATA II or III enclosure.  In other words, just but an enclosure that you like, as long as it is SATA.  Many newer computers have SATA II or III compatible motherboards, so getting a SATA II or III drive will give you significantly improved performance over an SATA I drive (though that's probably a moot point, as there aren't many SATA I drives available nowadays anyway).  [www.newegg.com](www.newegg.com) is a great place to get computer hardware like that.

---

