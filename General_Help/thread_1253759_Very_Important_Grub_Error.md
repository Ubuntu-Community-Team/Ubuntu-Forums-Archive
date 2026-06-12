---
title: "Very Important Grub Error"
date: 2009-08-30
forum: General Help
---

### Post by Natpjohnson on 2009-08-30
Hello,
I've already checked everywhere on the internet but it seems no one has done what stupid me did.  I have two separate hard drives on my laptop.  I had windows vista on the first and ubuntu on the second.  I decided that i needed more space for windows so i deleted the volume on the second harddrive that ubuntu was on.  Then i just partitioned a new volume that windows could use.  When i restarted my computer i got the grub 1.5 stage error 17.  All the posts i have come across are those of people who got the error but still have ubuntu on their computer.  However in my case i deleted ubuntu.  My uncle (an IT guy) doesn't know what to do.  I heard something about switching the boot order of the drives and I did that but i still get the error.  My laptop is a Toshiba A205 Satellite.  I would really appreciate any help given, and thank you.

---

### Post by bowhuntr09 on 2009-08-30
try fdisk /mbr

---

### Post by Natpjohnson on 2009-08-30
where do i type that?

---

### Post by StuartN on 2009-08-30
> **Natpjohnson said:**
> where do i type that?

I guess that the previous poster meant booting from a live CD and typing that in a terminal. RescueCD and the like have extra tools for recovery, but a regular Ubuntu CD should be enough to resurrect the system.

---

### Post by Natpjohnson on 2009-08-30
> **bowhuntr09 said:**
> try fdisk /mbr
heres what I did tell me if i did it wrong:
I stuck in an ubuntu live disk and chose try without any changes.  I then opened up a terminal and typed fdisk /mbr.  I then got "unable to open /mbr".

Im also fairly sure my second harddrive letter is k if that matters.  when i type kdisk /mbr it says it can't find that command.

---

### Post by vernonrj on 2009-08-30
If you have a Vista Recovery Disk or the Installation Disk you can follow the steps on here

[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

---

### Post by louieb on 2009-08-30
lots of people have deleted / reformatted  there Linux install without knowing that unless they put the Window boot loader back in the MBR 1st - the computer will look for the GRUB boot loader, its not there and the compter does not boot.

 Anyway lots of way to fix too. Heres a pretty good list. [IDBS Remove Replace Uninstal Grub]("http://members.iinet.net.au/%7Eherman546/p18.html")

---

