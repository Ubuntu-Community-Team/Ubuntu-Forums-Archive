---
title: "No option to uninstall Ubuntu?"
date: 2010-06-02
forum: General Help
---

### Post by d4rin on 2010-06-02
I installed Ubuntu 10.04 on my second HD with a thumbdrive image using this program:

Universal-USB-Installer-v1.5.8, And I have Windows 7 installed on my main HD.

I would like to uninstall Ubuntu from my second HD so I can see/use it again with Windows 7 for backing things up.

When I load off the thumbdrive I see no uninstall options, there is a repair mode but I didn't see 'uninstall'.

I would like to remove it from my second HD, and I would like the bootloader back to normal after it's uninstalled.

Any ideas guys?

NOTE: I cannot uninstall via add/remove programs because I did not install it on the same HD as Windows 7.

And making this .reg key doesn't do anything.

REGEDIT4

[-HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\Wubi]

---

### Post by sgage on 2010-06-02
Assuming that you've let Ubuntu install grub on the MBR, just use your Windows disc to restore the MBR to the Windows boot loader. Then boot into Windows and use Disk Manager to reformat the Linux partition to ntfs. No "uninstall" necessary.

---

### Post by WorMzy on 2010-06-02
How did you install Ubuntu? If you booted from the thumbdrive and installed it on it's own partition, then you can't "uninstall" it, just as you can't "uninstall" Windows. You can, however, simply delete the partition from any partition editing software. Ubuntu's default is gparted, but to delete Ubuntu's partition, you'll need to boot Ubuntu from the live thumbdrive, then run gparted.

If, on the other hand, you installed Ubuntu while booted into Windows, then I believe you can remove it by rerunning the installer. In that scenario, it's just treated by Windows as a program, so you can always uninstall it by using add/remove programs.

---

