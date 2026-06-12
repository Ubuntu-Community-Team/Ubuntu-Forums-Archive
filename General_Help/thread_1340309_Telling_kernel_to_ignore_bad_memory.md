---
title: "Telling kernel to ignore bad memory"
date: 2009-11-28
forum: General Help
---

### Post by sdowney717 on 2009-11-28
I have 1024 MB and the last 54 MB is bad according to memtest86.

SO, all you have to do is make a comment in the kernel boot line

For grub2 it is tricky. You have to run sudo update-grub to regenerate 
/boot/grub/grub.cfg and grub2 uses the settings in /etc/default/grub to generate the new /boot/grub/grub.cfg file. 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" should be
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash memmap=54M\$970M"??

however this is writing into grub.cfg
memmap=54M$\970, BUT you want memmap=54M\$970

so that means you must edit /boot/grub/grub.cfg manually. it is a read only root file so you got to make it writable before you edit.

thus 
linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=4923760a-6e34-4678-b0ab-d06b151a2998 ro   quiet splash
becomes
linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=4923760a-6e34-4678-b0ab-d06b151a2998 ro   quiet splash memmap=54M\$970M

for example in my case memmap=54M\$970M tells it to ignore the last 54MB of the ram. You can use M for MB's and K for kilobytes or use an address.

I dont know if this is a bug or not but it means you will have to edit the file by hand everytime a new kernel comes thru unless someone knows better syntax for the file /etc/default/grub


also in /etc/default/grub the line
#GRUB_HIDDEN_TIMEOUT=0  
tells it to show the menu

memmap examples, personally think setting the memmap parameters using MB's and not addresses is easier
[http://linux.derkeiler.com/Mailing-Lists/Kernel/2008-03/msg05303.html](http://linux.derkeiler.com/Mailing-Lists/Kernel/2008-03/msg05303.html)
[http://ubuntuforums.org/showthread.php?t=860631](http://ubuntuforums.org/showthread.php?t=860631)
grub2 help
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by sdowney717 on 2009-11-28
ok, i got it with using this

54M\\\$970M

yields this

54M\$970M


the '\' char must tell it to ignore processing the next char as a control char when creating the line.

i ran thru combinations till i could make some sense of it
> 
54M\\$\970M  54M\$\970M

54M\$\970M   54M$\970M

54M\\\$\970M 54M\$\970M

54M\$$\970M  54M$$\970M

54M\\970M    54M\970M

54M\\$970M   54M$970M

54M\\$970M   54M\M

54M\\$$970M  54M\23219970M

54M\$$970M   54M$M

54M\$\$970M  54M$$970M

54M\\$\$970M 54M\$$970M

54M\\$\970M  54M\$\970M

54M\\$970M   54M\M

54M\$970M    54M$970M

54M\\970M    54M\970M

54M\\\$970M  54M\$970M


---

