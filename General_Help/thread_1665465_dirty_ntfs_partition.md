---
title: "dirty ntfs partition"
date: 2011-01-12
forum: General Help
---

### Post by Karyo on 2011-01-12
Hi guys,

I have a ntfs data partition declared in fstab that ubuntu can`t mount any more at boot. It works fine if I mount it from cli. 

I have a dual boot kubuntu 10.10/Window 7 on my machine and the partition in question serves a data partition were I keep all my stuff.

Everything was working normally until a few day ago. Now windows give`s me a blue screen at every boot, and linux has trouble mounting this partition at boot.
I tried to fix it from windows recovery mode, I did a chkdsk /F and a system restore but as we all know windows is windows ... and it didn`t work :)

I need some pointing in the right direction since I don`t have much experience with this, and also are there any tools for ntfs debugging on linux?

Thanks

---

### Post by CoreyB. on 2011-01-12
You could try installing ntfsprogs and then run

sudo ntfsfix /dev/drive_name

where drive_name is wherever you have the NTFS partition like sda1 or something.

You can read more at this [Linux man page]("http://linux.die.net/man/8/ntfsfix") or by googling ntfsprogs or ntfsfix.

Good luck.

---

### Post by oldfred on 2011-01-12
ntfsfix only fixes minor issues  & sets the chkdsk flag so when you boot windows it will run chkdsk.

You often have to rerun chkdsk until there are no errors. It does not fix everything on one pass.

Vista/7 CHKDSK
chkdsk [drive] /f /r
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

---

