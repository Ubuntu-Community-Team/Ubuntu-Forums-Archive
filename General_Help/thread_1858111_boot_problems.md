---
title: "boot problems"
date: 2011-10-11
forum: General Help
---

### Post by luke.w.pc on 2011-10-11
when i boot my laptop with ubuntu 11.04 it loads on to grub and i have to select ubuntu then it waits with a bit flashing in the top left corner then it goes to "your disk drives are being checked for errors ....." and if i press c to cancel it just then it just goes black and freezes but if i wait for it to complete it takes ages to complete but then if i go to manual recovery it goes to consol and i dont know what to do but skip mounting or fix errors it will just freeze any help greatly apprieciated.

---

### Post by Mark Phelps on 2011-10-12
If it's doing the disk check on every reboot, then there are filesystem problems that it's trying to correct.  Cancelling out leaves the problems in place, such that it will try again on the next reboot.

You need to let it finish the filesystem check.  If it then continues to do checks on subsequent boots, that's a strong indication of a failing drive -- and you then need to back off your files before it crashes.

---

### Post by luke.w.pc on 2011-10-12
i have left it till the end of the check but if i tell it to try to fix the errors it will just say "continue to wait ........." 
and if i leave it it wont do any thing. and also i wouldn't think it would be a drive error because the laptop is only about 1 1/2 years old and hasn't ever had any drive problems exept always memory checking but i was wondering weather there was a way to repair the operating system files or somthing like using the ubuntu live disk like in windows xp, to fix it?

---

### Post by Mark Phelps on 2011-10-13
Laptops tend to be HARD on drives.  Not only due they run HOT (due to the heat from other components and lack of good ventilation) they also tend not to fare well with constant jostling, especially if you carry the laptop around with it turned on.  So, it's not impossible that a laptop hard drive can be failing after only 1 1/2 years of use.

What you can do to check the drive is go to the website of the drive manufacturer and see if they have a downloadable utility that will check the health of the drive.

Unfortunatly, most of those tend to run only in MS Windows, but some do allow you to create a bootable CD containing the utility.

Also, some BIOSs include hardware monitoring.  For drives, this is often referred to as S.M.A.R.T.  If your laptop BIOS supports that, you should look at the page and see what it reports.

---

