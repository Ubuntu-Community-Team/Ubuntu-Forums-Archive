---
title: "Select older kernel from GRUB screen or install older kernel"
date: 2011-11-07
forum: General Help
---

### Post by MorrisseyJ on 2011-11-07
Hi

I am having an issue with the new kernel (random freezes) and would like to revert back to an older version.

I used to be able to do this easily at the GRUB prompt,as the older versions of the kernel would get stored on my GRUB screen. I could then just select the kernel version i wanted or set the config file to boot from the relevant kernel on the list. 

In Natty it seems that the older kernels are no longer stored on my GRUB screen when a newer version of the kernel installs. 

Can anyone tell me either how to get the older versions of the kernel to show up on my GRUB screen or how i can easily install the previous kernel?

Thanks.

---

### Post by ajgreeny on 2011-11-07
You can try holding shift at bootup to get to a grub menu, and from that you can boot to an older kernel.

If that is no help, or you don't see a menu, please show the output of ```
grep menuentry /boot/grub/grub.cfg
```in terminal.  That will list the kernels on your system that should be showing in the menu.

---

### Post by MorrisseyJ on 2011-11-07
Hi,

Thanks for the response. 

Holding down the shift key just brings up the GRUB menu as normal - which only shows the 2.6.38-12 kernel and the rest of my partitions (Windows).

The output of

> grep menuentry /boot/grub/grub/.cfgis:

```
menuentry 'Ubuntu, with Linux 2.6.38-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.38-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
```So the older kernel is there, its just not showing in my GRUB menu.

---

### Post by WasMeHere on 2011-11-07
Hi MorrisseyJ

In the grub menu of vanilla Natty I have the line 'Previous Linux versions'. I guess you have it too. Select that and press Enter! Then you get a submenu with your old versions.

Have fun finding out :-)
Olle

---

### Post by drs305 on 2011-11-07
As *Olle Wiklund* stated, they should be 'hidden' under the "Previous" entry.

If they are not, since the older kernels are still on your machine, you can highlight the top entry of the Grub 2 menu, press 'e' to edit it, and then scroll to the 'linux' and 'initrd' lines and change the version number to the one you want to convert (e.g ...38-12-generic to ...38-11-generic).

Once you have made the changes, don't press ENTER, just CTRL-x to boot and then change the default by removing the newer kernel either manually or with Ubuntu Tweak, using Grub Customizer, or editing /etc/default/grub manually.

---

### Post by MorrisseyJ on 2011-11-07
Hi thanks everyone for all the help. Yes, that option is there. I don't know how i missed it.

Just installed 'start-up manager' and can configure the boot preference from there. 

Thanks again for the help.

---

### Post by drs305 on 2011-11-07
You aren't the first person to miss the new submenu.  ;-)

StartUp-Manager can do a few things with Grub 2, but for serious and consistent tweaking I'd recommend Grub Customizer (see the 'Customizer' link in my signature line). GC was built after Grub 2 was introduced, so it does a better job than SUM.

Please mark the thread SOLVED via the thread tools link near the top right of the first post if you don't have any more need for assistance with this.

Happy Ubuntu-ing !

---

### Post by MorrisseyJ on 2011-11-07
Thanks. 

Will have a look at that. 

Thread marked as solved.

---

