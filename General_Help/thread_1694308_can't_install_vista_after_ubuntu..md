---
title: "can't install vista after ubuntu."
date: 2011-02-24
forum: General Help
---

### Post by Supakon on 2011-02-24
Hi,
  I recently installed ubuntu10.10,i didn't dual boot so i've only got that OS on my laptop and although i really like ubuntu so far i need to reinstall vista because there are some programmes i use that wont run in ubuntu.
I tried rebooting with my vista recovery disc in and it wont load the files,i've reinstalled vista many times in the past with the same disc without problems but never after i've installed ubuntu.
I've read about bootloader and grub,don't fully understand it,could that be why i can't load the vista files?

---

### Post by AbsolutIggy on 2011-02-24
You need to clarify what happens. What do you mean by 'doesn't load the files'?

And to be sure, you're having trouble installing or starting windows?

(If you're having trouble installing, grub probably won't help you. But you'll have to fix grub so you can boot ubuntu after installing windows.)

---

### Post by Supakon on 2011-02-24
When my laptop starts,it says windows is loading set up files,or something similar,with a loading bar across the bottom of the screen,when it reaches the end it then comes up with choose language,then where do i want to install,i choose and click ok.Then it says loading files this may take a few minutes,i've left it for about 20 minutes and it stays on 0%.

I'm assuming it's a problem with my laptop and not because i've got ubuntu installed.

---

### Post by decrepit on 2011-02-24
Ubuntu creates an ext3 or ext4 file system,that windows won't recognise, have you got a spare ntfs partition for windows to go in?
If that's the problem I'm surprised you don't get an error message saying no space on disk.

---

### Post by hansdown on 2011-02-24
Hi Supakon.

Just like to add, the recovery disks are different than install disks.

They look for a recovery partition, which would have bee overwritten by the ubuntu install.

---

### Post by Supakon on 2011-02-24
Thx Hansdown,much appreciated :),looks like i'll be using ubuntu permanently from now on lol

---

### Post by amoghharish871 on 2011-02-24
Okay, so I think I know what the problem is. While you install Windows, it replaces any other OS and claims itself as the primary OS. But, Windows only understands NTFS Hard disk partitions. NTFS is a very unstable type of partition which is the reason Ubuntu doesn't use it. If you want to reinstall Windows Vista, you need to format your partition in NTFS format. To do this, go into System>Adminstration>Disk utility. There, it displays the HDD or SSD you are using and also mentions the partitions that are available. Now, Click on the partition that you want to install Windows in and there will be an option below to format. Click on that and select disk type as NTFS and and click ok. 

But if you really want to run those apps, you could also try installing and setting it up under Wine. It should most probably work. Otherwise you could try finding opensource alternatives on the web and get them installed. 

And yeah, I totally forgot to mention this, you can't install Vista with a recovery disk. All the other times that you installed Vista, it must have already been installed and was just replacing the system files to the original state. Try downloading the ISO or get the original installation disk from one of your friends. The reason you can't use a Recovery disk is also because, the primary partition in your hard drive is occupied by Ubuntu.

---

### Post by Supakon on 2011-02-24
amoghharish871 thank you for your reply,i'll try those things you suggested :)

---

### Post by amoghharish871 on 2011-02-24
@Supakon Okay! If you need further help just post it again in this thread! BTW, which app were you wanting to use on Vista? Maybe I know an alternative for it.

---

### Post by Mark Phelps on 2011-02-24
So much misinformation here ... where to begin ...

> **amoghharish871 said:**
> Okay, so I think I know what the problem is. While you install Windows, it replaces any other OS and claims itself as the primary OS.
No it does not -- unless you tell it to.  It's perfectly acceptable to install MS Windows on a drive that already has another OS.  True, MS Windows will overwrite the MBR, but that's not "replacing any other OS".
>  NTFS is a very unstable type of partition 
Based on what, exactly?  
> which is the reason Ubuntu doesn't use it. 
Ubuntu doesn't use it because it's a proprietary format and there are alternative formats available that do just as well, if not better.
> If you want to reinstall Windows Vista, you need to format your partition in NTFS format. Only if you want to overwrite an existing partition.  If you leave some space unallocated, Windows will format that space for you. In fact, since Vista uses an enhanced version of NTFS, it's actually better to let IT format the space, rather than doing it with GParted.
>  But if you really want to run those apps, you could also try installing and setting it up under Wine. It should most probably work. In my own experience. Wine is one of the worst wastes of time there is. While it does run some things well, most of those are older versions.  Wine is best viewed as a last-resort option.
> And yeah, I totally forgot to mention this, you can't install Vista with a recovery disk. All the other times that you installed Vista, it must have already been installed and was just replacing the system files to the original state. 
While there are several kinds of "recovery" disks, some are just repair disks, meaning, they can fix boot problems and some disk problems. They can't be used to install or reinstall the OS.  Others are restore disks and they generally launch WinPE which then looks for a recovery partition on the drive containing a compressed Windows image file.  IF you did recovery before, not repairs, they worked not because Vista was already there, but because the recovery image was still present on the drive.  If you erased that image, the recovery disk will do you no good. > the reason you can't use a Recovery disk is also because, the primary partition in your hard drive is occupied by Ubuntu. While this could be true, the more likely reason is that you erased the recovery partition installing Ubuntu.  You can look for this by entering "sudo fdisk -lu" (that's a lowercase L, not a one) in a termial.  That will list out your partitions.  If the recovery partition is still there, it will show up in the list.

---

### Post by wiggly81 on 2011-02-24
> **Supakon said:**
> 
  i need to reinstall vista because there are some programmes i use that wont run in ubuntu.


maybe there is an alternative that will do the job for you in Ubuntu what sort of software do you want to run?

---

