---
title: "Windows gurus needed"
date: 2010-02-21
forum: General Help
---

### Post by MooPi on 2010-02-21
I've devised a recovery system using Linux for Windows recovery system. Basically a usb drive loaded with a minimal Linux install with gparted, clamav, file mamager,ntfstools . The host machine will have a partition just for recovery backup consisiting of Ext3 file system, and enough space to backup a clean Windows folder. My question is what is required for a system backup. Should I just copy the Windows system folder or do I need others. The premise is if the system becomes corrupted i can just drop in the backup Windows folder and scan for viruses to clean and disinfect, or use the clean backup to replace infected system files
I've been using Linux for so long I've lost some of my skills on the Windows side and need advice as to what would be necessary. So what folders would be needed for a complete or adequate backup?

---

### Post by vlamnire on 2010-02-21
I'm using Windows Vista but you should have a back up of the Boot folder, Windows folder, and the autoexec.bat, bootmgr, BOOTSECT.BAK, config.sys, IO.SYS, MSDOS.SYS, and pagefile.sys files.  If you want to keep all the programs you installed I would back up the Program Files folder to and perhaps the User folder.  If your in Windows you do not see most if not all the files I listed but Linux can.  That's what I think I've never done something like you want to do here before.  But there is a few Windows programs you can use to make an exact copy of the drive.  I personally use Acronis True Image.

---

### Post by MooPi on 2010-02-21
This is a desperation move by me. I have friends that I'm their tech support and am constantly cleaning and reloading Windows systems. Some if not all of these friends can't afford an expensive solution so this is my work around as an inexpensive alternative. I'm looking just for system essential files.

---

### Post by vlamnire on 2010-02-21
I am support for many of my friends also, just backup what I've listed there then and it should be fine.  You should copy all of the folders and files you see when accessing the Windows drive with Linux and copy it with Windows to another hard drive and try to boot from that hard drive.

---

### Post by MooPi on 2010-02-21
> **vlamnire said:**
> I am support for many of my friends also, just backup what I've listed there then and it should be fine.  You should copy all of the folders and files you see when accessing the Windows drive with Linux and copy it with Windows to another hard drive and try to boot from that hard drive.
Doesn't sound like a workable system ? The copy to the another drive and boot part.

---

### Post by lisati on 2010-02-21
I recall seeing a "windows recovery disc" being mentioned previously in the forums, but don't have a link to hand at the moment.

---

### Post by Ozymandias_117 on 2010-02-21
I would suggest avast4workstation over clamav [http://www.avast.com/linux-home-edition#tab4]("http://www.avast.com/linux-home-edition#tab4")

---

### Post by MooPi on 2010-02-21
I use Avast home edition and install it on most system reloads but I will stick with Clamav because now I've got two AV applications working. One installed on the windows side and Clamav on the Linux side. Besides space is at a premium on a 4 gig usb drive.

---

