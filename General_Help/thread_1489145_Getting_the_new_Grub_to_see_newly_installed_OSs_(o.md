---
title: "Getting the new Grub to see newly installed OSs (on other HDD) and setting defaults?"
date: 2010-05-20
forum: General Help
---

### Post by markjs on 2010-05-20
So I just had gotten to know the old Grub a little when I upgraded Ubuntu to find the new Grub, which I barely understand at all!  My use of Ubuntu is mostly for learning and recreational as my bread and butter is working on people's messed up Windoze systems, since that is where the work is.  Naturally I've got to use and work with Windoze to know how to fix it and keep it running cleanly, but Ubuntu was the first Linux I found that to me seems like something that could be potentially be embraced by "non geeks".  I have as yet to get anyone to try it; it is all about keeping up with the Joneses and having what they have.  There is also that old pervasive myth that you get what you pay for, which with computers, I find the opposite is so often true, that the good stuff is mostly free.

In any case I dabble a lot with Ubuntu for fun and personal knowledge, but since I put 10 on I had only Windoze 7 on my machine at the time.  It picked it up and I purposely installed Grub to my Ubuntu drive (I used separate physical drives, so that if you removed the Ubuntu drive, 7 would boot as if Grub and Linux were never on the machine and that is the way I like it since I tinker a lot.).

The trouble is that I need Win 7 to be the default and I don't know how to do that with Grub 2 (is it 2?)  I used to know with the old one.  Also, I have since added a 160GB PATA drive with XP on it, since so much of the help I am asked to give over the phone is with XP and I am not one who can talk others through things unless I can see it myself.  Plus there are some things I do that just plain old work best with XP.  So I also need to add XP to my boot menu, and it is, on a separate physical drive as well, and I wanted that the same too; if you made the XP drive the priority boot device it will boot XP as if it was the only OS on the machine.

What the ideal for me would be is to have the Ubuntu drive as the one it boots from, Windoze 7 to be the default OS, and XP to be on the menu too.  I have been able in all of the time with Ubuntu and Linux in general to find precious little info on how to do things with multiple physical drives.  It seems to be taken for granted that the only way people multi boot is with separate partitions on a single physical drive, and that it is a radical and unthinkable idea that anyone would want a separate physical drive for another OS, so I would really appreciate the help!

---

### Post by dcstar on 2010-05-20
> **markjs said:**
> So I just had gotten to know the old Grub a little when I upgraded Ubuntu to find the new Grub, which I barely understand at all!  My use of Ubuntu is mostly for learning and recreational as my bread and butter is working on people's messed up Windoze systems, since that is where the work is.  Naturally I've got to use and work with Windoze to know how to fix it and keep it running cleanly, but Ubuntu was the first Linux I found that to me seems like something that could be potentially be embraced by "non geeks".  I have as yet to get anyone to try it; it is all about keeping up with the Joneses and having what they have.  There is also that old pervasive myth that you get what you pay for, which with computers, I find the opposite is so often true, that the good stuff is mostly free.

In any case I dabble a lot with Ubuntu for fun and personal knowledge, but since I put 10 on I had only Windoze 7 on my machine at the time.  It picked it up and I purposely installed Grub to my Ubuntu drive (I used separate physical drives, so that if you removed the Ubuntu drive, 7 would boot as if Grub and Linux were never on the machine and that is the way I like it since I tinker a lot.).

The trouble is that I need Win 7 to be the default and I don't know how to do that with Grub 2 (is it 2?)  I used to know with the old one.  Also, I have since added a 160GB PATA drive with XP on it, since so much of the help I am asked to give over the phone is with XP and I am not one who can talk others through things unless I can see it myself.  Plus there are some things I do that just plain old work best with XP.  So I also need to add XP to my boot menu, and it is, on a separate physical drive as well, and I wanted that the same too; if you made the XP drive the priority boot device it will boot XP as if it was the only OS on the machine.

What the ideal for me would be is to have the Ubuntu drive as the one it boots from, Windoze 7 to be the default OS, and XP to be on the menu too.  I have been able in all of the time with Ubuntu and Linux in general to find precious little info on how to do things with multiple physical drives.  It seems to be taken for granted that the only way people multi boot is with separate partitions on a single physical drive, and that it is a radical and unthinkable idea that anyone would want a separate physical drive for another OS, so I would really appreciate the help!

The Grub2 HOWTOs explain all of these things - search them out.

---

### Post by markjs on 2010-05-20
Thanks, that was way easier than in Grub 1!

[Grub2 How-to]("https://wiki.ubuntu.com/Grub2")

For anyone else who is looking for answers.

---

