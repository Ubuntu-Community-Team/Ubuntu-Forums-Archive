---
title: "Using LiveCD to access data on a Hard Disc"
date: 2011-03-24
forum: General Help
---

### Post by Exzackly on 2011-03-24
My computer has 2 separate drives. The first drive has Windows Vista and I purchased a second drive for a Ubuntu install. I reinstalled Windows which obviously re-wrote the MBR, preventing me from booting Ubuntu. I intend to reinstall Ubuntu eventually but I need to access (copy) several files that are on the Ubuntu Drive. I figured I could just boot the Ubuntu LiveCD, mount the primary drive, and copy the files there. When I try to do so, I am told that the files do not belong to me and therefor I cannot copy or move them. Obviously for security reasons that makes plenty of sense but I didn't consider that. How might I get the LiveCD to allow me access to those files which are all contained in 1 folder? I tried shouting, "I PROMISE NOT TO USE WINDOWS. UBUNTU IS THE ONE FOR ME," but Ubuntu didn't fall for it. There must be someway for me to convince Ubuntu that my actions are completely harmless and that he'll always have a home on any HD of mine.

I'm not exactly a newbie but it has been a long time (8-10yrs) since I've used any flavor of Linux. Thank you in advance for your time.

Zack:D

EDIT: Or if there is a way to boot the drive with Ubuntu without actually changing the MBR, that would work too. I was told that the Windows boot loader could boot Linux but I don't think I want to use that boot loader. I intend to use Grub2 to load both but right now I just need to access that folder.

---

### Post by timgood on 2011-03-24
If you re-install grub you won't need to re-install Ubuntu and your existing Ubuntu installation will work. So you could recover your files. Info on re-installing grub [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

Hope this helps.

---

### Post by tredegar on 2011-03-24
From the live cd, run this command in a terminal
**gksudo nautilus**
That'll give you a file manager running as root, which will let you move the files, to an external disk for example.

---

### Post by QLee on 2011-03-24
[QUOTE=Exzackly]...
I'm not exactly a newbie but it has been a long time (8-10yrs) since I've used any flavor of Linux. 
...[/QUOTE]
However, you'll remember enough to understand. When you've booted the live CD, open up a terminal window and enter the command , gksudo nautilus, that will open the file manager with root permissions and you will remember that root can grab those files. Should be easy to grab the whole folder you want. Now, we could also do this from the command line but the GUI will probably be easier for you. Just remember to consider that any file that needs to retain Linux permissions can not keep them on a filesystem that doesn't understand them, like a Windows volume or a CD. If it's your home you're meaning and you don't have another Linux filesystem to keep it on you'll have to make a tarball first. You probably remember most of this stuff anyway.

---

### Post by Exzackly on 2011-03-24
I found this document and read it.  I couldn't be certain if the instructions worked for me though.  I have 2 separate hard drives.  Windows is on the primary drive and Ubuntu is on the newly installed second drive. The MBR is on the primary drive. GRUB2 would have been installed on the primary drive even though I allowed Ubuntu to use all of the second drive, correct? Some of those instructions were confusing me when considering that.  I don't really need to reinstall GRUB2 just to get access to some files do I?  If so, I suppose I will but I was just certain there was an easier way.

Thanks,
Zack

---

### Post by QLee on 2011-03-24
[QUOTE=Exzackly]I found this document and read it.  I couldn't be certain if the instructions worked for me though.  I have 2 separate hard drives.  Windows is on the primary drive and Ubuntu is on the newly installed second drive. [/QUOTE]
Yes, if you used the correct "boot directory" on sdb but I think that advice is assuming that your Ubuntu installation is still intact (very likely it is Windows shouldn't have bothered with it) and would allow you to skip getting those files. A GRUB to MBR installation doesn't require modifying the Ubuntu installation so that wouldn't be overwritten. Still a good idea to have a backup of important files though and that's what I would do in your situation.

[QUOTE=Exzackly]The MBR is on the primary drive. GRUB2 would have been installed on the primary drive even though I allowed Ubuntu to use all of the second drive, correct? [/QUOTE]
Probably, if you did not specify a different device I believe default is sda for GRUB to MBR installation. If it worked after installation before Windows install took back the MBR then that was it.

---

