---
title: "Deleted Ubuntu partition, can't boot Windows"
date: 2011-05-20
forum: General Help
---

### Post by alonewestand on 2011-05-20
Don't have the Windows install disk.  Tried to reinstall Ubuntu from the disk but it hangs at a black screen with a _.  If there's no disk it boots into grub rescue>.

Edit: Also tried Super Grub Disk.  Like the Ubuntu disk, computer doesn't seem to even acknowledge its existence and still boots into the "no such partition grub rescue>" command prompt screen.

Edit2: Going to try Rescatux, I guess.

Edit 3: I'm able to boot from the Ubuntu disk now, but it won't let me create a partition to install Ubuntu like it did before, offering only to replace Windows or to "try ubuntu".

Edit 4: The following [how-to]("http://ubuntuforums.org/archive/index.php/t-622828.html") does not work in my terminal.  I get the result "Unable to locate package ms-sys" even after enabling community-maintained open source software (universe) and updating.

---

### Post by jerrrys on 2011-05-20
is this a upgrade to 11o4 ?

---

### Post by alonewestand on 2011-05-20
I had 11.04 installed I was trying to delete it and just boot back into Windows.

---

### Post by jerrrys on 2011-05-20
from what i know (i do not run windows) you need that xp cd to restore xp boot menu, but you no got.

so maybe re-installation of ubuntu is necessary. this will once again give you grub and windows should boot.  11o4 installation is different from my 10o4 so can't help you there.  maybe a win-person will come along and help.  myself, i think i would just install 10o4 (just because i know it will work) and get windows back and then make yourself a windows cd and then wipe ubuntu

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=remove+ubuntu&as_qdr=all&sa=Google+Search&lang=en#851](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=remove+ubuntu&as_qdr=all&sa=Google+Search&lang=en#851)

---

### Post by oldfred on 2011-05-20
Lilo's boot loader in the MBR works just like windows in that it looks for a partition with the boot flag and jumps to that partition to continue to boot.

per meierfra. mbr.bin may cause problems in some cases better to use lilo
Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing testdisk with Synaptic.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

If you are keeping windows you should have a windows repair CD.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Repair Disc at the following links:
Windows Vista Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not auto repair XP (they create the boot sectors differently) but can run chkdsk on any NTFS partition.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

