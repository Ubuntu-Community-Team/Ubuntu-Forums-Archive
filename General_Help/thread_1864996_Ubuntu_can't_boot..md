---
title: "Ubuntu can't boot."
date: 2011-10-19
forum: General Help
---

### Post by valasek94 on 2011-10-19
Hello, i have a big problem with the newest ubuntu 11.10. Before i had windows xp, it works fine than i want ubuntu, so i burn a disc and boot it at computer startup. Everything works fine, ''try ubuntu'' works so i decided to install. After install, pc restarted and took me to the grub menu with four options of boot, normal mode, recovery mode and two hard drive check or something like that, so i chose the normal mode. But it wont boot, it frozed at the black screen with blinking cursor in left corner, a mouse and keyboard dont work, they are disconnected. I must hardly restart computer an always is the same. I tried everything, nomodeset, delete quiet and splash, xforcevesa. I dont know a **** about ubuntu so i cant fix it, maybe a read, it could be the problem with graphic card, i have nvidia geforce 6600, but livecd works, so i dont have an idea. Every help will be perfect and i would be very happy for fixing this ******* problem, because i want ubuntu!
Thank you for answers

---

### Post by hal8000 on 2011-10-19
If you delete the options quiet and splash, then when Ubuntu boots you should see terminal messages.

What is the last message on the screen before it locks up?

One more thing, the last few Ubuntu releases do display just a flashing cursor before the login screen appears, I am presuming you have waited at least 5 minutes to see if anything appears?

Boot time is pretty quick generally as fast as windows on the same hardware.

---

### Post by oldfred on 2011-10-19
With nVidia, nomodeset should work.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

Have you tried recovery mode to get to a command line?

---

### Post by valasek94 on 2011-10-20
When i delete quiet splash, nothing appears, just the same blank screen with cursor. 

I tried to boot in recovery mode, and in this it writes some problems like acpi_processor_power_init.., kernel thread helper, start kernel kernel init, acpi fan init, irg to desc and much more i dont know if its needed for my problem, and keyboard and mouse still disconnect themselves before it jumps to this screen.

And one thing more, ubuntu live cd and try ubuntu only goes with acpi off, nolapic, noapic parameters, so maybe is there any way to add this three parameters to hard drive boot options.

And nomodeset doesnt work, its the same as without it.

---

### Post by oldfred on 2011-10-20
Just like you added nomodeset, you can add additional parameters. But that is for a one time boot. 

If you need permanent parameters then you modify /etc/default/grub and run sudo update grub to incorporate those into grub.cfg.

gksudo gedit /etc/default/grub
sudo update-grub

[https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29](https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29)

> GRUB_CMDLINE_LINUX
    * Entries on this line are added to the end of the 'linux' command line (GRUB legacy's "kernel" line) for both normal and recovery modes. It is used to pass options to the kernel. 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
   * This line imports any entries to the end of the 'linux' line (GRUB legacy's "kernel" line). The entries are appended to the end of the normal mode only.
       o To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash". 






---

### Post by drs305 on 2011-10-20
The options to add to match the CD options would be:
> noapic noloapic acpi=off 
added to the 'linux' line for manual editing of the grub menuentry or on the "GRUB_CMDLINE_LINUX_DEFAULT" line in */etc/default/grub*. After saving the file don't forget to run "sudo update-grub" to incorporate the changes in the Grub menu.

---

### Post by freccia on 2011-10-20
I had the same problem myself after an upgrade from 11.04 and nobody came up with a solution except to format the drive and do a fresh install, and that is what i had to do , loosing everything and so I installed 11.04 and will not upgrade to 11.10 at least until there is a good solution to this problem.
Thanks

---

