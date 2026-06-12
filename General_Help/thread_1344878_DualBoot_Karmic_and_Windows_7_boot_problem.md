---
title: "DualBoot Karmic and Windows 7 boot problem"
date: 2009-12-03
forum: General Help
---

### Post by adrian05 on 2009-12-03
Hy.
I've installed Windows 7 (in C: drive (sda1))last month on my laptop and then I installed Ubuntu Karmic with WUBI(E: drive (sda3)).I had two option on boot: Windows and Linux(and if i was going for linux the grub was doing its job well). Everything worked great until yesterday, when i decided to reinstall windows 7. I reinstalled windows, no problems, but the option to boot into Ubuntu disapeared. I hoped it should be something easy to do to recover, sience everything worked just fine before.
I tried some things but nothing helped:
1. mounted sda3 on /win
   mounted /win/ubuntu/disks/root.disk to /vdisk
Then I tried:
   sudo grub-install --root-directory=/vdisk
Here it tels me to specify the modules manualy.
Can anyone help me pls? Thank you.

---

### Post by pastalavista on 2009-12-03
When you install Ubuntu with the Wubi installer, the Ubuntu "partition" is actually just a folder in Windows. I would think that re-installing Windows would mean you'd also need to re-install everything else you installed in Windows, including Ubuntu. If you want Ubuntu to persist, you would be better served with a standard dual-boot setup.

---

### Post by QIII on 2009-12-03
pastalavista is entirely correct.

Wubi installs Ubuntu in a Windows folder that has "virtual partitions" for Ubuntu.  It allows Ubuntu to be run in a "loop device" essentially as if it were installed on its own device (with a few provisos and caveats).

When you reinstalled Windows, you destroyed that folder and Ubuntu along with it.

I concur with the advice to do a proper dual-boot install.

---

### Post by adrian05 on 2009-12-03
Thank you very much guys. I reinstalled windows, but sience it was installed in another partition, the ubuntu files(from root.disk) were not erased. But I managed to make it work. Grub was ok too. I renamed the old ubuntu folder to E:\ubuntu1, installed Ubuntu again on E:\ubuntu. Then i rebooted, let ubuntu install and entered windows again. I deleted the new ubuntu instalation folder, and renamed back the old ubuntu1 folder to E:ubuntu. Then I copied wubildr and wubildr.mbr from E:/ubuntu/winboot to my C: (where is the Vista bootloader installed) and replaced the old ones.
Somehow, Ubuntu didn't make a hash check or something and just worked.
Later I found that using bcdedit I could make a new entry into vista's bootloader. 
Thanks again. Bye

---

