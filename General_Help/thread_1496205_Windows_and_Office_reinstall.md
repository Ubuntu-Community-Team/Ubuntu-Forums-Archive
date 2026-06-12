---
title: "Windows and Office reinstall"
date: 2010-05-29
forum: General Help
---

### Post by finlost on 2010-05-29
This isn't exactly an Ubuntu question, but the Windows forums are so hard to navigate and I am often leery of the information on them.

Now to the problem at hand....

Unfortunately, I am bound to continuing an install of Windows due to the need to run QuickBooks.  With that said, I run a dual boot Lenovo Y510 laptop with Vista Home Premium and Ubuntu 9.10.  I cringe every time I need to boot to Windows.  Windows is so freakin' slow and often unresponsive.

I have noticed Vista getting worse and worse in performance.  I would like to reload Vista and MS Office 2007. I have OEM installation disks and I believe the appropriate installation keys.  Both are legal copies.

Per using GParted, I believe there is also a Windows recovery partition.  Am I better using the recovery partition or using my OEM disk?

I am more concerned about reinstalling MS Office 2007.  I need this as I use Excel in conjunction with QuickBooks.  I am responsibly certain OOo will not interface with QuickBooks.  All the user licenses for this copy of MS Office 2007 are used.  Since I am reinstalling on the same hardware, I *shouldn't* have any licensing issues.  This is MS, so I know there will be issues.  How do I ensure I will be able to reinstall MS Office  or am I SOL?

Once that is done, Ubuntu 9.10 will be installed and run 95% of the time on this laptop.

I know this isn't exactly the correct forum for this question, but I am hoping other knowledgeable dual booters will be able to give some help.

---

### Post by BoneKracker on 2010-05-29
Nice avatar. :P

---

### Post by finlost on 2010-05-29
Jerk

---

### Post by jerenept on 2010-05-29
You will probably need to reinstall Ubuntu, because the Windows installer  puts its own bootloader on the hdd. it does not recognise Ubuntu. Does Quickbooks run in WINE? there are some open-source options you may want to look at, like GNUCash, grisbi or HomeBank: all in the repositories.

---

### Post by elliotn on 2010-05-29
If u already have a partition with windows then u could just backup your important files and do a clean install then install office, the OEM wont stop u from doin that as like u said its same pc. Just remember to reinstall ur grub as windows will overwrite it

---

### Post by howefield on 2010-05-29
You are better reading the documentation that came with your PC with regards restoring your installation of Windows.

You are likely to over write grub, so would need to restore that after restoring Windows.

---

### Post by finlost on 2010-05-29
I did downloaded an OEM manual from Lenovo that I need to read regarding using the recovery partition.  I am mostly concerned about MS licensing.  I have legal licenses and OEM disks, but I am still concerned that MS will hose me.  I was hoping for responses from others that have had to nuke their MS installation on caveats to look out for.

I know I will have to reinstall Ubuntu.  I have started to backup fies and used Recordmydesktop to capture my eye candy settings.  Ubuntu One and Dropbox are the cat's pajamas for backing-up files.

QBs doesn't run in Wine.  Intuit is in bed with MS and Adobe.  QBs is the only reason I need a Windows install.  :(

---

### Post by Mark Phelps on 2010-05-29
It's hard to provide a definitive answer because it really varies by every OEM and, in some cases, by specific machines -- but in general, if the OEM licensed your machine using BIOS-locked licensing (which nearly all of them do), then a reinstall will not present a problem -- since it checks the BIOS table to confirm that the license is legit.  Trying to move the license to another machine (which is NOT what you're doing) is when the problems develop.

Office, however, is a different story.  It is not licensed using the BIOS.  If yours came with a license key, you SHOULD be able to reactivate it using that key.  If that doesn't work, there's no point in contacting MS, they'll just tell you to contact the machine vendor.  In that case, you will probably have to contact the machine vendor to see what they recommend regarding re-activation.

---

### Post by BoneKracker on 2010-05-29
Ole hyvä

Back up MBR using dd.
Reinstall Windows (however).
Restore MBR using dd.
Verify dual-boot still working properly.
Boot into Windows and reinstall Office.

Onnea!

---

### Post by finlost on 2010-05-29
Thanks Mr. Phelps.  :cheers:

---

### Post by wilee-nilee on 2010-05-29
You probably know your key to MS Word but here is a key finder if not.
[http://www.magicaljellybean.com/keyfinder/](http://www.magicaljellybean.com/keyfinder/)
I don't think your going to have any problems with the word being activated. And as Mark Phelps posted the OEM is a auto verification.

---

