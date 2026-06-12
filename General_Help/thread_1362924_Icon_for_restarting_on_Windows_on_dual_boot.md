---
title: "Icon for restarting on Windows on dual boot?"
date: 2009-12-23
forum: General Help
---

### Post by AvatarGG on 2009-12-23
Hello,

Some time ago, I found a link on these forums to a tutorial that explained how to create an icon on your Ubuntu desktop to restart the computer and having Grub load Windows automatically (without having to manually select it). It also explained how to do the same on Windows, by the way.

I am unable to find it using the search. Does anyone know where can I find it or how to create the icon I talk about? Any help would be much appreciated.

---

### Post by TetonsGulf on 2009-12-23
I think this is what you want... from [https://help.ubuntu.com/community/SoftwareFromOtherOperatingSystems](https://help.ubuntu.com/community/SoftwareFromOtherOperatingSystems)

Dual-Booting tricks

Switch to Windows shortcut

If you have your computer set up to run two operating systems (you can find more information about this at WindowsDualBoot), you can set up an icon that will switch you into Windows from Ubuntu by following these instructions:

First, we must edit the GRUB menu and see what menu number the entry for Windows is. Run:  gksudo gedit /boot/grub/menu.lst  Warning: Be careful editing this file, making a mistake will potentially make your system un-bootable until you fix it with a LiveCD

Look at this file, after the comments, you should see a line that says ## ## End Default Options ##. The actual menu items are located after this line. Count them, and make a note of where the Windows entry appears. Keep in mind that GRUB starts counting from 0, so don't start at 1. In my case, the entry for Windows is number 5. Note: Be sure to count every entry that has a "title" line, including the one that says Other operating systems: if you have it.

Before we are done with the menu, we must change the default settings and change the Windows entry so that it automatically resets the default to Ubuntu. This will allow us to simply reset the computer from Windows and have Ubuntu load as it normally would.

To do this, look for the line that starts with default, near the beginning of the file. Change it so that it says

```
default saved
```

Warning: RAID users should heed the warning in this file

Next, we must change the line savedefault under the Windows entry to savedefault 0, where 0 is the number of the Ubuntu entry. Your number may be different, but likely not. Save the file, close gedit, and move on to the next step.

Now, we need to create a script that will set the default operating system to Windows, and then reset the computer. First, we need to allow normal users to run the grub-set-default and reboot commands, which normally requires sudo. To do this, run  sudo visudo  Add the following lines to the bottom of the file -

```
ALL ALL= NOPASSWD: /usr/sbin/grub-set-default
ALL ALL= NOPASSWD: /sbin/reboot
```

Warning: If visudo complains about syntax errors when you exit the program, do not ignore them! Go back and look at the file and see what went wrong. If you mess up the sudoers file you might not be able to run sudo at all, which you'll need a LiveCD to fix.

WARNING: This will allow any user on your computer to reboot the computer. Normally, any user can use the menus to do this, but if you allow users to remotely connect to your computer you may want to consider the idea that any of them could reset your computer at any time, so this might not be something you want to do.

Now, run gedit reset-to-windows.sh, and put the following lines into it, replacing 5 with the number of the Windows entry in the GRUB menu:

```
sudo grub-set-default 5
sudo reboot

```
Save this file, and make it executable and system-wide by doing the following:

 ```
chmod a+x reset-to-windows.sh
sudo chown root reset-to-windows.sh
sudo mv reset-to-windows.sh /usr/bin
```

Great! Only one last step: right click on the desktop and select Create Launcher. Name this launcher Switch to Windows, and set the command to /usr/bin/reset-to-windows.sh. Select an icon if you'd like.

Now, you can use this icon to reset the computer, and it will come back up in the Windows operating system. Later, if I can get my hibernate to work, I will show you how to use this technique to hibernate Ubuntu instead of resetting.

---

### Post by AvatarGG on 2009-12-24
Thank you very much! That was I was looking for.

---

