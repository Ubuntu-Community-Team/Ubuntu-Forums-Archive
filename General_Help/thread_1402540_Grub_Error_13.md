---
title: "Grub Error 13"
date: 2010-02-09
forum: General Help
---

### Post by eppes on 2010-02-09
I have a Sony VAIO VPCW115XG. I have a dual-boot of XP SP3 (Home Edition) and Ubuntu 9.04 (April'09 release). My Windows XP is not booting and Grub Loader is showing:

**Error 13**
[B]Invalid or unsupported executable format

[/B]and nothing else is shown. On Ubuntu the corresponding drive is not visible. The result of typing *sudo fdisk -lu* in Terminal shows the following result

Device                Boot             Start                        End                Blocks     Id  System
/dev/sda2           *        9766912    250806171   120519630      7  HPFS/NTFS

and also other drives. And when I tried to manually mount it using the command:
*sudo mkdir /media/xp*
*sudo  mount -t ntfs /dev/sda2 /media/xp*
then it showed the error:
*/dev/sda2 doesn't seem to have a valid NTFS.*

I'm sure I didn't do anything fishy in Windows Xp. Please help me, I urgently need to extract some file which is only in XP. Hence even if I lose my XP, I need to find some way to recover that file (on the main drive where XP is loaded).

---

### Post by mörgæs on 2010-02-10
You will get loads of hits in Google when searching for this error message, for example

[http://ubuntuforums.org/showthread.php?t=282545](http://ubuntuforums.org/showthread.php?t=282545)

---

