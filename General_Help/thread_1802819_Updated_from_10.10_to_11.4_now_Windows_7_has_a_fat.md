---
title: "Updated from 10.10 to 11.4 now Windows 7 has a fatal Error"
date: 2011-07-12
forum: General Help
---

### Post by bestdarncomputers on 2011-07-12
Like the title says I updated my dual boot Windows 7-Ubuntu 10.10 to 11.4.

The  update seemed to go over without a hitch, except for the few slides of a  power point that I was working on when it rebooted being lost, and my  KildClient not working I can find anything wrong with the Ubuntu side of  things. I was able to access the files on the Windows side of the  partition and all of the files are still here and everything seems to be  working correctly.

When I attempt to boot into windows 7 it will  look like it's going to work then flashes a blue screen with an error,  something like:

A fatal error has occurred, to prevent damage, windows in now shutting down. 0x000001 0x001006e8 

I  REALLY need access back to the Windows side of my laptop, it's where  all of my business programs and data are, and I have billing that needs  to get done if I ever expect to get paid.

Running a Toshiba SatelliteC655, let me know what other information you need.

---

### Post by seawolf167 on 2011-07-12
Welcome to the forums!

I'm not sure what that error refers to or how to fix it specifically, but my thoughts would be to reinstall the Windows partition boot record and see if that allows Windows to boot. If not, try a full Windows MBR installation, then if that works, reinstall Grub and then update it to check for the Windows loader.

To reinstall the Windows 7 partition boot record, insert your Windows 7 cd, boot off of it and select to enter the recovery console. Once there, type in the following command then restart your computer and see if the Windows loader Grub menu option allows Windows to boot ok.

```
BootRec.exe /FixBoot
```

---

### Post by bestdarncomputers on 2011-07-12
That command didn't work, something about not having access or something.  I've run the windows repair a half dozen times and fixed every error that it can find. Still get the same error of not being able to boot, I updated the Grub and no change, any other ideas?

---

### Post by seawolf167 on 2011-07-12
What is the specific error you are getting? 

Does this command work?

```
[bootsect.exe]("http://technet.microsoft.com/en-us/library/dd744577%28WS.10%29.aspx") /nt60 c:
```Have you tried the check disk using the following command?

```
[chkdsk]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true") /f
```

---

