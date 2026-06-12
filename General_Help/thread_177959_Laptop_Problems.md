---
title: "Laptop Problems"
date: 2006-05-17
forum: General Help
---

### Post by Last_Hero on 2006-05-17
Right, I got Ubuntu as my first even non-Microsoft OS, downloaded it, burned the ISO and then installed.

But, than I had a Hard Drive partition error and a to format a few of my partitions, including the one Ubuntu was installed on, now when I try to boot XP
I get a Grub Error, Error 22 I think.

Is there anyway to remove GRUB and revert to my original XP boot so I can reinstall Ubuntu on my fixed Hard Disk?

Please say there is as I cannot acces my folders etc through Ubuntu and I really need to finish some work for this Friday.

Thanks for any help.

---

### Post by Sef on 2006-05-17
you could try this from the command line:  fdisk /mbr

that should get your windows up again.


> 22 : No such partition
    This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk.

[http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_13.html]("http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_13.html")

---

### Post by Last_Hero on 2006-05-17
Which command line?

Do I have to load Ubuntu from CD to do that 'cause I don't think you can get a command line in XP before th operating system loads, not like in 95 where you could load DOS on startup.

---

### Post by JoeG on 2006-05-17
Boot up from your XP setup disk.  When setup starts, select the option for recovery console.   From there, you should be able to use the command **fixmbr** to restore the boot record to its pre-Ubuntu state.  Lemme know if that helps.

JoeG

---

### Post by Last_Hero on 2006-05-17
ofcourse, I forgot about my XP disks as it came pre-installed. 

Thanks, gonna try that now.

---

### Post by Last_Hero on 2006-05-17
Seems ACER didn't think to supply me with an XP Setup disk, I got thier Acer Recovery disks, but the only option is Recover. It says it will erase everthing on my first partition, which I assume they mean as the 2gig or so partition that shows up at the top the GNOME partition editor, is that correct, or will I lose all my music, documents etc aswell?

---

### Post by JoeG on 2006-05-17
Yeah, unfortunately, recovery CDs set the hard disk filesystem back to what it was from the factory.  So, you lose everything.   Are you wanting to reinstall Windows, Ubuntu, or set up a dual-boot?

JoeG

---

### Post by Last_Hero on 2006-05-17
I want to either remove GRUB so I can resinstall it along with Ubunto or fix it and then reinstall Ubunto, oh yeah, and my bloody recovery disks dont work.
And now the installer for Ubunto doesnt work either.
This is not my week.

---

### Post by JoeG on 2006-05-17
It almost sounds like your boot order has changed to check the hard drive before the CDROM.  Make sure that the CDROM is prior to the hard drive in your BIOS boot order.

JoeG

Sometimes these things ... ](*,)

---

### Post by obnibolongo on 2006-05-17
[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

The process I prefer is one listed there, but I'll paste it here.

Boot Linux in any way possible: Ubuntu LiveCD, Knoppix LiveCD, Gentoo LiveCD, whatever.

Go to a command line with root access ( sudo -s OR su - [password for Knoppix is empty]).
> # grub

grub> root (hd0,0)           (Specify where your /boot partition resides)
grub> setup (hd0)           (Install GRUB in the MBR)
grub> quit                  (Exit the GRUB shell)

If you wish to start Windows afterwards and for some reason GRUB option won't work, read the link I provided in the beginning of this post.

Good luck for your work.

BTW: next time try a better subject for your post, such as "GRUB fails to load: error 22"; it'll both help people deciding to which topics they know they can answer and people who have the same problem.

---

### Post by Last_Hero on 2006-05-17
I got Ubuntu working now, but now my XP doesn't show up on teh Boot list, bah, I think I saw a fix in a different post though, so thumbs up for that.

I had to specifically to change my boot order to get it to read the CD cause I had HD top ti ever so slightly increase loading times.

"BTW: next time try a better subject for your post, such as "GRUB fails to load: error 22"; it'll both help people deciding to which topics they know they can answer and people who have the same problem."

My problems have changed throughout the day :p

---

