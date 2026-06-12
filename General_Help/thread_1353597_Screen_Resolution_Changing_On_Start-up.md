---
title: "Screen Resolution Changing On Start-up"
date: 2009-12-12
forum: General Help
---

### Post by Uadebisi on 2009-12-12
Hi,

My screen resolution changes on start-up from 1024 to 832 or 800, forcing me to constantly reconfigure only to have it change again on reboot. My panel icons also get shuffled around.  

I have seemingly found a couple of solutions to this problem but I am so new to Linux that I do not understand how to implement the fixes.

One of the fixes is to run the following in a terminal
> gksudo nvidia-settings, select your resolution and click on save to x configuration file.Or,>  do a gksudo nvidia-xconfig, this will then create the xconfig file, then do a gksudo nvidia-settings and select your rez and save to X. (both posted by Arup)

However, after I type "gksudo nvidia-settings", nothing happens. There is a pause with the terminal & then it jumps to the next line but without showing any new info. I do have the jockey gtk hardware installed by default.

Another fix I found that has worked for at least a couple people was this:
> Originally Posted by **madverb**                                      
                 *Even better! Just removed the ~/.config/monitors.xml and now it completely ignores the gnome settings! Login is also much smoother now. This is really damn annoying.*
The problem is that I do not know how to implement this fix. 

Remember, I am new to Ubuntu so talk to me like I am 7:)

---

### Post by Uadebisi on 2009-12-14
UPDATE: I have since realized that I do not have a Nvidia card but an Intel  82945G/GZ Integrated Graphics Controller. And after reading countless threads pertaining to this and countless different correction opinions, I still have no idea how to rectify my problem, if that's even possible.

When I type Intel in the  Package Manager, I find a bunch of (uninstalled) drivers that may fix the situation but I am not sure & not one of them is suggested as a fix in any of the threads that I read.

Anyone know how to fix this? Thanks!

---

### Post by Uadebisi on 2009-12-15
Well, I seem to be having a conversation with myself but I do have an answer ;)

Here's what I did to fix my problem... keeping in mind that I use Grub2 so all I had to do was download "Startup Manager" from the "Software Center" & adjust the settings in the GUI. Also, I have no /etc/X11/xorg.conf file:

     > originally posted by** trx64: **I've solved the problem by disabling KMS (Kernel Mode Setting) in Intel driver, leaving the detection of my screen resolution just with X. There is no need to change xorg.conf, just leave it at default values.
 
 Edit the file /boot/grub/menu.lst (if you have GRUB 2, use [Startup Manager]("apt:startupmanager")). In the end of the "kernel" line of the OS entry, add "nomodesetting":
 
         Code:
     title           Ubuntu 9.10, kernel 2.6.31-14-generic
root            (hd0,4)                              
kernel          /boot/vmlinuz-2.6.31-14-generic root=UUID=92583a31-1693-438c-ae3f-61ab9b8ca13a ro quiet splash locale=pt_BR **nomodesetting**                                       
initrd          /boot/initrd.img-2.6.31-14-generic                                   
quiet                                 
                                 
See [http://ubuntuforums.org/showthread.php?t=1308745](http://ubuntuforums.org/showthread.php?t=1308745)

---

