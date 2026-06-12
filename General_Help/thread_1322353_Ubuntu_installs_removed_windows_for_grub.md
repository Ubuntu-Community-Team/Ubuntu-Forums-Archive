---
title: "Ubuntu installs removed windows for grub"
date: 2009-11-10
forum: General Help
---

### Post by drewsun on 2009-11-10
ok, so i had windows vista installed (64 bit) and dont have the install cd/dvd.
I installed ubuntu with the live cd and selected install side by side and now when my computer loads i can only boot ubuntu and ubuntu has 8gb and 228mb left so windows has to be there, how can i boot from windows and not ubuntu, im thinking of never using ubuntui again it makes me have grief.If i can fix this soon ill reconsiter,what can i do to   even have a option to boot from windows? do i uninstall and if so how do i remove grub aswell

thanks in advanced :)

---

### Post by drewsun on 2009-11-10
> **drewsun said:**
> ok, so i had windows vista installed (64 bit) and dont have the install cd/dvd.
I installed ubuntu with the live cd and selected install side by side and now when my computer loads i can only boot ubuntu and ubuntu has 8gb and 228mb left so windows has to be there, how can i boot from windows and not ubuntu, im thinking of never using ubuntui again it makes me have grief.If i can fix this soon ill reconsiter,what can i do to   even have a option to boot from windows? do i uninstall and if so how do i remove grub aswell

thanks in advanced :)
help soon plz

---

### Post by raymondh on 2009-11-10
which Ubuntu version did you install?  9.04 and previous use GRUB legacy and 9.10 uses GRUB2.  How to edit GRUB to chainload windows will depend on which GRUB version you have.

[This is Herman's site]("http://members.iinet.net/~herman546/index.html").  Scroll midway to access either GRUB or GRUB2 pages.  

Herman's site also has info about supergrub ... have a read at it.

If you want to delete Ubuntu, and since you don't have a Vista install disc to fix the MBR (or put the windows bootloader back ..... also known as fixmbr or fixboot), download this first and burn to a disc BEFORE deleting Ubuntu.

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

You can use gparted from the liveCD (in live session mode) to work on your existing partitions.  Ubuntu has the EXT format by default.  Post back if you need instructions.  For reference, here's the gparted documentation.

[http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)

Lastly, if you do delete Ubuntu, you need to boot into the recovery disc (above) to access a command prompt to FixMbr.

If I may suggest (and since this may be new to you), I would first boot into the liveCD and go live session .... once in live session, go to PLACES to access your personal files in Vista and copy them over to a USB thumb drive or an external HD.  I say this because there are no guarantees whenever an operator works with partitions.

Regards,

---

### Post by drewsun on 2009-11-10
but i can even see were vista is, meaning it shows the linex drives that take up 4 gb but not the other 316gb sugestions?
and how can i downloiad torents on ubuntu?
And i installed ubuntu 9.04

ok, so im downloading the vista recovery disk, then ill burn it then beboot then boot from cd then what should i do?

---

### Post by raymondh on 2009-11-10
Will you try to edit grub (or GRUB2) to chainload windows or will you delete Ubuntu?

Which ubuntu version did you install?

Do you still have the liveCD?  Do you have back-ups of your files?

---

### Post by drewsun on 2009-11-10
> **raymondhenson said:**
> Will you try to edit grub (or GRUB2) to chainload windows or will you delete Ubuntu?
Which ubuntu version did you install?

Do you still have the liveCD?  Do you have back-ups of your files?
i was thinking of chaining it like it was ment to be and but whitch will allow me to acsees windows faster?

i have the ubuntu 9.04 cd not the vista as i said, if all else fails i should get windows 7 in a few day/weeks

ubuntu is cool, but does not have the support as windows so i think ill keep ubuntu to :)

---

### Post by raymondh on 2009-11-10
Are you in Ubuntu now?  Access a terminal (applications > accessories) and type

sudo fdisk -l

(that's a small L).  You'll be asked for your password which when you type will be invisible.  Copy and paste back the results in your next post.

A boot-info script will be more thorough.  See my sig below. Once downloaded to your desktop, access a terminal and type

sudo bash ~/Desktop/boot_info_script*.sh

That'll produce a results.txt file.  Paste the results in your next post.  Note, it'll be a long report so highlight it and wrap it in codes.

---

### Post by drewsun on 2009-11-10
> **raymondhenson said:**
> Are you in Ubuntu now?  Access a terminal (applications > accessories) and type

sudo fdisk -l

(that's a small L).  You'll be asked for your password which when you type will be invisible.  Copy and paste back the results in your next post.

A boot-info script will be more thorough.  See my sig below. Once downloaded to your desktop, access a terminal and type

sudo bash ~/Desktop/boot_info_script*.sh

That'll produce a results.txt file.  Paste the results in your next post.  Note, it'll be a long report so highlight it and wrap it in codes.

it says Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9512b8f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37796   303596338+  83  Linux
/dev/sda2           37797       38913     8972302+   5  Extended
/dev/sda5           37797       38261     3735081   82  Linux swap / Solaris
/dev/sda6           38588       38891     2441848+  83  Linux
/dev/sda7           38892       38913      176683+  82  Linux swap / Solaris
/dev/sda8           38262       38565     2441848+  83  Linux
/dev/sda9           38566       38587      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order
drew@drew-ubuntu:~$

boot info wont download?

---

### Post by raymondh on 2009-11-11
Drewsun,

I do not see your windows install.  Vista would have a NTFS format (or even a FAT .. for some windows install) which I do not see listed.  Are you sure you installed side-by-side or did you "use entire disk"?  What version ubuntu did you install?  9.10?  If so, can you access terminal again and update GRUB2.

Basically,  if what your fdisk-l is saying is true ..... we cannot retrieve windows if it is not there. Your HD had a total of 38913 cylinders.  From cylinder 1 to cylinder 38913, it is all linux.

What are the other LINUX installs (sda6 and sda8 )

---

