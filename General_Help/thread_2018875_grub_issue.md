---
title: "grub issue"
date: 2012-07-06
forum: General Help
---

### Post by hawthornso23 on 2012-07-06
I'm running precise.

For some reason grub hasn't been updating itself with new kernel versions for some time. Having recently cleaned out my old 3.0 kernel versions I now find myself unable to boot without manually editing the grub command. Fortunately tab completion manages to find the valid and existing kernel versions even though the grub menu itself now lists only obsolete and deleted kernels.

**sudo update-grub**     

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-26-generic
Found initrd image: /boot/initrd.img-3.2.0-26-generic
Found linux image: /boot/vmlinuz-3.2.0-25-generic
Found initrd image: /boot/initrd.img-3.2.0-25-generic
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
Found linux image: /boot/vmlinuz-2.6.38-14-generic
Found initrd image: /boot/initrd.img-2.6.38-14-generic
Found linux image: /boot/vmlinuz-2.6.35-32-generic
Found initrd image: /boot/initrd.img-2.6.35-32-generic
Found linux image: /boot/vmlinuz-2.6.35-31-generic
Found initrd image: /boot/initrd.img-2.6.35-31-generic
Found linux image: /boot/vmlinuz-2.6.35-30-generic
Found initrd image: /boot/initrd.img-2.6.35-30-generic
Found memtest86+ image: /boot/memtest86+.bin
done
```

which looks OK. But during next boot it tries once again to boot into a non-existent 3.0 kernel. The presence of the 2.6 kernels here is also a bit annoying  as according to synaptic they are not installed making it hard to uninstall them. I suspect they may have become orphaned from the package database somehow in the last distribution upgrade. They seem to still be there even though synaptic cannot see them.

```

$ cd /boot ; ls
abi-2.6.35-30-generic         initrd.img-3.2.0-25-generic
abi-2.6.35-31-generic         initrd.img-3.2.0-26-generic
abi-2.6.35-32-generic         memtest86+.bin
abi-2.6.38-14-generic         memtest86+_multiboot.bin
abi-3.2.0-24-generic          System.map-2.6.35-30-generic
abi-3.2.0-25-generic          System.map-2.6.35-31-generic
abi-3.2.0-26-generic          System.map-2.6.35-32-generic
config-2.6.35-30-generic      System.map-2.6.38-14-generic
config-2.6.35-31-generic      System.map-3.2.0-24-generic
config-2.6.35-32-generic      System.map-3.2.0-25-generic
config-2.6.38-14-generic      System.map-3.2.0-26-generic
config-3.2.0-24-generic       vmcoreinfo-2.6.35-30-generic
config-3.2.0-25-generic       vmcoreinfo-2.6.35-31-generic
config-3.2.0-26-generic       vmcoreinfo-2.6.35-32-generic
extlinux                      vmcoreinfo-2.6.38-14-generic
grub                          vmlinuz-2.6.35-30-generic
initrd.img-2.6.31-21-generic  vmlinuz-2.6.35-31-generic
initrd.img-2.6.35-30-generic  vmlinuz-2.6.35-32-generic
initrd.img-2.6.35-31-generic  vmlinuz-2.6.38-14-generic
initrd.img-2.6.35-32-generic  vmlinuz-3.2.0-24-generic
initrd.img-2.6.38-14-generic  vmlinuz-3.2.0-25-generic
initrd.img-3.2.0-24-generic   vmlinuz-3.2.0-26-generic

```

Can anyone suggest how to fix this problem so that I can boot normally.

---

### Post by jmfal on 2012-07-06
If you haven't done it already, reboot to grub screen >>recovery>>update grub

---

### Post by drs305 on 2012-07-06
Try this quick fix, and if it doesn't work proceed to the next paragraph. This makes sure your system updates the grub.cfg file:
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

I recommend installing and running Boot Repair and select the Recommended Repair option. If that doesn't work, there is an advanced option to purge/reinstall Grub. We used to have to do that manually but BR can now walk you through the procedure.

Link to Boot Repair is in my signature line.

---

### Post by hawthornso23 on 2012-07-06
Thanks for you help

```
sudo grub-mkconfig -o /boot/grub/grub.cfg
[sudo] password for ian: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-26-generic
Found initrd image: /boot/initrd.img-3.2.0-26-generic
Found linux image: /boot/vmlinuz-3.2.0-25-generic
Found initrd image: /boot/initrd.img-3.2.0-25-generic
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
Found linux image: /boot/vmlinuz-2.6.38-14-generic
Found initrd image: /boot/initrd.img-2.6.38-14-generic
Found linux image: /boot/vmlinuz-2.6.35-32-generic
Found initrd image: /boot/initrd.img-2.6.35-32-generic
Found linux image: /boot/vmlinuz-2.6.35-31-generic
Found initrd image: /boot/initrd.img-2.6.35-31-generic
Found linux image: /boot/vmlinuz-2.6.35-30-generic
Found initrd image: /boot/initrd.img-2.6.35-30-generic
Found memtest86+ image: /boot/memtest86+.bin
done
```

Now rebooting to see if that will take

---

### Post by drs305 on 2012-07-06
Once, (if) you get it booting, you can try using Ubuntu Tweak to remove remnants of older kernels. This post contains other methods as well:
[http://ubuntuforums.org/showthread.php?t=1587462]("http://ubuntuforums.org/showthread.php?t=1587462")

---

### Post by hawthornso23 on 2012-07-06
OK - that didn't work. It still tried to boot me into 3.0.0-17

Note that I CAN boot. In fact I'm, posting this from the machine in question after rebooting. But I have to manually edit the grub commandline each time to point it to the correct kernel version.

I will now try the other options you mention.

---

### Post by drs305 on 2012-07-06
I understood you can boot but generally I recommend only working on one thing at a time. But removing older kernels shouldn't hurt.

Do you have another OS running Grub. It sounds like you may be updating your current GRUB but booting another one. This could be very misleading if your other version is similar, such as Mint. You can either 

1. Ensure your current version controls Grub:
```
sudo grub-install /dev/sdX # (normally sda)
```

Another way to check, but not fix, if your current Grub controls is to edit /boot/grub/grub.cfg and change the first menuentry's title to something that will stand out. Then reboot and see if the new title is displayed. This will ensure you are editing the booting menu entries.
```

gksu gedit /boot/grub/grub.cfg
```
In this case you would NOT want to run "update-grub" after saving the changes.

---

### Post by hawthornso23 on 2012-07-06
Your boot repair program seems to have fixed the immediate issue.

```
 uname -a
Linux Tartaglio 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

Thank VERY MUCH for your assistance. 

I'll look over some of the other things you pointed at in case there is a lingering issue.  If there is another grub around it can only have happened during my most recent distribution upgrade which got a little bit ... exciting. The machine has only ever had ubuntu on it.

---

