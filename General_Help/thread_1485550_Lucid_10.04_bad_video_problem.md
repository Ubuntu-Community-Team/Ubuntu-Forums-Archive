---
title: "Lucid 10.04 bad video problem"
date: 2010-05-17
forum: General Help
---

### Post by wightghost on 2010-05-17
I just installed 10.04 Lucid Lynx and have a serious graphics problem.  I've attached a picture to show the problem.
Some Background:
Pentium 4 3.06GHz
1.5GB RAM
ATI Radeon 9600

I installed via liveUSB but had to choose the "nomodeset" option by pressing F6.  Otherwise after the Ubuntu boot screen the graphics went like that in the attached image.  

The installation went fine (took less than 15 minutes!) but after the reboot the graphics problem returned.  I can't see anything and the system is useless this way.  I can't post up any logs (I'm typing this from the liveUSB).

Any Ideas?

Thanks

---

### Post by Timtro on 2010-05-17
Try this.

Press CTRL+ALT+F1 or F2 or... to drop to a TTY terminal. Then edit your grub configuration as explained here:

[http://www.antiyes.com/dell-studio-15-ubuntu-910-install](http://www.antiyes.com/dell-studio-15-ubuntu-910-install)

to add the nomodeset for when grub loads your kernel.

Then I'd probably load the binary driver if you're not opposed to such a thing.

---

### Post by wilee-nilee on 2010-05-17
Here is a thread on this card.
[http://ubuntuforums.org/showthread.php?t=1424087](http://ubuntuforums.org/showthread.php?t=1424087)
Here is a straight link from the thread.
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by ryan858 on 2010-05-17
You have to edit your /boot/grub/grub.cfg and add nomodset at the end of the line with your kernel and parameters.

Open a terminal and type:

[B]mount /dev/*<partition>* /mnt 
g[/B]**edit /mnt/boot/grub/grub.cfg**

Where *<partition>* is the partition you installed Ubuntu on, such as *sda1* or *sda2*, etc.

Then, you should have grub.cfg opened in Gedit.

For example,
[I]/boot/grub/grub.cfg:
[/I]> 
...

menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c17adedf-9f46-4e67-9ecd-268017d99c30
    **linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=c17adedf-9f46-4e67-9ecd-268017d99c30 ro quiet splash nomodset**
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=1680x1050x24
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c17adedf-9f46-4e67-9ecd-268017d99c30
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=c17adedf-9f46-4e67-9ecd-268017d99c30 ro single
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}Do not modify anything else, and do not copy this quote, yours will probably be different, but very similar. Just add nomodset to the end of the line and click Save.

The part in my quote should be close to the end of the file... And make sure you put it in the main Ubuntu entry, not the recovery entry. It says "Ubuntu, with Linux 2.6.32-21-generic" **NOT** "Ubuntu, with Linux 2.6.32-21-generic (recovery mode)".

---

### Post by lavinog on 2010-05-17
per: [https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting):
```

# ATI Radeon:
echo options radeon modeset=0 > /etc/modprobe.d/radeon-kms.conf

```

This should work better though since you need sudo:
```

echo options radeon modeset=0 |sudo tee /etc/modprobe.d/radeon-kms.conf

```

---

### Post by wightghost on 2010-05-17
> **ryan858 said:**
> You have to edit your /boot/grub/grub.cfg and add nomodset at the end of the line with your kernel and parameters.

This did the trick!  Many thanks.  I have proper video now.
Now the wireless doesn't work :mad:
May have to post a separate thread if I can't get it going.

Thanks again

---

