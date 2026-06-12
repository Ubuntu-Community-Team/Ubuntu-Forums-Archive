---
title: "Dual boot with Windows"
date: 2012-06-10
forum: General Help
---

### Post by ryanyeah on 2012-06-10
So I am running a single install of 12.04 right now. I would like to dual boot with Windows, but have been told Windows needs to be installed first in order to allow this to happen. Would the following set of steps allow this to happen?

- unplug my current ubuntu drive temporarily.
- plug in a new drive and install windows onto it.
- plug in my ubuntu drive again. 
- turn on computer and hopefully it will get to grub and ill have the option to boot from either? that is unless the Windows crappy boot loader overwrites it.

---

### Post by latinlightning on 2012-06-10
When you say "unplug" I'm taking that you have external storage mediums? The easiest way would be to have one hdd that has Windows installed first, then partition that same drive to allow Ubuntu to dual-boot and have GRUB be the boot loader and THEN use your external storage medium for your data and files (be it both for WS and Ubuntu).

---

### Post by wilee-nilee on 2012-06-10
That is a fine method, when done make sure the Ubuntu HD is first in the bios, and run in ubuntu.

```
sudo update-grub
```

To pick up the windows install.

And by the way derogatory remarks on any OS are not really appreciated.

If you want help be civil.

---

### Post by lindsay7 on 2012-06-10
Your idea will work but you will not have a true dual boot system.  The computer bios is set right now to boot from the Ubuntu drive. If you want to use windows you will have to go into the bios and tell it to boot from the new drive.  You will have to do this each time you want to boot into the other os.  The good news is you can not screw anything up.

---

### Post by ryanyeah on 2012-06-10
> **latinlightning said:**
> When you say "unplug" I'm taking that you  have external storage mediums? The easiest way would be to have one hdd  that has Windows installed first, then partition that same drive to  allow Ubuntu to dual-boot and have GRUB be the boot loader and THEN use  your external storage medium for your data and files (be it both for WS  and Ubuntu).

Nah, internal. That would be fine but I don't want to lose my existing ubuntu installation by reinstalling. 

> **wilee-nilee said:**
> That is a fine method, when done make sure the Ubuntu HD is first in the bios, and run in ubuntu.
```
sudo update-grub
```To pick up the windows install.

Ah, sweet. I'll give this a go.

> 
And by the way derogatory remarks on any OS are not really appreciated.
If you want help be civil.

Sure, I'll leave this out next time. I only said it because it's quite annoying Windows bootmgr has overwriting tendencies and by choice, doesn't work with grub or non-windows OSs.

---

### Post by wilee-nilee on 2012-06-10
> **lindsay7 said:**
> Your idea will work but you will not have a true dual boot system.  The computer bios is set right now to boot from the Ubuntu drive. If you want to use windows you will have to go into the bios and tell it to boot from the new drive.  You will have to do this each time you want to boot into the other os.  The good news is you can not screw anything up.

All completely wrong it is a dualboot and grub will boot windows.

---

### Post by ryanyeah on 2012-06-10
> **lindsay7 said:**
> Your idea will work but you will not have a true dual boot system.  The computer bios is set right now to boot from the Ubuntu drive. If you want to use windows you will have to go into the bios and tell it to boot from the new drive.  You will have to do this each time you want to boot into the other os.  The good news is you can not screw anything up.

If I boot to the ubuntu drive as the first drive, won't that take me to grub and give me the option to boot to either ubuntu or windows? If that is the case, it wouldn't require actual tampering with the bios boot priority order each time.

---

### Post by oldfred on 2012-06-10
Many suggest disconnecting drives to be sure each drive is independent. 

If you have Windows on the first drive just be sure to connect it as the first drive when you reconnect both drives. Ubuntu uses UUIDs and tolerates changes.

More info, if you do not disconnect drive, you have to use manual install or something else. That is the only way you get the choice on which drive's MBR to install the grub2 boot loader.

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

