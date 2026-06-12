---
title: "Ubuntu boot problem"
date: 2012-02-08
forum: General Help
---

### Post by Marko1223 on 2012-02-08
I ve got an dell 500 laptop and i got ubuntu 11.10.I am trying to get back to windows.I ve got the windows cd and it wont boot from it ok.I am trying to delete the paritions.So i put my ubuntu 11.10 cd so i coud boot from it and then from it delete the partitions.I go in go to boot and it won t boot from the cd it just goes foward to desktop?

What shoud i do?Can i just go in from ubuntu and disk utility and delete the partitions?


PS:sorry for bad english

---

### Post by Mark Phelps on 2012-02-08
IF you're not going to be able to boot from the Windows CD, then how are you going to reinstall it -- even if you do manage to erase your drive first?

Not booting from CD can be any of the following problems:
1) Damaged or scratched CD -- unlikely here because you tried different CDs
2) Defective CD reader -- likely because BOTH CDs won't work
3) Dirty laser lens in the CD drive -- easily fixed by using one of the lens cleaner tools.  This is also likely if your CD drive is several years old and has been used a lot.
4) Boot device selection not set properly -- you can check this because, if it IS set properly, you should see a line of text at the top of the screen saying something like "press any key ...".  If you don't see that, your BIOS is not set to boot from the CD drive.

---

### Post by Marko1223 on 2012-02-08
> **Mark Phelps said:**
> IF you're not going to be able to boot from the Windows CD, then how are you going to reinstall it -- even if you do manage to erase your drive first?

Not booting from CD can be any of the following problems:
1) Damaged or scratched CD -- unlikely here because you tried different CDs
2) Defective CD reader -- likely because BOTH CDs won't work
3) Dirty laser lens in the CD drive -- easily fixed by using one of the lens cleaner tools.  This is also likely if your CD drive is several years old and has been used a lot.
4) Boot device selection not set properly -- you can check this because, if it IS set properly, you should see a line of text at the top of the screen saying something like "press any key ...".  If you don't see that, your BIOS is not set to boot from the CD drive.



Umm about the second...when i get into ubuntu how can i  "read" the cd-s that means it s not defective?
4. it goes like this diskette drive
internal hdd
usb
cd dvd
onboard inc (no number on this one) 

i tryed to shut everything of except cd dvd and i think it says no boot device (i think so)

---

### Post by Marko1223 on 2012-02-08
anyone?

---

### Post by Mark Phelps on 2012-02-08
> **Marko1223 said:**
> Umm about the second...when i get into ubuntu how can i  "read" the cd-s that means it s not defective?
If you can read the CD in ANOTHER PC, then the CD itself is not defective.  If this CD driver can not read ANY CDs -- then the CD drive hardware is likely to be bad.

> 4. it goes like this diskette drive
internal hdd
usb
cd dvd
onboard inc (no number on this one) 

To boot fron CD by default, you need the CD DVD to be at the TOP of the list.

Also, regarding my first comment above, see if another PC can BOOT from the CD, not just read it.

If no PC can boot from the CD, then how did you create the CD?  Did you just copy the ISO file to it? IF so, that will not make it bootable. You need a CD burning program that will burn an IMAGE file (ISO file).  That will create a bootable CD.

---

### Post by Marko1223 on 2012-02-08
> **Mark Phelps said:**
> If you can read the CD in ANOTHER PC, then the CD itself is not defective.  If this CD driver can not read ANY CDs -- then the CD drive hardware is likely to be bad.


To boot fron CD by default, you need the CD DVD to be at the TOP of the list.

Also, regarding my first comment above, see if another PC can BOOT from the CD, not just read it.

If no PC can boot from the CD, then how did you create the CD?  Did you just copy the ISO file to it? IF so, that will not make it bootable. You need a CD burning program that will burn an IMAGE file (ISO file).  That will create a bootable CD.

The cd drive is ok.Ok i will try on another pc.I burned the ISO file to it.The slowest speed,using burnproof.If nothing works what next?

---

### Post by Marko1223 on 2012-02-08
Coud i try a dual boot like with wubi,so i install win beside linux?

---

