---
title: "GRUB error"
date: 2010-10-02
forum: General Help
---

### Post by jay0613 on 2010-10-02
Hey,
On my XP desktop I have Ubuntu installed through Wubi. Earlier today I switched to Ubuntu and ran the update manager. It downloaded a bunch of things. Towards the end it said that Grub was being updated and asked which hard drive to install grub to. It said if you're not sure, then pick all of them. I picked my "C" and "F" hard drive. Then restarted the computer and now I get a Grub error. Right now I am running off of the live CD. Since I can access my hard drive in my Ubuntu folder it has an icon to uninstall wubi. I want to know should I uninstall wubi? Or would it mess up? I haven't done it yet. Thanks

---

### Post by Rubi1200 on 2010-10-02
This is a known bug:
> **[COLOR=Red][SIZE=3]Important Note to Wubi (Windows Ubuntu) Users: Grub Update results in "No Such Disk":[/SIZE][/COLOR] **
A late July 2010 Grub 2 update is causing a "**[COLOR=DarkRed]no such disk[/COLOR]**"  error for some users of WUBI, resulting in an unbootable system. If the  system doesn't display the original Windows menu, the most likely cause  of the failure is that Grub 2 was installed in the MBR and/or on the  Windows partition. To correct this, restore the Windows bootloader using  this link:
[How to restore the Ubuntu/XP/Vista/7 bootloader]("http://ubuntuforums.org/showthread.php?t=1014708")

Whether the failure is due to improper user selections or Grub 2's  failure to recognize a Wubi install, it has been reported in the  following bug and users can review it for status updates and recovery  options when they become available:
[https://bugs.launchpad.net/wubi/+bug/610898](https://bugs.launchpad.net/wubi/+bug/610898)
Source:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

See also here:
> Upgrading Wubi systems from 10.04 LTS is known to fail, and is not recommended at this time.
[https://wiki.ubuntu.com/MaverickMeerkat/TechnicalOverview#Known%20issues](https://wiki.ubuntu.com/MaverickMeerkat/TechnicalOverview#Known%20issues)

---

### Post by jay0613 on 2010-10-02
I just tried that for my "C" and "F" hard drive, and after I did the sudo grub-install I get this for sda1

error: cannot seek '/dev/sdc' .
error: cannot seek '/dev/sdd' .
error: cannot seek '/dev/sdc' .
error: cannot seek '/dev/sdd' .
error: cannot seek '/dev/sdc' .
error: cannot seek '/dev/sdd' .

Then I got the same thing for sdb1.

So would uninstalling wubi fix my problems? Or make them worse?

Thanks

---

### Post by jay0613 on 2010-10-02
bump

---

### Post by bcbc on 2010-10-02
wubi installs need the windows bootloader. running the wubi uninstaller from live cd is impossible and won't help.

To install a windows equivalent bootloader from live cd:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

```
ignore warnings that refer to booting linux.

This works the same as the windows bootloader, but if you prefer you can install the windows bootloader using a windows repair disk
xp - "fixmbr"
vista/7 - "bootrec.exe /fixmbr"

---

### Post by jay0613 on 2010-10-02
After I did the sudo apt-get install lilo it said something about installing lilo for the first time and I had to run sdev something, I'm sorry I don't remember what it said and I don't know how to bring it up again. 

Then after I did sudo lilo -M /dev/sda mbr it says "
WARNING: kernel & initrd not found in the root directory (/vmlinuz & /initrd.img)
WARNING: Do NOT reboot or LILO may fail to boot if your kernel+initrd is large.
WARNING: Please read /usr/share/doc/lilo/README.debian

Then it says the Master Boot Record has been updated. Are those the warnings you meant for me to ignore?

---

### Post by bcbc on 2010-10-02
> **jay0613 said:**
> After I did the sudo apt-get install lilo it said something about installing lilo for the first time and I had to run sdev something, I'm sorry I don't remember what it said and I don't know how to bring it up again. 

Then after I did sudo lilo -M /dev/sda mbr it says "
WARNING: kernel & initrd not found in the root directory (/vmlinuz & /initrd.img)
WARNING: Do NOT reboot or LILO may fail to boot if your kernel+initrd is large.
WARNING: Please read /usr/share/doc/lilo/README.debian

Then it says the Master Boot Record has been updated. Are those the warnings you meant for me to ignore?

Yes. the "kernel & initrd" are for booting linux.

---

### Post by jay0613 on 2010-10-02
That worked. Thank you for your help.

One more thing, I just uninstalled Ubuntu and restarted my computer and it went straight to Windows XP like normal. Now in my "C" and "F" hard drive I have a folder that is called boot. Then inside that folder it is called grub. Then inside that are a bunch of .mod files. Do I need those folders or can I delete them?

---

### Post by bcbc on 2010-10-02
> **jay0613 said:**
> That worked. Thank you for your help.

One more thing, I just uninstalled Ubuntu and restarted my computer and it went straight to Windows XP like normal. Now in my "C" and "F" hard drive I have a folder that is called boot. Then inside that folder it is called grub. Then inside that are a bunch of .mod files. Do I need those folders or can I delete them?

You're welcome. Glad you got everything sorted.
Those boot folders sound like artifacts left over from grub - therefore probably safe to delete.

---

