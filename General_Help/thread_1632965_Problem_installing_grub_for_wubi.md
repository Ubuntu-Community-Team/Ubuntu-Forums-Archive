---
title: "Problem installing grub for wubi"
date: 2010-11-28
forum: General Help
---

### Post by stablum on 2010-11-28
Hello everyone,

This is actually a cross-post from the mailing list ubuntu-user; since I didn't receive answer from there, I am posting here.

I have been using wubi for three months since now.
Yesterday the windows bootloader got damaged and I thought that it
could have been a nice idea to replace it with grub on the /dev/sda
device.
I used a ubuntu live cd for this purpose.

Actually I managed to install grub with the following commands:

mount -o loop /media/a/ubuntu/disks/root.disk /media/u
grub-install --root-directory=/media/u/ /dev/sda

where /media/a is the mountpoint of the /dev/sda3 partition with windows.

you can read my grub.cfg file at the following page:
[http://nopaste.info/10654e8d03.html](http://nopaste.info/10654e8d03.html)

The grub.cfg file is located in the ubuntu filesystem image file that
is stored on the windows partition.

Unfortunately at boot grub looks for a device that has the uuid of the
ubuntu filesystem image.
It does not find it and fails to load the grub menu, letting me with a
"grub rescue" prompt.

How can I tell grub-install to configure grub to look into that file
image to search for grub.cfg?

Please let me know if you need other info to solve this problem.

Thank you very much for the attention,
regards,
Francesco Stablum

---

### Post by sikander3786 on 2010-11-28
Grub can't take control while Ubuntu is installed using Wubi, inside Windows.

Restore your Windows bootloader from the Windows disc.

---

### Post by stablum on 2010-11-28
Thank you very much for the quick reply.

Unfortunately I do not have any windows disk. This is a factory windows installation for the laptop. However I downloaded that "Windows 7 Repair Disk" that allowed me to reinstall the windows boot loader.

Unfortunately this boot loader reinstallation did not take into account wubi. To make things worse Windows 7 is still unable to load correctly due to some obscure corrupt files (I have details if needed, but I don't think it's the case to include them here).

The file boot.ini has actually disappeared; probably due to the various automatic repair attempts.

I still have a Ubuntu live cd that I can use to try to fix this mess.

Do you have any suggestion? Pointers to useful documentation?

thank you very much,
Francesco

---

### Post by stablum on 2010-11-28
I have another question: is the grub bootloader of wubi installed directly inside the filesystem image?

---

### Post by sikander3786 on 2010-11-28
Regarding Wubi, see this.

[http://ubuntuforums.org/showpost.php?p=10159040&postcount=5](http://ubuntuforums.org/showpost.php?p=10159040&postcount=5)

Despite a Wubi install of Ubuntu, the bootloader in the MBR of your HDD is the Windows Bootloader which chainloads Wubi Ubuntu bootloader and boots it.

How did you try Windows 7 bootloader rapair? Using the GUI tool or the command? If used the GUI, you need to try that at least 3 times and then you might get Windows back.

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

[http://technet.microsoft.com/en-us/magazine/ee851681.aspx](http://technet.microsoft.com/en-us/magazine/ee851681.aspx)

---

