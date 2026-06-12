---
title: "How to fix a hard drive with bad sectors."
date: 2010-01-20
forum: General Help
---

### Post by mindstormmaster1 on 2010-01-20
I recently got a bad virus that wouldnt let me reinstall Windows so I figured I would install Ubuntu and give it a go, but now it says my hard drive has "many bad sectors" a quick Google search shows many ways to fix this in Windows, but how do I do it in Ubuntu?  Easily since Im just getting the hang of things.

Thanks,
Ethan

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=144269&stc=1&d=1264008471[/IMG]

---

### Post by mk1w86 on 2010-01-20
The best thing to do would be to replace the drive because once you get a lot of bad sectors it can spread further across the disk causing data loss. ;)

However you could try the Western Digital drive diagnostics which you can download from here:

[http://support.wdc.com/product/download.asp?groupid=702&lang=en](http://support.wdc.com/product/download.asp?groupid=702&lang=en) 

The WD diagnostics can reallocate bad sectors and completely wipe the disk.

Make sure you backup any important data on the drive before running any diagnostics!!!

---

### Post by doas777 on 2010-01-20
agreed. you cannot repair the drive, regardless of your os. teh windows tools are an equivilant to teh oss "badblocks" app, which allows you to ignore the badblocks (note where they are, and just pretend that that space does not exist), but usually that is a sign that your disk is dying anyway, so might as well backup whatever you can get off it, while you still can. does you no good to mark and relocate your bad blocks, just in time for the head to crash or the spindle to seize.

if you can a whit for your data, take this kind of error/warning very seriously.

---

### Post by wojox on 2010-01-20
I've never seen that. It stated Windows only. Can I download the .iso and boot from cd-rom and use it?

---

### Post by mk1w86 on 2010-01-20
> **wojox said:**
> I've never seen that. It stated Windows only. Can I download the .iso and boot from cd-rom and use it?

Are you talking about the WD drive diagnostics? :-?

You can download the DOS CD version which is an iso image.

---

### Post by doas777 on 2010-01-20
> **wojox said:**
> I've never seen that. It stated Windows only. Can I download the .iso and boot from cd-rom and use it?
pretty sure you would want the dos cd version.

---

### Post by lykwydchykyn on 2010-01-20
My understanding is that bad sectors represent physical problems on a disk.  They can't be "fixed" by software, but you can tell the filesystem to mark them and not use them, which is what software that "fixes" bad sectors would do.

If you're using EXT2/3/4 (it's the default, so you probably are), you can boot to a live CD and use "fsck -c <device>" to accomplish this.

The reason replacement is recommended is that bad sectors usually have a physical cause, and that cause is usually still there causing more bad sectors.  So it's a sign of impending failure.

---

### Post by wojox on 2010-01-20
Cool thanks for the info to both of you. ;)

---

### Post by mindstormmaster1 on 2010-01-20
This is why I love Linux users and this forum just ask anything and poof you have some super great replys in a few minutes!  Thanks guys I was afraid of that luckily everything is backed up so once it fails it wont be a big deal just the battery life on that laptop is zero and the HDD is dieing so guess its time to get a new computer.

Thanks!

---

