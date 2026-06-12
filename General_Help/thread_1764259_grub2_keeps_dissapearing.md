---
title: "grub2 keeps dissapearing"
date: 2011-05-21
forum: General Help
---

### Post by thedukesays on 2011-05-21
Had a search on the forums and can't find anything exactly like my issue.

Dual booting with W7.  Every so often grub or my MBR disappears.   I get a black screen with a cursor on boot.  I can use the live CD and repair grub and everything is fine. But then it disappears again.  I've tried a fresh install of ubuntu 11.04 this works as it reinstalled grub2 and Ubuntu.  But again after about 4 or 5 restarts of the PC grub2 or the Mbr vanishes and I have to reinstall.

Its driving me mad.  The only thing I can think is something is corrupting the MBR.  I've checked it for a virus and also any errors using MBRchecker from W7 and it was fine.

---

### Post by oldfred on 2011-05-21
Do you have any DRM software in Windows? Some of that writes into the first few sectors after the MBR to hide serial numbers or other data. But grub2 has part of its boot in that same area. Grub2 has been modified to avoid the sector with flexnet. Also some windows virus checkers think grub is a boot sector virus.

Writes to MBR area-----------------------------------
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
[http://linux.slashdot.org/story/10/08/28/2112208/Some-Windows-Apps-Make-GRUB-2-Unbootable](http://linux.slashdot.org/story/10/08/28/2112208/Some-Windows-Apps-Make-GRUB-2-Unbootable)
[http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html]("http://www.chiark.greenend.org.uk/ucgi/%7Ecjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html")
In Windows 7, had to remove Windows 7 DataSafe.
HP ProtectTools, Dell Recovery, flexnet and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct or Uninstall Dell DataSafe issues with MBR
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)
h

---

### Post by thedukesays on 2011-05-21
Thanks oldfred.  I'll check this out.  AVG in windows did update and it seems to be since that update I've been having this issues.  Although its not telling me its found anything.

---

### Post by linuxinstalledfromhdd on 2011-05-21
BitDefender


 First you need to get a [free scanner key]("http://www.bitdefender.com/site/Products/ScannerLicense/") here via email. Once received, navigate to the appropriate .DEB package (64bit or 32bit) and download.


 32-bit Ubuntu:
 wget [http://download.bitdefender.com/SMB/Workstation_Security_and_Management/BitDefender_Antivirus_Scanner_for_Unices/Unix/Current/EN_FR_BR_RO/Linux/BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run](http://download.bitdefender.com/SMB/Workstation_Security_and_Management/BitDefender_Antivirus_Scanner_for_Unices/Unix/Current/EN_FR_BR_RO/Linux/BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run) && sudo sh BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run 64-bit Ubuntu:
 wget [http://download.bitdefender.com/SMB/Workstation_Security_and_Management/BitDefender_Antivirus_Scanner_for_Unices/Unix/Current/EN_FR_BR_RO/Linux/BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run](http://download.bitdefender.com/SMB/Workstation_Security_and_Management/BitDefender_Antivirus_Scanner_for_Unices/Unix/Current/EN_FR_BR_RO/Linux/BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run) && sudo sh BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run

---

### Post by thedukesays on 2011-05-30
Thanks for all the posts. 

I've deleted AVG on W7 and now using avast.  Fingers crossed its not deleted grub2 so appears this was the issue after all.

Thanks again for your help.

---

