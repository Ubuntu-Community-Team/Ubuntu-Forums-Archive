---
title: "GRUB Help"
date: 2006-05-15
forum: General Help
---

### Post by Sonic5688 on 2006-05-15
How do I remove GRUB from my MBR so that itll automatically load my primary OS?

---

### Post by aysiu on 2006-05-15
You don't have to remove Grub to change the default OS that boots:
[https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS](https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS)

---

### Post by Sonic5688 on 2006-05-15
Im trying to completely remove Linux from this particular machine though.

---

### Post by aysiu on 2006-05-15
Maybe [this link](http://support.microsoft.com/default.aspx?scid=kb;en-us;314458) will help.

---

### Post by Sonic5688 on 2006-05-15
Also, I tried just wiping out Ubuntu completely, but it tries to load GRUB and gives an error, so i need to remove GRUB.

---

### Post by Sonic5688 on 2006-05-15
I already have Windows XP installed on this pc, I just want to remove Linux. And GRUB. Definitly GRUB :) . I dont have an XP install cd anymore though, so i cant use the MBR repair utility on it.

---

### Post by aysiu on 2006-05-15
I'm not sure if it's possible to run the *fixmbr* DOS command without a Windows CD.

---

### Post by Sonic5688 on 2006-05-15
So I'm basically stuck with Linux?

---

### Post by aysiu on 2006-05-15
[QUOTE=Sonic5688]So I'm basically stuck with Linux?[/QUOTE] I just said I'm not sure it can be done. Maybe it can be done, but I don't know how.

If you want, you can uninstall almost all of the Linux packages, shrink the Linux partition down to as small it can get, and then create a FAT32 or NTFS partition out of the remaining space.

Grub will still be there to boot Windows from. If you change Windows to be the default OS and change the timeout to 0 seconds, you won't know the difference.

---

### Post by richbarna on 2006-05-15
Have you got another PC ?
Maybe you can try this ?
Found it at :-
[http://www.kellys-korner-xp.com/xp_haldll_missing.htm]("http://www.kellys-korner-xp.com/xp_haldll_missing.htm")
> REINSTALLING WINDOWS IS NOT AN OPTION. 
 
 Final Solution: 
 
 Removed hard drive from system.
 Added Hard drive to a 2nd WORKING XP PRO System. As Slave on Cable select.
 
 ***(all references to &#8220;D:\&#8221; are the Slave Hard drive damaged windows)***
 
 Booted system and enabled - Explorer\tools\folder options
 
 Display contents of system folders.
 Show Hidden Files and Folders.
 UN-check Hide Protected OS Files.
 
 Go to &#8220;D:\&#8221; open Boot.ini in NOTEPAD, remove the Extra OS&#8217;s added with option 1.
 Close and Save changes to Boot.ini
 
 Go to &#8220;My Computer&#8221; Right click on &#8220;D:\&#8221; select SEARCH &#8220;D:\&#8221;
 
 Search &#8220;All or Part of the File Name&#8221; = &#8220;hal&#8221;
 
 Hal.dll may or may not be found in &#8220;D:\WINDOWS\System32&#8221; either way it&#8217;s no good.
 A working copy of hal.dll WILL be found in &#8220;C:\WINDOWS\ServicePackFiles\i386&#8221;
 COPY THAT FILE &#8220;D:\WINDOWS\ServicePackFiles\i386\hal.dll&#8221;
 And Paste it to &#8220;D:\WINDOWS\System32&#8221; folder; if it asks to overwrite say YES.
 
 You may now un-do the changes made to Explorer\tools\folder options to RE-Hide files.
 Shut Down the computer.
 
 Remove the 2nd Drive and reinstall it to its own tower as Master.
 
 _You should Now be able to boot the computer up as if nothing ever happened._
 
 With the exception that it will prompt you to reinstall some drivers, Just say YES and let it auto detect &#8230;THEY ARE ALREADY THERE. And will setup fine. 
 
 This "FIX" assumes that the computer in question HAS at ther very least service pack1, if not service pack 2.
 
 If these patches have NOT been installed , I dont believe any such Reserve copy of hal.dll will exist on the drive! 


---

### Post by wyo on 2006-05-16
[QUOTE=Sonic5688]So I'm basically stuck with Linux?[/QUOTE]

If you have done a default install of Ubuntu Grub has changed your MBR and the MBR of your Windows installation is lost. But you should be able to do a "recovery" with your Windows CD.

O. Wyss

---

### Post by aysiu on 2006-05-16
[QUOTE=wyo]If you have done a default install of Ubuntu Grub has changed your MBR and the MBR of your Windows installation is lost. But you should be able to do a "recovery" with your Windows CD.

O. Wyss[/QUOTE] I think the point is that Sonic doesn't *have* a Windows CD.

---

### Post by fluid_motion on 2006-05-26
You can try *fdisk mbr* if you can access your WIndows XP DOS prompt, you shouldn't need the XP disc.

---

### Post by ingo on 2006-05-26
fdisk mbr is the command you want, it'll rewrite your mbr to start win. if you cannot get hold of dos commands (cos I never used xp...) try a win98 start diskette

---

