---
title: "Need help with file permissions"
date: 2011-09-07
forum: General Help
---

### Post by Electrifry on 2011-09-07
I recently switched to Ubuntu after not being able to find the install disk for Windows XP after System32 went corrupt.

The remains of my Windows XP installation is on one hard drive (the original one, has 160GB of space) and Ubuntu is on the other (a 40GB hard drive I cannibalized from another older computer). I want to be able to play all my games that I had on Steam and they are currently residing on the other hard drive. I have installed "PlayOnLinux", and now all I have to do is get Steam (and the games) working. However, Steam.exe and all the other executables in the steam folder aren't allowed to execute.

I did do some research, and tried changing the file permissions to make them executable in the file properties using the GUI, but they still aren't executable. I have tried using this command to do it, but it seems to have no affect:

sudo chmod ugo+rwx -R /media/62980034980008ED/Program_Files/Steam
I know that that is the right path, but it's not actually doing anything.

I definitely can't reinstall everything on the hard drive with Ubuntu, there isn't enough space.

Any ideas on what I should do?

Thanks in advance...

---

### Post by claracc on 2011-09-07
Windows .exe files don't run in ubuntu as  .deb files don't run in windows.

You need to install wine (it is in the repositories)  in ubuntu and inside wine some .exe files from windows can run.

This is a link [http://wiki.winehq.org/](http://wiki.winehq.org/) where you can obtain some information from wine.

Sorry, forgot about wine, I haven noticed that you said you had installed playonlinux.  Perhaps the games you have are not supported by playonlinux.

---

### Post by Rob_H on 2011-09-07
> **Electrifry said:**
> 
Any ideas on what I should do?

Thanks in advance...

If you spend a lot of time playing Windows games, you may be disappointed with the experience on Ubuntu. Although Wine makes it possible to play some games, many suffer glitches of one kind or another under Linux. At least that's been my experience.

My advice as a gamer would be to look harder for your Windows XP install CD and dual-boot Windows and Ubuntu.

---

### Post by Electrifry on 2011-09-07
> **claracc said:**
> Sorry, forgot about wine, I haven noticed that you said you had installed playonlinux.  Perhaps the games you have are not supported by playonlinux.

I'll be playing TF2, L4D2, Killing Floor, Audiosurf and maybe some Synergy.

Speaking of using playonlinux, am I supposed to use the install button in PlayOnLinux to install my games or would I just be able to install them from within steam?

Should I just give up on trying to use the game files I had from before I installed Ubuntu? If so, is there something I could do to perhaps use my larger hard drive for all the data storage for the games? I don't want my boot disk to become too crowded.

[QUOTE=Rob_H]If you spend a lot of time playing Windows games, you may be  disappointed with the experience on Ubuntu. Although Wine makes it  possible to play some games, many suffer glitches of one kind or another  under Linux. At least that's been my experience.

My advice as a gamer would be to look harder for your Windows XP install CD and dual-boot Windows and Ubuntu.     [/QUOTE]

I am fully aware that playing Windows games on Ubuntu will be horrible. However, the install CD must have landed on the Kitchen Table of Losing Stuff, and is therefore a lost cause.

Do both operating systems have to be in working order to do a dual boot? Cause I still have yet to delete the remnants of Windows XP.

---

### Post by oldfred on 2011-09-07
You can do a lot of repairs of XP from Linux. Chkdsk is about the only thing you cannot do and that is often essential. But you can use any Windows repairCD to run Chkdsk. I recently used a Win7 repair USB to run chkdsk on my XP install.

If files are still missing you can do this to copy from CD to C:\:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
Where [CDDrive] is location of cd or D: etc.
or:
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 

A discussion about the Bootcfg command and its uses fix boot.ini
[http://support.microsoft.com/kb/291980](http://support.microsoft.com/kb/291980)
[http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm)


How to fix XP when the boot files are missing & info on windows in logical partitions-  meierfra.
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
missing boot files meieifra - post 10
[http://ubuntuforums.org/showthread.php?t=1241394](http://ubuntuforums.org/showthread.php?t=1241394)

---

### Post by Electrifry on 2011-09-07
> **oldfred said:**
> 
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 


Well I can boot into Ubuntu, but when I try to mount the drive that has Windows on it I get an error...

Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

However I can mount the part of the drive that isn't on the Windows partition. (There's a 90GB partition with all my games on it and a 70GB partition with Windows, the first one works and the latter doesn't.)


Is it safe to assume that I just won't be able to run any of the games I had installed before I got Ubuntu? Am I going to have to reinstall them through PlayOnLinux?

---

### Post by oldfred on 2011-09-07
I think that is pretty much saying you need chkdsk. Ubuntu will not mount a NTFS partition that needs chkdsk to prevent further damage that chkdsk may not be able to fix. You may be able to make minor repairs with ntfsfix from Ubuntu but that sets chkdsk flag and then Ubuntu for sure will not mount it. But you can force mount if you have to to get some data. But best to run chkdsk. Know anyone with Windows to use a Windows repairCD?

---

### Post by Electrifry on 2011-09-07
No one I know even has a windows installation disk. The new fad around here is buying a laptop with Windows pre-installed with no installation disk...

---

### Post by oldfred on 2011-09-07
If someone has Windows & you can provide a CD or Flash.

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by Electrifry on 2011-09-07
Oh cool I didn't know you could do that...

Well we do have a bunch of blank DVDs conveniently lying around.

Thanks for the help.

---

