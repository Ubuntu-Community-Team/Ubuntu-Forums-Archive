---
title: "Problems with GRUB loading Window's 7"
date: 2010-05-24
forum: General Help
---

### Post by baddoght on 2010-05-24
Hi all,

I reviewed the posts regarding problems loading Windows after the 10.04 upgrade.  I told my father (who is a very basic user) to take the defaults during the upgrade from 9.10 to 10.04.  Now he is unable to boot his Windows 7 drive.  

I did some reading of the forums and I followed the instructions from below:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

When I get to the bottom, the Sixth screen of the **testdisk** screen is saying to rebuild, not backup.  

In my grub.cfg, I suspect I simply need to edit the following line in red:

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'  <---- ([COLOR=Red]CHANGE to **hd0,2**[/COLOR])
    search --no-floppy --fs-uuid --set fe94832b9482e58d
    chainloader +1

Here is the result of HD's from the testdisk:
[I]Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63

     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0  32 33    12 223 19     204800 [System Reserved]
 2 P HPFS - NTFS             12 223 20 60801  47 46  976564224 [Win 7 Local Disk][/I]

Am I on the correct path, and is there an easy way to edit the grub.cfg file?

Please advise.

Thanks.

Bad[DOG]/H.T.
Ken

---

### Post by wilee-nilee on 2010-05-24
So if you can get this script posted it will give the information needed to fix this. Post it in code tags by highlighting the text in the reply click on the # in the panel then submit.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Now are you doing this direct on the computer or you 3rd partying this. Also any additional fixes run after the script that don't work may need the script run again to see whats going on.

---

### Post by baddoght on 2010-05-31
Hi Wilee -
 
My appologies in not responding, my mother-in-law passed away.  I will try and get by my dad's in the next day or so to address your request.
 
Bad[DOG]/H.T.

---

### Post by oldfred on 2010-05-31
Sorry to hear about your mother-in-law.

Please to [COLOR=Red]not[/COLOR] modify this 
set root='(hd0,1)'  <---- ([COLOR=Black]CHANGE to **hd0,2**[/COLOR])

Your windows boots thru/from a system reserved/boot/recovery partition. The * or boot flag is the active partition in windows which tells it where to boot from. The entry is correct.

But to be able to see what may be the problem post the boot-info script that wilee-nilee gave you a link to.

---

