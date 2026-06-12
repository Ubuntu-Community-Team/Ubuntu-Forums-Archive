---
title: "CHKDSK is stuck"
date: 2011-08-09
forum: General Help
---

### Post by SugoiDesu on 2011-08-09
I'm trying to install Ubuntu 11.04 on my sister's Windows 7 machine.
It tells me to run CHKDSK /R in order to resume the installation, but it stucks at level 4.
What should I do?

---

### Post by blueridgedog on 2011-08-09
How big is the drive?

Did chkdsk with any options show any errors?

---

### Post by SugoiDesu on 2011-08-09
No, it didn't.
This drive has free 238GB.

---

### Post by psusi on 2011-08-09
Wait.. it takes a long time.

---

### Post by SugoiDesu on 2011-08-09
It freezes for 2 hours on 23 percent, at the exact number of files.

---

### Post by psusi on 2011-08-09
It sounds like your drive is dieing.  Boot from the Ubuntu livecd, and open the disk utility and look at the drive's SMART status.

---

### Post by SugoiDesu on 2011-08-09
Dying? What do you mean?!
Ummm... How tdo I boot Ubuntu from a LiveCD? (Sorry for being a nubb)

---

### Post by william.smith3 on 2011-08-09
Do you get this error when your booting the LiveCD, or have you already installed the Operating System? The Ubuntu disc that you burned.

---

### Post by SugoiDesu on 2011-08-09
This is a WUBI problem...

---

### Post by Mark Phelps on 2011-08-09
Sounds like the Win7 filesystem may be corrupted -- which is NOT a Wubi problem, per se.

The more you mess with this, the greater the risk of damaging the Win7 filesystem so that it won't boot anymore.

So, the NEXT thing you should do is boot into Win7, use the Backup feature to create and burn a Win7 Repair CD.  At least with this, if you do encounter further Win7 problems, you have the means to boot into a Windows environment to do repairs.

---

### Post by psusi on 2011-08-09
> **SugoiDesu said:**
> Dying? What do you mean?!
Ummm... How tdo I boot Ubuntu from a LiveCD? (Sorry for being a nubb)

Put the CD in the drive, and tell your bios to boot from it.  This is usually done with Del, F2, or F12 to either get a one time boot device menu, or go into the bios settings so you can change the boot order.

---

### Post by SugoiDesu on 2011-08-10
> **Mark Phelps said:**
> Sounds like the Win7 filesystem may be corrupted -- which is NOT a Wubi problem, per se.

The more you mess with this, the greater the risk of damaging the Win7 filesystem so that it won't boot anymore.

So, the NEXT thing you should do is boot into Win7, use the Backup feature to create and burn a Win7 Repair CD.  At least with this, if you do encounter further Win7 problems, you have the means to boot into a Windows environment to do repairs.

What should I do next?
Thanks!

---

### Post by Mark Phelps on 2011-08-10
> **SugoiDesu said:**
> What should I do next?
Thanks!

Did you burn the Win7 Repair CD?  If so, boot with it, choose the option to Repair your Computer, and run Startup Repair.  Do this three times -- that's right, three times.

If all goes well, you will be able to boot back into Win7.

If it fails, especially if it says it can't find a Win7 installation on your PC, Win7 is gone, or corrupted so bad it can't be repaired.

At that point, your only option (presuming you want Win7 back) would be to either Restore the PC to it's original factory state, or reinstall Win7 from an Installation DVD.

---

