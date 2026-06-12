---
title: "change windows boot manager timeout=0"
date: 2010-12-13
forum: General Help
---

### Post by botelhorui on 2010-12-13
Hello ubunto forum, i recently started using ubuntu and its very cool.

I installed last ubuntu from windows 7 using wubi and it worked great, i am writing this from ubuntu. The problem is I changed the timeout to 0 on windows 7 startup options as well default operating system to ubuntu, so now i cannot boot to windows because the windows 7 boot manager just flashes and goes directly to the grub boot manager and even if try to choose windows 7 on grub boot manager it only goes back to windows 7 boot manager and the same thing happens.

I have no DVD drive and i only have a 1Gigabyte USB PEN.

I already searched insanely on ubuntu forums, used unebooting, tried creating a windows 7 startup disk with unebooting, tried formating USB PEN with GLParted and choosing FAT32, ex3, NTSF as well with boot flag and then copying files to usb, wich didnt work. I tried to fix it with SUPER GRUB DISK didnt work too....


SO please i beg for help :(...

Is there anyway i can change this little timeout setting from windows 7 boot partition (yes i really learned something) so i can boot to windows 7? By whatever method, it can be from within ubuntu or using a 1Gb pen?

I know it can only be changed using bcdedit.exe but not even with wine it worked.

Thank you in advance, i tried my best :(

---

### Post by pastalavista on 2010-12-13
Install Startup-Manager from the Software Center or in terminal```
sudo apt-get install startupmanager
```Run it from the System>>Administration menu or Alt+F2 'startupmanager'

---

### Post by botelhorui on 2010-12-13
thank you but that doesnt allow me to change windows 7 loader timeout. that is for grub boot manager ONLY. I want to edit windows boot manager.

---

### Post by stinkeye on 2010-12-13
I dont know if W7 is the same but in XP you just edit the boot.ini
eg
```
[boot loader]
redirect=usebiossettings
redirectbaudrate=
[COLOR="Purple"]timeout=15[/COLOR]
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="XP" /noexecute=optin /fastdetect /usepmtimer
multi(0)disk(0)rdisk(1)partition(2)\WINDOWS="GAMES" /noexecute=optin /fastdetect /usepmtimer
```

---

### Post by pastalavista on 2010-12-13
> **botelhorui said:**
> thank you but that doesnt allow me to change windows 7 loader timeout. that is for grub boot manager ONLY. I want to edit windows boot manager.
On my PC, at the first splash screen, there are options for selecting the BIOS setup (F2) and the boot loader (F12). It might be different on yours.  I don't understand why, when you select Windows with Grub, it sends you right back to Grub. You might need to use a Windows install CD to repair it, in which case, you'd need to setup Grub again after fixing Windows MBR.

---

### Post by mortani on 2011-01-04
Hello!
I just found this thread after searching for a while (it seems most people have trouble with the grub loader, not the windows one!), and i have the exact same problem!
Is there no way to change the timeout of the windows loader? I don't have a dvd drive so i won't be able to use recovery discs either (not that i'm sure it would help)!

Regards
Mortan

---

### Post by hawkmage on 2011-01-04
Windows 7 doesn't use the same boot.ini that Vista did.  It uses a "Boot Configuration Database" also know as the BCD.  You can manipulate this using the bcdedit command.  

If you have the Windows 7 Rescue Disk boot from it.  Do not choose to restore anything. Open command window and run "bcdedit" this will list the BCD info.  In the "Windoes Boot Manger" section I assume that the timeout value is 0.  To change it to 30 seconds you would run "bcdedit /timeout 30".  Exit the command window and reboot.  You should have the boot menu.

---

### Post by mortani on 2011-01-06
> **hawkmage said:**
> Windows 7 doesn't use the same boot.ini that Vista did.  It uses a "Boot Configuration Database" also know as the BCD.  You can manipulate this using the bcdedit command.  

If you have the Windows 7 Rescue Disk boot from it.  Do not choose to restore anything. Open command window and run "bcdedit" this will list the BCD info.  In the "Windoes Boot Manger" section I assume that the timeout value is 0.  To change it to 30 seconds you would run "bcdedit /timeout 30".  Exit the command window and reboot.  You should have the boot menu.

Correct, the boot.ini is definately not applicable with windows 7.

I searched frantically for some sort of keypress, or maybe an application to change the settings for this boot manager, but no such luck :/

I ended up using the method hawkmage described, but if course i didn't have a dvd drive. Fortunately i had a spare computer running win 7 as well, so i was able to follow the procedure for making a usb disc bootable, found on the neosmart website.

However, since my laptop is 32 bit, and not 64, as my desktop (gah!), i needed to find a recovery image elsewhere. I can report that torrent given on the same page:
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
is not functional (for me anyway). 
I was able to find a boot image elsewhere (*cough* piratebay), and the above method worked for setting the timeout of the bootloader.

I can't believe i spent this many hours fixing such a small amount of data :O

Booting into windows however, i encountered a BSOD, followed by a restart :confused:
I ran the startup repair utility from the recovery disc, to no avail. I do not know what to do now.. I would not have expected that the so-called simple windows installer for ubuntu would wreck my windows installation this much!

Update:
btw i did of course boot into windows once after installing ubuntu, that was when i changed my bootloader timeout. Could it have been anything i did inside ubuntu that screwed up my windows install? The only things i remember was mounting the windows drive and opening up a few files, i also tried assigning my dropbox folder to the same as my windows dropbox folder. Could that lead to some kind of corruption?

---

### Post by bcbc on 2011-01-06
> **mortani said:**
> Correct, the boot.ini is definately not applicable with windows 7.

I searched frantically for some sort of keypress, or maybe an application to change the settings for this boot manager, but no such luck :/

I ended up using the method hawkmage described, but if course i didn't have a dvd drive. Fortunately i had a spare computer running win 7 as well, so i was able to follow the procedure for making a usb disc bootable, found on the neosmart website.

However, since my laptop is 32 bit, and not 64, as my desktop (gah!), i needed to find a recovery image elsewhere. I can report that torrent given on the same page:
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
is not functional (for me anyway). 
I was able to find a boot image elsewhere (*cough* piratebay), and the above method worked for setting the timeout of the bootloader.

I can't believe i spent this many hours fixing such a small amount of data :O

Booting into windows however, i encountered a BSOD, followed by a restart :confused:
I ran the startup repair utility from the recovery disc, to no avail. I do not know what to do now.. I would not have expected that the so-called simple windows installer for ubuntu would wreck my windows installation this much!
I thought holding down F8 during boot causes the menu to be offered regardless of timeout setting.

In any case, this is hardly a Wubi problem. Windows allowed you to select a zero timeout, while your default OS was not Windows. It seems like a warning from Windows - Are you sure? - would be reasonable.

Grub has an override that prevents you from hiding the grub menu if it detects multiple OS's. You can override this with a few code mods, but you still have the option of holding down SHIFT to make it appear.

---

### Post by peedeeramone on 2011-01-06
there are a lot of potential reasons for your bsod, some of which could be ubuntu, and others being windows. i probably wouldnt have run that startup corrector thing if i were you. those tend to delete things and overwrite them with defaults, but being that you dont want windows defaults that may have botched it. granted im not entirely sure what you actually did so im mostly talking out of my a$$. i would try the f8 trick, i want to say it worked for older versions of windows but im not sure of that either.

good luck

---

### Post by bcbc on 2011-01-06
I've been reading around - seems like there might be a bug and that the F8 key doesn't work when the timeout is zero.

However, it's strange that editing the timeout to > zero is giving a bsod. That indicates to me some other issue.

---

### Post by mortani on 2011-01-07
Yes indeed i tried holding down a variety of buttons when trying to boot into windows, f8 included, but it skipped the windows boot just the same. When i started the recovery disk, i did not run any sort of recovery, only the command prompt, followed by changing the timeout of the loader with the method mentioned before. After that, i got the bsod, so i thought the windows startup recovery would help, but i have had no progress, also tried restoring the system from a restore point, that didn't help either.

I do realize that the problem could very well be caused by windows, but i think the most likely explanation would be something i could have done to my windows installation, from within ubuntu. Are there any sort of "recover my windows partition" applications to check the partition?

---

### Post by mortani on 2011-01-14
Is anyone still reading this thread? I would really like to find a solution to getting my windows partition up and running again. Would it help if i moved my WUBI installation to its own linux partition, using LVPM? ([http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)).
I have a hard time believing that i'm the only one getting this problem, since i got this bug allmost immediately after installing ubuntu with WUBI, but i haven't been able to find anyone else with the same problem (yet).

---

### Post by bcbc on 2011-01-14
Someone got it fixed here [http://ubuntuforums.org/showpost.php?p=10349941&postcount=13](http://ubuntuforums.org/showpost.php?p=10349941&postcount=13) (bootrec.exe /fixmgr)

But it did remove the Ubuntu entries - so you'll have to add them back manually afterwards.

PS don't use LVPM it doesn't support installs after 8.04. You can use this instead: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

EDIT: since you already tried repairing Windows and are getting a BSOD this fix may be too late for you.

---

### Post by mortani on 2011-01-15
> **bcbc said:**
> Someone got it fixed here [http://ubuntuforums.org/showpost.php?p=10349941&postcount=13](http://ubuntuforums.org/showpost.php?p=10349941&postcount=13) (bootrec.exe /fixmgr)

But it did remove the Ubuntu entries - so you'll have to add them back manually afterwards.

PS don't use LVPM it doesn't support installs after 8.04. You can use this instead: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

EDIT: since you already tried repairing Windows and are getting a BSOD this fix may be too late for you.

Hi, thanks, i ran that from the windows recovery console, and it didn't help :/ I guess the only fix will be a complete wipe of my system drive, followed by re-installation of everything :S

---

