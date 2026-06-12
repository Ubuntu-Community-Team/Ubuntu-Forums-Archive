---
title: "Grub rescue/no partition found"
date: 2011-08-11
forum: General Help
---

### Post by Carne1590 on 2011-08-11
Help!  I am NEW to Ubuntu.  A friend gave me Ubuntu 9-10 and I have been using it in my netbook for some time. Bthe other day we did an update and now a black screen is up and states:
Error: no such partition
Grub rescue>_
I am operating dual O'S with Windows XP and Ubuntu
The only thing I have been able to do after searching hours on the Internet is the following:
When I type set it gives me the following information:
Prefix=(hd0,5)/boot/grub
Root=hd0,5
Grub rescue>_

I understand that the hard drive is 0 meaning the only one I have and 5 means the location of the grub in the partition.

Other than that I can get no further!  Can you help???

Thanks
Carrie

---

### Post by Rubi1200 on 2011-08-11
Hi and welcome to the forums :-)

Please do the following so we can get a better overview of the situation:

Boot the computer with a LiveCD/USB, choosing to try not install Ubuntu.

Go to the link at the bottom of my post and run the boot info script (instructions included there).

Post the results and we can take it from there.

Thanks.

---

### Post by Carne1590 on 2011-08-11
I can not get it to connect from the USB...

---

### Post by Blasphemist on 2011-08-11
I'm not sure what you mean. Can you boot the iso on usb? If so, can you choose try ubuntu? If you can choose try and get a desktop, can you access the internet? If you can access the internet and download the boot info script, please run it and post the results within code tags (use the # key in the message window).

---

### Post by Carne1590 on 2011-08-11
the computer will not boot in either Windows or Ubuntu.... I put the USB drive in and start her up and the screen with error comes up.

---

### Post by Blasphemist on 2011-08-11
It sounds like you are not getting it to boot from the usb. You'll need to go into bios and set the usb to first in the boot order or many pc's have a boot manager that you can access to choose your boot device. When you first turn on the computer you should be prompted at least for the bios access via an F key or maybe delete key. If there is a boot manager prompt it is likely at the same time.

---

### Post by Carne1590 on 2011-08-11
I tried that as well. The BIOS are set to boot from that location.

---

### Post by Blasphemist on 2011-08-11
You must then not have a bootable usb device that is working but let's go another direction then for now. This is how to proceed from the grub rescue prompt.
> The GRUB 2 rescue mode is a major enhancement to the GRUB bootloader. The presence of the grub rescue> prompt signifies that GRUB 2 has failed to find the grub folder, the grub.cfg file, and the associated modules. The rescue prompt is presented so the user can provide the path to the grub folder, load the necessary modules, and provide the proper boot commands.

A common reason for the grub rescue> prompt is an incorrect path to the grub folder. Reasons for the prompt could include a failure to update GRUB 2 after certain system or partition operations, improper designation of the grub folder location, or a failed installation.

To successfully boot from the grub rescue> prompt:

The grub folder must exist and contain the necessary GRUB 2 files.
The proper path must be set via the set prefix command.
Many GRUB 2 commands will not work until the correct path is set.
If the path to the grub folder (normally /boot/grub) is not correct, an unknown command or file not found message is likely.
The necessary modules must be loaded.
The kernel cannot be loaded until the 'linux' module is loaded.
A Linux kernel and initrd.img must be located and loaded.
> The rescue mode provides fewer commands than the normal GRUB prompt line, but also provides these additional commands:

Command
Result
dump
Clears memory
exit
Exit GRUB 2
normal
Return to the standard "grub>" mode if possible.
Among the commands which can be used in the grub rescue mode if the normal module can be loaded:
boot
cat
chain
help
insmod
linux
ls
multiboot
normal
search
set
unset
Once the user has confirmed the paths and existence of the proper folders in the previous section, run the following commands:
Rescue Prompt Boot Instructions (* Wubi Users See Note):
1. set prefix=(hdX,Y)/boot/grub
Use the values determined earlier. Example: If the Ubuntu system is on sda5, enter: set prefix=(hd0,5)/boot/grub
2.* set root=(hdX,Y)
Example: set root=(hd0,5)
3. insmod normal
Attempt to load the normal module.
4. normal
Activate the normal module. If successful, the GRUB 2 menu may appear.
5. set
(Optional) Review the current settings.
6. ls /boot
(Optional) Check for a vmlinuz and a initrd.img entry.
7. insmod linux
An error message usually means the path is incorrect.
8.* linux /vmlinuz root=/dev/sdXY ro
Selects the latest kernel. Example: linux /vmlinuz root=/dev/sda5 ro
9. initrd /initrd.img
Selects the latest initrd image.
10. boot
* For Wubi installs (within Windows) only substitute these commands in Steps 2 and 8:
2. set root=(loop0)
8. linux /vmlinuz root=/dev/sdXY loop=/ubuntu/disks/root.disk ro
Some additional considerations:
The current prefix and root settings may be checked at any time with the set command. To remove a setting, use the unset command (example: unset prefix).
Modules must be loaded before they can be used. If a module has not been loaded a unknown command error is displayed. If an incorrect path is specified, a file not found error message may be displayed.
The linux module must be loaded to be able to load both the kernel and the initrd image unless the normal module is loaded first.
If the modules cannot be found in the /boot/grub folder, the user may be able to load them from the /usr/lib/grub/i386-pc folder. The address if Ubuntu was installed on sda1 would be (hd0,1)/usr/lib/grub/i386-pc and the command would be: insmod (hd0,1)/usr/lib/grub/i386-pc/normal.mod
For a successful boot from the rescue prompt, the prefix path and root= setting must be correct, the linux module must be loaded, and the kernel (vmlinuz) and initrd image (initrd.img) must be accepted.
 The user should attempt to load the normal module to regain more capabilities while in the Grub 2 terminal. Try loading the normal GRUB 2 module with insmod normal, followed by normal on a separate line to activate the module. If successfully loaded and activated, help and additional commands will be available.
These changes are not permanent. After successfully booting into the system the user should run sudo update-grub and inspect the GRUB 2 configuration file (/boot//grub/grub.cfg). For problems with booting the main linux kernel, ensure the search, linux, and initrd lines in the [### BEGIN /etc/grub.d/10_linux ###] section of the file now point to the correct locations. The user may need to reinstall GRUB 2 using sudo grub-install /dev/sdX.
The above comes from this document that you may need to refer to. [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

