---
title: "how to boot my windows installation from the other harddisk?"
date: 2011-10-23
forum: General Help
---

### Post by ExcessPhase on 2011-10-23
I installed ubuntu on one harddisk.
When I rebooted there was no boot menu.
Later I was able to get grub2 to work and I got a boot menu, curiously showing me two ubuntu  versions
but no windows installation.
I can still access the NTFS harddisk from within ubuntu.
First:
I'm using computers since 1986 and I already dealt professionally with solaris and LINUX.
Added new harddisks to solaris.
But I'm unable to get my problem resolved.
I searched the web and all the information regarding grub2 is very cryptic.
All I want is to tell the bootmanager that he should provide a menu entry to boot from the other harddisk (sdb1).
This is a sata drive.

Peter

---

### Post by drs305 on 2011-10-23
Have you run "sudo update-grub"?

Do you have os-prober installed:
```
which os-prober
```
If you get no return, install it:
```
sudo apt-get install os-prober
```

Is the 30_os-prober file executable:```

sudo chmod +x /etc/grub.d/30_os-prober
```

Try running this command again:
```
sudo update-grub
```

See if there is now a Windows entry:
```
grep 'menuentry' /boot/grub/grub.cfg
```

If you still don't have the Windows entry, please download and run the 'Boot Info Script' and post the contents of RESULTS.txt.

You can get to the script download page by clicking the "BIS" link in my signature line.

Note about the 2 Ubuntu versions: Each time a new kernel is introduced it is added to the Grub menu. For slightly older Grub versions, the list will continue to grow as kernels are introduced. In the latest version (Grub 1.99) the older kernels are moved to a submenu so the main page list does not expand.

---

### Post by ExcessPhase on 2011-10-23
[QUOTE=drs305;11385887]Have you run "sudo update-grub"?

I was thinking, that I only need to run this after changing some source file.

> Do you have os-prober installed:

yes

```
grep 'menuentry' /boot/grub/grub.cfg
```If you still don't have the Windows entry, please 


peter@ubuntu:~/Desktop$ grep 'menuentry' /boot/grub/grub.cfg
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {
peter@ubuntu:~/Desktop$ 



> download and run the 'Boot Info Script' and post the contents of RESULTS.txt.


see attached


Thanks for the quick help

---

### Post by micael3000 on 2011-10-23
Hello,

Please, run the sudo update-grub, everything should be working just fine... You don't need to change any configuration before doing it. ;)

[]'s.

---

### Post by drs305 on 2011-10-23
Edit: As was mentioned, run update-grub if you haven't already. If that doesn't work...

I am not a Windows guy so I can only provide limited assistance, although I think I know the problem.

The RESULTS.txt shows only the **bold entry** for your Windows boot files:
> /bootmgr /Boot/BCD **/Windows/System32/winload.exe**
Grub is not finding the /bootmgr or /Boot/BCD entries, therefore it is not adding the entry to the Grub menu. The additional files are for Windows 7. If Windows is booting through the original Vista bootloader, the missing files might be slightly different but I know there is more than the single .exe file.

Does Windows boot for you if you set the BIOS to boot sdb first? If not, you will need to repair your Windows installation. I think it's 'fixboot' but you probably know more about it than I do or you can search these forums for that term and you will find more information about repairing the boot files.

Here's one link if Windows won't boot:
[http://ubuntuforums.org/showpost.php?p=10049238&postcount=4]("http://ubuntuforums.org/showpost.php?p=10049238&postcount=4")

---

### Post by ExcessPhase on 2011-10-29
I had to reinstall windows XP to be able to repair windows vista (because it was an upgrade)...
Working now from an USB drive....

---

