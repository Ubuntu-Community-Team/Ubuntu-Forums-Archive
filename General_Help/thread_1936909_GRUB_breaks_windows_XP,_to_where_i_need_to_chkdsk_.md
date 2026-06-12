---
title: "GRUB breaks windows XP, to where i need to chkdsk again"
date: 2012-03-06
forum: General Help
---

### Post by altjx on 2012-03-06
I have two hard drives in this machine:
SATA 400GB HD with Ubuntu 10.04
IDE HD with Windows XP

For some reason, the Windows XP hard drive only boots up after i run a full "chkdsk /r". The minute I enable the Linux SATA HD and try booting into it, refreshing GRUB, reboot, and try getting into XP, it stops the XP hard drive from even working.

For ex, once I do a "sudo update-grub2" and reboot, I can no longer get into Windows, not from the GRUB menu nor from booting to the XP HD from the boot menu. I am sure this is not a hard disk error, because it ONLY happens when after I get XP working, and THEN enabling the linux HD in the bios. I'm basically working on fixing windows xp to boot up properly, and then have grub re-detect xp.

I am trying to revert from having to reinstall XP all over this boot issue. I mean granted, when I run the chkdsk, everything in XP runs fine. Boots up well. But the minute I boot to the linux hard drive, windows XP hard drive stops working.

Any help would be greatly appreciated.

---

### Post by Sergius14 on 2012-03-07
If you only want to repair your WinXP, you should completelly disable your Ubuntu disk and boot from a Windows XP install CD.

When you start the install procedure you have an option to run a recovery console (I think that is the 'R' key option) before the format and install menu.

On that console (type help, o Google this for more help) you have at least to commands: Fix-Boot and Fix-MBR. Run both of them and then reboot.

This shoud completelly fix the boot/MBR to boot directly into your Windows XP with the Microsoft bootloader.

Be advised to completelly disable your SATA or you are going to overwrite your Grub2.

----

It is possible that your grub2 have been installed on your IDE... In that case, you will have to do this again but inverted: Disconnect IDE and left only SATA HDD and make the equivalent procedure from an Ubuntu Live CD.


Start with the Windows recovery and came back with your results.

---

### Post by altjx on 2012-03-07
> **Sergius14 said:**
> If your only want is to repair your WinXP, you should completelly disable your Ubuntu disk and boot from a Windows XP install CD.

When you start the install procedure you have and option to run a recovery console (I think that is the 'R' key option).

Over that console (type help, o Google this) you have at least to commands: Fix-Boot and Fix-MBR. Run both of them and then reboot.

This shoud completelly fix the boot/MBR to boot directly into your Windows XP. 

Be advised to completelly disable your SATA or you are going to overwrite your Grub2.

Also your grub may have been installed on your IDE...In that case, you will have to do this again but inverted: Disconnect IDE and left only SATA HDD and make the equivalent procedure from an Ubuntu Live CD.


Start with the Windows recovery and came back with your results.

Thanks for your reply. The XP CD that I have does not give me the "r" option for some reason like I've seen in screen shots.

I've reinstalled the entire OS and this seems to have fixed the problem and works perfectly now. At first, it would even give me the "YooYoo" text when trying to boot into XP. From some sources around, people say they've had to reinstall so I just went to that, considering I only had about 6 gigs to back up of data.

Thanks for your help though man!

---

### Post by oldfred on 2012-03-07
Were you hibernating in Windows and then writing into the NTFS partition from Ubuntu?

Best to create a shared NTFS data only partition, do not hibernate and set the XP partition as read only when you mount it from Ubuntu. Then you should not have problems in XP from Ubuntu.

---

### Post by altjx on 2012-03-07
> **oldfred said:**
> Were you hibernating in Windows and then writing into the NTFS partition from Ubuntu?

Best to create a shared NTFS data only partition, do not hibernate and set the XP partition as read only when you mount it from Ubuntu. Then you should not have problems in XP from Ubuntu.

Well, accessing XP from Ubuntu worked perfectly for me. My problem was when I was booting up the computer, the XP disk did not boot. I would have to load Hiren's Boot CD, and do a chkdsk on the XP drive in order for me to reboot and successfully access it.

The minute I turned back on the linux drive and booted up to linux, then rebooted and tried to get back into XP, XP wouldn't work again.

---

### Post by Mark Phelps on 2012-03-07
I can't tell if you answered oldfred's question about messing with the XP filesystem while XP was hibernated -- but based on your response, I would have to guess your answer is YES.

Which is the basis of your "problem".

Messing with a Windows filesystem while its parent OS is hibernated is likely to cause filesystem corruption -- which is why you will then have to run CHKDSK on it to get it working again.

It is best NOT to mess with a Windows filesystem while the parent OS is hibernating.

---

### Post by altjx on 2012-03-07
> **Mark Phelps said:**
> I can't tell if you answered oldfred's question about messing with the XP filesystem while XP was hibernated -- but based on your response, I would have to guess your answer is YES.

Which is the basis of your "problem".

Messing with a Windows filesystem while its parent OS is hibernated is likely to cause filesystem corruption -- which is why you will then have to run CHKDSK on it to get it working again.

It is best NOT to mess with a Windows filesystem while the parent OS is hibernating.

Well, I am not aware of making any changes to XP's filesystem while the OS was hibernated (or not being used rather). Once I ran the chkdsk to get it working, I had no reason to make any other changes to the filesystem. 

Unless updating GRUB somehow makes changes itself to the XP filesystem, then I'm not aware of any other causes.

---

### Post by Mark Phelps on 2012-03-09
Are you automounting the XP filesystem using FSTAB when Ubuntu is loading?  

Ordinarily that should not cause problems with XP, but you could look into /etc/fstab and confirm there are no entries for the Windows partitions.

---

### Post by altjx on 2012-03-09
Not quite sure at this point. The XP file system was definitely auto mounting, but I gave the PC back after formatting the XP drive and solving the issue.

---

