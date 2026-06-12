---
title: "Dual boot: Virus on windows partition"
date: 2011-10-08
forum: General Help
---

### Post by bball2601 on 2011-10-08
Hey guys,

I want to start off by saying have been using Ubuntu for a couple of years but still wouldn't consider myself all that experienced with 
Linux OS's.
I have an hp laptop (64 bit pavilion dm4 in particular) on which I dual boot Windows 7 and Ubuntu 11.04.
The other day I realized that I have a virus on my Windows partition.  I'm not entirely sure about the origin of the virus or how I got it.  This usually wouldn't be a problem because an easy fix would be to just restore my computer using Acronis True Image, however I have never done a Windows restore while dual booting.

Windows is my initially installed OS, so I am worried that if I restore Windows I will lose Ubuntu, which is the OS I use most and not affected by the virus.

Is there a way to restore Windows without losing Ubuntu, or I way i can create a backup image of Ubuntu which can be restored after I restore Windows?

Also, the backup image I have of Windows was taken when I already had been dual booting.  I know that Acronis did not back up anything having to do with Ubuntu, but is it possible that it would recognize that there is another OS and possibly leave if unaffected if I go through with the restore.

Sorry for such a long post, but I am generally new to dual booting and don't have any experience with system restoration on dual booted systems.

Thanks in advance for any help.

---

### Post by Dangertux on 2011-10-08
> **bball2601 said:**
> Hey guys,

I want to start off by saying have been using Ubuntu for a couple of years but still wouldn't consider myself all that experienced with 
Linux OS's.
I have an hp laptop (64 bit pavilion dm4 in particular) on which I dual boot Windows 7 and Ubuntu 11.04.
The other day I realized that I have a virus on my Windows partition.  I'm not entirely sure about the origin of the virus or how I got it.  This usually wouldn't be a problem because an easy fix would be to just restore my computer using Acronis True Image, however I have never done a Windows restore while dual booting.

Windows is my initially installed OS, so I am worried that if I restore Windows I will lose Ubuntu, which is the OS I use most and not affected by the virus.

Is there a way to restore Windows without losing Ubuntu, or I way i can create a backup image of Ubuntu which can be restored after I restore Windows?

Also, the backup image I have of Windows was taken when I already had been dual booting.  I know that Acronis did not back up anything having to do with Ubuntu, but is it possible that it would recognize that there is another OS and possibly leave if unaffected if I go through with the restore.

Sorry for such a long post, but I am generally new to dual booting and don't have any experience with system restoration on dual booted systems.

Thanks in advance for any help.

I would say that if you ONLY reimage the Windows partition Ubuntu should not be effected, your boot loader might need to be repaired but since it is a reimage I don't even think that would necessarily be the case.

That being said I've never done anything like that to my personal system, so I can't speak from experience. I would highly recommend backing up anything you find valuable before attempting to do this just in case it goes bad, and make sure you have all installation media (windows and ubuntu) at your disposal before making any hastey decisions.

---

### Post by Shazaam on 2011-10-08
You could try Kaspersky's rescuecd...
[http://support.kaspersky.com/viruses/rescuedisk](http://support.kaspersky.com/viruses/rescuedisk)

I use avast in WinXP so I don't know how well it works.

---

### Post by bball2601 on 2011-10-08
Yeah thats what I was thinking.  I was just reading about repairing the boot loader and it doesn't seem difficult, so hopefully that works.

---

### Post by bball2601 on 2011-10-08
Shazaam, thanks for the link, but I already have back up disks and a back up image of my computer from Acronis.  I would use Acronis for the restore, I'm just wondering how that would affect my Windows partition.

---

### Post by Mark Phelps on 2011-10-08
Acronis, like the other Windows image/restore apps, will restore an ENTIRE partition -- and back to the ORIGINAL size it was when you made the backup.

So, for the sake of discussion, let's say you originally had Windows in a 120GB partition -- and you make a image of that using Acronis.  Then, you shrink the Windows partition to 80GB, and install Ubuntu to the 40GB of new free space.

When you NOW restore the Windows partition using Acronis, it will reuse the entire original 120GB, effectively erasing the Ubuntu partition.

If you want to restore the Windows partition without overwriting the Ubuntu partition, you would have to restore it to a different drive, shrink it to the size of the current partition, do an image backup of that, and then restore THAT backup to the drive that has Ubuntu.

---

### Post by bball2601 on 2011-10-08
I just completed the restore and everything went smoothly.  The back up I restored from was created after I had already partitioned my hard drive for both windows and ubuntu, so there were no problems. 

Thanks for the info though Mark, it'll be very helpful if I ever run into that situation with another computer

---

### Post by SiathLinux on 2011-10-17
The simple solution would be to install ClamAV on your Linux - and scan your Windows from Linux - virus will be removed.

> **bball2601 said:**
> Hey guys,

I want to start off by saying have been using Ubuntu for a couple of years but still wouldn't consider myself all that experienced with 
Linux OS's.
I have an hp laptop (64 bit pavilion dm4 in particular) on which I dual boot Windows 7 and Ubuntu 11.04.
The other day I realized that I have a virus on my Windows partition.  I'm not entirely sure about the origin of the virus or how I got it.  This usually wouldn't be a problem because an easy fix would be to just restore my computer using Acronis True Image, however I have never done a Windows restore while dual booting.

Windows is my initially installed OS, so I am worried that if I restore Windows I will lose Ubuntu, which is the OS I use most and not affected by the virus.

Is there a way to restore Windows without losing Ubuntu, or I way i can create a backup image of Ubuntu which can be restored after I restore Windows?

Also, the backup image I have of Windows was taken when I already had been dual booting.  I know that Acronis did not back up anything having to do with Ubuntu, but is it possible that it would recognize that there is another OS and possibly leave if unaffected if I go through with the restore.

Sorry for such a long post, but I am generally new to dual booting and don't have any experience with system restoration on dual booted systems.

Thanks in advance for any help.

---

