---
title: "Bootloader fails!"
date: 2011-12-28
forum: General Help
---

### Post by ka9mot on 2011-12-28
Windows 7 Machine. Regardless of what I try, when installing Ubuntu in a dual boot configuration, my Boot loader fails.

This is the only machine I am having this problem with.

Please help!

Asus MB
2G 400MHz Ram
P4 2.8GHz Hyperthreading
Windows on First IDE HD
Back-up and file storage on second IDE Drive
All of my Music and Ubuntu 11.10 on 3rd SATA Drive. 50G set aside for Ubuntu.
Windows 7 Home Premium.

She's an old girl, but she works good!

---

### Post by cbanakis on 2011-12-28
I had a similar problem in the past, but it may not be relevant in your situation. (Dual Boot)

I was not dual booting, but my problem was a direct result of having multiple hard drives, like you do.

It seems that Ubuntu likes to install the boot-loader on whatever hard drive is 1st in your bios, regardless of what hard drive you choose to have the OS itself installed on.

Try having your bios boot to the other 2 drives, and see if anything changes.

What happened with me, was I had my storage drive plugged into sata0, and my OS drive plugged into sata1.

During Ubuntu setup, I selected my OS drive, but then Ubuntu would not boot unless I set the storage drive as the boot drive in bios.

Let me know if that helps.

---

### Post by ka9mot on 2011-12-28
It will not install the boot loader on any drive. While installing Ubuntu, at the end when it says it is installing Boot Loader, then it pops up a dialog box that says installation of the boot loader failed.

---

### Post by cbanakis on 2011-12-28
ah, I thought you meant it would not boot after install.
Did not realize you were saying it would not install.

Maybe the drive is not the correct format?
I am assuming you are not formatting the drive during install, because that would involve erasing your music.

That could be the problem though.

Not sure.

I guess we'll see what others have to say on the subject.

---

### Post by ka9mot on 2011-12-28
It has me stumped. This machine has always been like that. Even with only my first drive in it and it was running XP. Which makes me wonder if maybe there isn't some king of utility protecting the boot sector of this drive......

Thanks for your help cbanakis!

---

### Post by ka9mot on 2011-12-28
I forgot to mention that the last time I tried to install Ubuntu on the same drive as Winders, I had to re-install Windows. 

I've successfully installed other versions of Linux in a dual boot configuration (Mandrake, Red Hat, Lindows (remember that one?), Marv's Hamshack Hack (That was a Knopix Distro for Ham Radio Operators). 
All of these old ones were more difficult then I wanted to deal with which is why I love Ubuntu.... It is easy for dummies like me.

---

