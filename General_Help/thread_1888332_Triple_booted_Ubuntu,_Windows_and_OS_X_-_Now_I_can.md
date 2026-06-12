---
title: "Triple booted Ubuntu, Windows and OS X - Now I can't boot Windows?"
date: 2011-11-29
forum: General Help
---

### Post by mortenmoulder on 2011-11-29
Hello Ubuntu forums, and thanks for reading my thread.

I installed Ubuntu after having perfectly installed OS X and Windows 7, I now can't boot up my Windows 7.

I am sitting on Ubuntu at the moment, but when I press on the Windows 7 (Booter) in Grub startup menu, it just goes black, and then loads Grub Loader menu again...


I tried Google a lot, but I can't seem to solve this weird thing.


When I installed Ubuntu, I chose to install it Side-by-side with Windows, so I guess I have to make the partition active, or I have to make Grub know windows loader is there somewhere, or something...


Anyone know what to do? :)


EDIT: I should also say that I tried with "sudo grub" and then do the root (hd0,0) and setup (hd0) but that didn't work.
I tried a lot of root (hd0,1), hd0,2... and so on, but it keep saying "Cannot mount selected partition".

---

### Post by evilbrent on 2011-11-29
have you been through the Grub manual page?

---

### Post by mortenmoulder on 2011-11-29
> **evilbrent said:**
> have you been through the Grub manual page?

A bit, but it makes no sense.

---

### Post by Mark Phelps on 2011-11-29
> **mortenmoulder said:**
> When I installed Ubuntu, I chose to install it Side-by-side with Windows ..

Allowing the Ubuntu installer to shrink a Win7 OS partition sometimes ends up with a corrupted Win7 OS partition -- rendering it unbootable in the process.

You can try using the Boot-Repair utility to restore the Win7 Boot:

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

If that doesn't work, let us know because, since you most probably did NOT create a Win7 Repair CD while Win7 was still working, you will have to go to a site and PURCHASE a Win7 Repair CD image, download it, burn it to CD -- and use that to repair Win7.

---

### Post by mortenmoulder on 2011-11-29
> **Mark Phelps said:**
> Allowing the Ubuntu installer to shrink a Win7 OS partition sometimes ends up with a corrupted Win7 OS partition -- rendering it unbootable in the process.

You can try using the Boot-Repair utility to restore the Win7 Boot:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If that doesn't work, let us know because, since you most probably did NOT create a Win7 Repair CD while Win7 was still working, you will have to go to a site and PURCHASE a Win7 Repair CD image, download it, burn it to CD -- and use that to repair Win7.

Thanks for your reply!
I ran the program, and I pressed the recommended one, and it was a success.

But when I boot up now, I press Esc, and only Linux (4 versions) show up, and a chainloader and some more option, but not my OS X or Windows partition.

Otherwise the install was a success. - What do I do now to add my Windows and OS X to the menu?

---

### Post by mortenmoulder on 2011-11-29
Should I try to "Recover MBR" and then Recover the MBR for: ???

or Partition startup by the MBR: ???
I can choose between:
sda1 (Windows 7)
sda2
sda3
sda1 (Windows 7)
sda2
sda3.... What should I do?

---

### Post by Mark Phelps on 2011-11-30
OK, since you can boot into Ubuntu, then open a terminal there and enter "sudo update-grub".  That will regenerate the GRUB menu and SHOULD add an entry for Windows.

Can't help you witn OSX, don't use it.

---

