---
title: "? Read 2nd Ubuntu disk, copy files to new Ubuntu disk?"
date: 2011-05-13
forum: General Help
---

### Post by omac on 2011-05-13
Hi All,

I'm not sure if this is in the correct section, and I couldn't find a similar situation while searching ....

Situation: Old IDE Hard Disk with Ubuntu 8.04 and data inside slowly breaking down, so I bought a New SATA Hard Disk and installed Ubuntu 10.10 on it, with the intention of transfering files from Old Disk to New Disk.  My old computer has both IDE and SATA slots.

I set the Old IDE 8.04 Disk jumper to slave, so that the New SATA 10.10 Disk boots up.  The old disk is seen in the / directory as "root".

By logging in as "su", I was able to cd to "root", but when I "ls" it, it didn't show anything at all.  I was hoping just to navigate to the different directories and copy the files one by one, but I now don't know how to do that.

QUESTION: What is the best way to copy files from an Ubuntu 8.04 Hard Disk to a newly installed Ubuntu 10.10 Hard Disk?

Thanks. :)

---

### Post by lmarmisa on 2011-05-13
I recommend to use Clonezilla Live:

[http://www.clonezilla.org/clonezilla-live.php](http://www.clonezilla.org/clonezilla-live.php)

Clonezilla will allow you to clone your old IDE disk into your new SATA disk.

Do not worry if your new SATA hard drive is bigger than the old IDE one. You will able to define new partitions or modify the existing ones in the future using GParted.

---

### Post by jocko on 2011-05-13
> **omac said:**
> The old disk is seen in the / directory as "root".

By logging in as "su", I was able to cd to "root", but when I "ls" it, it didn't show anything at all.  I was hoping just to navigate to the different directories and copy the files one by one, but I now don't know how to do that.

QUESTION: What is the best way to copy files from an Ubuntu 8.04 Hard Disk to a newly installed Ubuntu 10.10 Hard Disk?

Thanks. :)
The /root directory is the home directory of the root user. It normally does not contain any visible files or folders (but probably contain a few hidden files and folders).
Why would you try to mount a hard drive in /root? What's wrong with using the dedicated locations for mount points in /mnt or /media?

---

### Post by omac on 2011-05-13
> **jocko said:**
> The /root directory is the home directory of the root user. It normally does not contain any visible files or folders (but probably contain a few hidden files and folders).
Why would you try to mount a hard drive in /root? What's wrong with using the dedicated locations for mount points in /mnt or /media?

Oh, sorry, I didn't mount "root" myself; I just saw it there.  I may be mistaken, and "root" just be a part of the regular directories when ubuntu is installed.

Anyway, I'm a noob with linux.  I can't seem to see the old hard drive in the menu places > computer.

@lmarmisa, thanks for the suggestion, but I was hoping to have a new, fresh install of the later OS, without all the junk from the old one, save for some files I want to copy.

---

### Post by omac on 2011-05-14
Ok, I solved this one.

First off, I was wrong about the old ide 8.04 Ubuntu hard disk in "root"; root is part of the ubuntu directories, and I never noticed it.  My mistake.

On the solution ...

It was a matter of the correct jumper setting and bios setting.

I put the jumper setting of the ide hard disk to "cable select" and put the end of the ide cable to it (I guess that turned it into master).

I then went to the boot priority of the bios, which before would only allow me to choose between CD and old ide hard disk to boot from.  There was another menu option where I could choose which of the 2 hard disks (the ide and the sata) would be Disk #1 to boot from.

I choose the new sata 10.10 ubuntu as disk #1, and I was able to see the old ide 8.04 disk in the menu > places > computer, and copying anything was no problem.

Thanks for the inputs.  I guess my mistake was in the bios and jumper settings, not really an ubutu issue, sorry about that. :)

---

