---
title: "Dual boot Laptop won't boot after partition resize - Grub error"
date: 2012-01-19
forum: General Help
---

### Post by Expert Novice on 2012-01-19
So I resized the partition next to the one where I have ubuntu installed. Using Easeus Partition Master I made it smaller so there was unallocated space between it and the Ubuntu partition with the intention of using it to install programs. When Partition Master tried to reboot all that happened was a black screen appeared with the message ''Grub error, unknown file system... rescue.''

After some googling on my other machine I used a bootable Super GRUB2 disc to boot into Windows and aborted the resize operation so as far as I know there were no actual changes made but when I tried to boot to Ubuntu I got the above error. I used Super GRUB2 again to boot into Ubuntu and tried running sudo update-grub but still get the same message.

Any suggetsions as to what I can try next please?

The machine is  running Windows 7 home premium and Ubuntu 11.10 with kernel 3.2.1 with both systems on separate partitions.

Thanks for reading :)

---

### Post by Expert Novice on 2012-01-19
Well, I managed to get windows to boot normally by using the system repair disc I'd made to get to cmd prompt and used the comand ***BootRec.exe /fixmbr.  ***When I booted the machine it went straight to windows with there was no sign of grub doing anything so I used the install disc to try the solution given [here]("http://ubuntuforums.org/archive/index.php/t-24113.html") but seem to have ended up going through a full install rather than just mending grub. I didn't lose much from the Ubuntu install and it won't take me long to get things back to where they were. All part of the learning process.

---

### Post by DevinMcElheran on 2012-01-19
You didn't happen to change the start of a partition did you? Most partitioning tools have a graphical description of your drive. If you move the front of the partition you've changed the starting sector. This sector is what grub uses to know where to boot from. You can change the tail of your partitions, but the first sector of a partition is a reference point and if changed, when grub look for that sector and finds something unexpected, it'll return an error. So I would say to boot up an Ubuntu live CD, or USB which is significantly faster, and reinstall grub from the terminal. You can find loads of tutorials of how to recover a grub installation. Just try to make sure you use a recent version of Ubuntu as an older version of grub might not support your kernel. I hope that helps.

---

### Post by Expert Novice on 2012-01-19
I made the windows (C) partion smaller creating unallocated space between it and Ubuntus partition. I don't think I moved Ubuntus partition boundaries at all  but that's not to say it didn't happen by mistake. 

Thanks for the suggestion on re installing grub. I'd tried that earlier on and seemed to have succeeded judging from the output in terminal but on booting the same problem persisted. That's when I found the other suggestion to use the cd to repair but I seem to have ended up with a fresh install. I was going to try restoring a backup I'd made a few days ago but the trouble now is that my cursor disappears as soon as the desktop appears 

:-(

---

### Post by DevinMcElheran on 2012-01-19
I don't know how to help with that, I'd say it's an x server problem.

---

