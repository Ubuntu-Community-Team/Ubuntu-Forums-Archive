---
title: "Removing GRUB."
date: 2009-07-09
forum: General Help
---

### Post by hurst21uk on 2009-07-09
Basically, I install Ubuntu on a USB HDD. I thought that the installation wouldn't touch my Boot manager on the main computer, but I was wrong.

All I wanted was to be able to boot from the USB HDD when it was connected. But if I disconnect it now, Grub tries to load, then I get an error.

So basically my question is this, how can I remove Grub and just have my pc boot to vista? I only want to be able to boot Ubuntu when I attach the USB HDD and change the boot settings in the BIOS.

Any help appreciated!

---

### Post by lindsay7 on 2009-07-09
One way is to reinstall the mbr to your computer using windows. You will need the windows install disk or a recovery disk or super grub. That will over write the grub on your hard drive. Then you can address the boot up of your usb install.

Here is the info on this,

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

You get to the command line with repair option and type bootrec.exe and the type bootrec /fixBoot.

If you do not have the windows install disk for vista I can give you a site to download a recovery disk.

This is where you can get it,

[http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/](http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/)

---

### Post by synapsys on 2009-07-09
Just for future reference, on the last step before installing files, you must hit the 'advanced' button to change where grub installs. It defaults to 'hd0' which is your primary hard drive and that WILL overwrite your mbr.

---

### Post by hurst21uk on 2009-07-10
> **synapsys said:**
> Just for future reference, on the last step before installing files, you must hit the 'advanced' button to change where grub installs. It defaults to 'hd0' which is your primary hard drive and that WILL overwrite your mbr.

I looked at that bit too, just though I'd leave it alone!

Thanks for the help anyways, I'll let you know how I go on.

---

### Post by hurst21uk on 2009-07-11
I downloaded the recovery disk as my Vista installation disc did not have the repair option. I used the bootrec /FixMbr and that removed GRUB! So thanks! 

I then reinstalled Ubuntu and then installed GRUB on the USB HDD, so all is fine now,

Thanks for the help!

---

