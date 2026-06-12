---
title: "error: no such partition"
date: 2011-06-07
forum: General Help
---

### Post by Uyoku on 2011-06-07
I recently partitioned my hard drive so that I could have Linux in addition to Windows Seven on my laptop. For some reason, at boot it it showed not only Linux, a Recovery mode for Linux, and a Windows 7 OS, but also a Windows Vista OS that I never installed.

Yesterday, A friend of mine borrowed my computer and chose to open Vista. Since then my computer has been stuck at the grub rescue screen with nothing other than the message:

error: no such partition
grub rescue>


I have tried the Set prefix, set root, insmod normal code and all it does is tell me the same error. Please help.

---

### Post by jerrrys on 2011-06-07
download testdisk live and see if you get lucky.  its fast and simple.

[http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)

---

### Post by Uyoku on 2011-06-07
Which one? There are 27 different links on that page. Also, what do I do after I complete the download?

I apologize if I seem ignorant, I only just started using this OS.

---

### Post by FormatSeize on 2011-06-07
> **Uyoku said:**
> Which one? There are 27 different links on that page. Also, what do I do after I complete the download?
 
I apologize if I seem ignorant, I only just started using this OS.
[This one]("http://www.cgsecurity.org/wiki/TestDisk_Download"). From there, click on the one that says "Linux" (it's the fourth one on the list), and your download should begin. And you don't seem ignorant.
 
Personally, I recommend using [these instructions]("https://help.ubuntu.com/community/Grub2") which are also listed below for your convenience, and don't involve any downloads:
> GRUB 2 Troubleshooting Preparation
In order to successfully boot from the "grub>" prompt, the user should locate/verify the: 
&#8226;Partitions - The / partition, and any separate partitions such as a boot partition. 
&#8226;Files - Location of the linux and initrd.img files (normally in /boot) and the grub.cfg file in /boot/grub 
The following commands will help determine this information. 
set
When set is typed without additional entries the command displays the current GRUB 2 settings.
 
ls 
The Linux partition should be listed, as should any special partition such as a separate boot or home. Example: (hd0) (hd0,1) (hd1,5) In this example sda, sda1, sdb5 are recognized. For (hd1,5), the X value is 1 and the Y value is 5.
 
ls (hdX,Y)/
This result should include vmlinuz and initrd.img
 
ls (hdX,Y)/boot
This result should include the specific kernel and initrd.img files
 
ls (hdX,Y)/boot/grub
Included should be numerous *.mod files and the grub.cfg file, as well as various *.img files.
 
 
''grub>'' Prompt Booting
If GRUB 2 leaves you at the grub> prompt, it has normally found the grub folder and loaded at least some basic modules. The configuration file (grub.cfg) may be missing or corrupted. 
If the user has confirmed the paths and existence of the proper folders in the previous section, attempt to load the configuration file with the following command: configfile (hdX,Y)/boot/grub/grub.cfg
 
If the configuration file is located, the GRUB 2 menu should appear and the user should be able to choose a selection and boot. If the configuration file is not found, a message will be generated and the user must enter the boot commands manually. 
&#8226;Press ENTER after completing each line. Some entries will not provide feedback. This is normal. 
&#8226;If a "file not found" or similar error message is displayed while running these commands, ensure you are using the correct X,Y values. 
Command Summary *: 
set root=(hdX,Y)
 
linux /vmlinuz root=/dev/sdXY ro
 
initrd /initrd.img 
 
boot
 
Expanded Instructions *: 
 
1.* set root=(hdX,Y) 
Type with correct X,Y results confirmed earlier and press ENTER. Remember GRUB 2 counts the first drive as 0, the first partition as 1. Example: If the Ubuntu system is on sda5, enter: set root=(hd0,5)
 
2.* linux /vmlinuz root=/dev/sdXY ro
Example: linux /vmlinuz root=/dev/sda5 ro 
 
* Wubi users see note.
 
3. initrd /initrd.img
Selects the latest initrd image.
 
4. boot
Boot to the latest kernel on the selected partition.
 
* Wubi users only - substitute these commands in Steps 1 and 2: 
 
set root=(loop0) 
 
linux /vmlinuz root=/dev/sdXY loop=/ubuntu/disks/root.disk ro 
 
Remember that the commands issued at the grub. prompt are not permanent. After successfully booting into the system the user should run sudo update-grub and inspect the GRUB 2 configuration file (/boot//grub/grub.cfg). For problems with booting the main linux kernel, ensure the search, linux, and initrd lines in the [### BEGIN /etc/grub.d/10_linux ###] section of the file now correctly point to the correct locations. The user may need to reinstall GRUB 2 (sudo grub-install /dev/sdX). 
If the system fails to boot, proceed to the grub rescue> section to run more targeted boot commands. 
Rescue Mode (''grub rescue>'') Booting
The GRUB 2 rescue mode is a major enhancement to the GRUB bootloader. The presence of the grub rescue> prompt signifies that GRUB 2 has failed to find the grub folder, the grub.cfg file, and the associated modules. The rescue prompt is presented so the user can provide the path to the grub folder, load the necessary modules, and provide the proper boot commands. 
A common reason for the grub rescue> prompt is an incorrect path to the grub folder. Reasons for the prompt could include a failure to update GRUB 2 after certain system or partition operations, improper designation of the grub folder location, or a failed installation. 
To successfully boot from the grub rescue> prompt: 
&#8226;The grub folder must exist and contain the necessary GRUB 2 files. 
&#8226;The proper path must be set via the set prefix command. 
Many GRUB 2 commands will not work until the correct path is set. If the path to the grub folder (normally /boot/grub) is not correct, an unknown command or file not found message is likely. 
&#8226;The necessary modules must be loaded. The kernel cannot be loaded until the 'linux' module is loaded. &#8226;A Linux kernel and initrd.img must be located and loaded. Use the GRUB 2 Troubleshooting Preparation section to locate the correct partitions and file locations. The following commands are available in the Rescue mode. 
The rescue mode provides fewer commands than the normal GRUB prompt line, but also provides these additional commands: 
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
 
Once the user has confirmed the paths and existence of the proper folders in the previous section, run the following commands: Rescue Prompt Boot Instructions (* Wubi Users See Note): 
 
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
 
Some additional considerations: &#9702;The current prefix and root settings may be checked at any time with the set command. To remove a setting, use the unset command (example: unset prefix). 
&#9702;Modules must be loaded before they can be used. If a module has not been loaded a unknown command error is displayed. If an incorrect path is specified, a file not found error message may be displayed. 
&#9702;The linux module must be loaded to be able to load both the kernel and the initrd image unless the normal module is loaded first. 
&#9702;If the modules cannot be found in the /boot/grub folder, the user may be able to load them from the /usr/lib/grub/i386-pc folder. The address if Ubuntu was installed on sda1 would be (hd0,1)/usr/lib/grub/i386-pc and the command would be: insmod (hd0,1)/usr/lib/grub/i386-pc/normal.mod 
For a successful boot from the rescue prompt, the prefix path and root= setting must be correct, the linux module must be loaded, and the kernel (vmlinuz) and initrd image (initrd.img) must be accepted.
 
The user should attempt to load the normal module to regain more capabilities while in the Grub 2 terminal. Try loading the normal GRUB 2 module with insmod normal, followed by normal on a separate line to activate the module. If successfully loaded and activated, help and additional commands will be available. 
These changes are not permanent. After successfully booting into the system the user should run sudo update-grub and inspect the GRUB 2 configuration file (/boot//grub/grub.cfg). For problems with booting the main linux kernel, ensure the search, linux, and initrd lines in the [### BEGIN /etc/grub.d/10_linux ###] section of the file now point to the correct locations. The user may need to reinstall GRUB 2 using sudo grub-install /dev/sdX. 

---

### Post by jerrrys on 2011-06-07
just a matter of preference, but to chose, go with gparted

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

all you have to do is get testdisk fired up and it will guide you to the fix, if one exist.

---

### Post by Uyoku on 2011-06-07
How am I to use this test disk file if I can't access my operating systems on my laptop?

---

### Post by jerrrys on 2011-06-07
it is a self-booting cd; no operating system required.

---

### Post by FormatSeize on 2011-06-07
> **Uyoku said:**
> How am I to use this test disk file if I can't access my operating systems on my laptop?
It is a Live CD, so you will boot into the environment provided by the CD and not use your operating system at all. They wouldn't actually work if you had to use your hard disk since your hard disk is broken, and because you can't do things that you can do from the CD if it used the disk without getting some sort of "device is busy" error.

---

### Post by Uyoku on 2011-06-07
So I just unzip the folder and put it onto a CD then put it into my laptop? Does it have to be a CD or can it be a DVD or a Flash Drive?

---

### Post by jerrrys on 2011-06-07
it can be flash or cd.  you need to download the ".iso" and then burn it to cd/flash

---

### Post by Uyoku on 2011-06-07
Thank you, I'm downloading it now.

---

### Post by Uyoku on 2011-06-07
I put it on my flash drive and plugged it into my laptop. What is the next step?

---

### Post by jerrrys on 2011-06-07
boot your lappy and follow the instructions.  like i said before, you just need to boot testdisk and it will guide you.

---

### Post by Uyoku on 2011-06-07
But how do I boot the test disk?

---

### Post by jerrrys on 2011-06-07
at this point i have to guess, i use a different version.  please to look here and see if this will help.

[http://gparted.sourceforge.net/liveusb.php](http://gparted.sourceforge.net/liveusb.php)

---

### Post by Uyoku on 2011-06-07
[ATTACH]194496[/ATTACH]

This appeared when I clicked on makeboot. Am I supposed to run it on my laptop only?

---

### Post by mike555 on 2011-06-07
Just to let you know, that Vista partition is your recovery partition for Windows 7 ,installed by the co. you bought it from ... once you get it fixed you might take it off your boot options so you or anyone else doesn't click it by mistake.......
   your friend might have messed up Windows 7 if he (or she) stopped the recovery mid stream , because it reinstalls Windows 7 as if it was new , probably formating as it does ....
   I would recommend before doing anything boot from a live boot manager (like grub live or plop live ) and see if you still are able to boot Windows 7 , if not then boot that Windows "Vista"partition and let it work to restore your Windows 7 ..... then install Ubuntu again to the Ubuntu partition .... then edit grub to put a # in front of the option to boot the Vista partition.

 but if you can boot everything (don't try Vista )using the live boot cd , then just boot into Ubuntu , then open terminal and type " sudo update-grub  " without the quote marks ... then make sure it works by restarting (without the live cd) if it works edit grub.

---

### Post by Uyoku on 2011-06-07
I don't know how to do any of that... I'm a newbie to this sort of thing.


Edit: Alright, I ran the makeboot thing and then plugged my flashdrive into my laptop. I chose my Flashdrive as the boot device and it said that there's "No bootable partition in the table."  Did I do anything wrong?

Edit 2: I reran the makeboot thing and tried again. This time it worked but it's asking about keymaps. First off, what is a key map? Secondly, which policy would you recommend using?

---

### Post by Uyoku on 2011-06-07
.Alright I set up the keymaps. What do I do next?


Edit: What would happen if I deleted the Linux partition? Would I then be able to access my Windows 7 OS?

---

### Post by Uyoku on 2011-06-07
I really need to fix this. Could somebody please answer my question?

---

### Post by mike555 on 2011-06-07
Don't delete any partition ..... grub will freakout ....... download a boot .iso to burn as an image to a cd, boot it , it will let you know which partitions are bootable still ..... 
 then boot Ubuntu if you can and follow my instructions before ....... in terminal , type "  sudo update-grub " without the quotes ... etc.

 a good live boot iso is ;   [http://en.kioskea.net/faq/2677-super-grub-disk-live-cd](http://en.kioskea.net/faq/2677-super-grub-disk-live-cd)

---

### Post by Uyoku on 2011-06-08
Can it be on the same flash drive as the GParted thing?

---

### Post by mike555 on 2011-06-08
I think the boot cd needs to be on a cd by itself , or maybe a thumbdrive by itself ( I haven't tried putting the boot manager .iso on a thumbdrive )

---

### Post by Uyoku on 2011-06-08
Is this a bootable file that could work from just itself on the flashdrive?

Edit: I booted it from the flash drive and it took me to something similar to grub rescue. It says:

SYSLINUX 4.04 EDD 2011-04-18 Copyright (C) 1993-2011 H. Peter Anvin et al
ERROR: No configuration file found
No DEFAULT or UI configuration file found
boot:

What should I do?

---

### Post by Uyoku on 2011-06-08
Please help.

---

### Post by mike555 on 2011-06-08
I think you did something wrong .. can you boot a cd ?

---

### Post by linuxinstalledfromhdd on 2011-06-08
[http://cinderbox.net/2011/06/08/how-to-fix-grub-grub2-windows-mbr-and-lost-systems/](http://cinderbox.net/2011/06/08/how-to-fix-grub-grub2-windows-mbr-and-lost-systems/)

---

### Post by Uyoku on 2011-06-09
> **mike555 said:**
> I think you did something wrong .. can you boot a cd ?

I can boot a cd now that a friend told me how. I'll try putting it on one.

Edit: I could boot it if my other computers would let me burn it.

Edit2: I went back to using the GParted thing that I could boot. I opened terminal and ran the sudo update-grub command, it told me this:


Searching for GRUB installation directory ...
No GRUB directory found.
 To create a template run 'mkdir /boot/grub' first
 To install grub, install it manually or try the 'grub-install' command.
 ### Warning, gurb-install is used to change your MBR. ###

Should I run these codes?

---

### Post by Uyoku on 2011-06-09
Please help.

---

### Post by jerrrys on 2011-06-09
**post#27**...its like test disk, but has a different interface.  should be easy to understand.  and if already posted, sorry.  i skimmed thru the post.

---

