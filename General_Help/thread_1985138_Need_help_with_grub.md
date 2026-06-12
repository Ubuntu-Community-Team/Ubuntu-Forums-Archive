---
title: "Need help with grub"
date: 2012-05-22
forum: General Help
---

### Post by brandon88tube on 2012-05-22
I ended installing grub to the Windows 7 (bootloader) partition /dev/sda1 when going through the original install. All was fine and dandy until I wanted to boot into windows... It just kept bringing me back to the grub menu. I figured I screwed something up and really needed to get into windows so I tried repairing the MBR thinking that might be the issue. Well that broke everything and I had to reinstall grub. Now, I'm back to a non-woking Windows 7 item in by grub menu. I wanted to know if someone could help me with this. The actual Windows 7 content is on /dev/sda2

---

### Post by synapsys on 2012-05-22
Windows tends to think it's the only disk in existence and likes to be on the first partition of the first drive. I suggest physically unplugging the drive housing Ubuntu, then running the Windows startup repair once more. After it's done, reboot into Windows to verify it's working. After that, plug the Ubuntu drive back in, and boot it up. Then (if you're running Grub2) you can run

```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```to rebuild the grub.cfg file. This should auto-detect the Windows disk and give you the option to boot into it at next reboot. Let me know if this works for you.

---

### Post by wilee-nilee on 2012-05-22
> **brandon88tube said:**
> I ended installing grub to the Windows 7 (bootloader) partition /dev/sda1 when going through the original install. All was fine and dandy until I wanted to boot into windows... It just kept bringing me back to the grub menu. I figured I screwed something up and really needed to get into windows so I tried repairing the MBR thinking that might be the issue. Well that broke everything and I had to reinstall grub. Now, I'm back to a non-woking Windows 7 item in by grub menu. I wanted to know if someone could help me with this. The actual Windows 7 content is on /dev/sda2

Download the link, extract it to the desktop, run the command and paste all the text from the result.txt to a reply. When you open the reply click the # in the reply panel, and paste all the text between the code tags.
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```

---

### Post by brandon88tube on 2012-05-23
I'm adding some additional info considering the posts provided don't really pertain to me. First, I only have 1 hdd that is partitioned. Second, I overwrote the small 100mb system partition Windows made with grub. When in grub, selecting Windows 7 sends be straight back to grub. I think this is trying to load up the first partition which originally had the Windows 7 bootloader, but now grub is located there and thus sending me right back to the grub boot menu. I need to somehow get it to boot the second partition which contains the actual Windows 7 install. I'm not all that familiar with grub and my attempts thus far haven't really worked. So, I was hoping someone here could help with this.

---

### Post by wilee-nilee on 2012-05-23
> **brandon88tube said:**
> I'm adding some additional info considering the posts provided don't really pertain to me. First, I only have 1 hdd that is partitioned. Second, I overwrote the small 100mb system partition Windows made with grub. When in grub, selecting Windows 7 sends be straight back to grub. I think this is trying to load up the first partition which originally had the Windows 7 bootloader, but now grub is located there and thus sending me right back to the grub boot menu. I need to somehow get it to boot the second partition which contains the actual Windows 7 install. I'm not all that familiar with grub and my attempts thus far haven't really worked. So, I was hoping someone here could help with this.

Post the script, this will confirm what you said you did.  This is a confirmation needed to help you, there are fairly easy ways to get the grub out of windows, but none of us will advise them until we confirm what is going on.

---

### Post by brandon88tube on 2012-05-23
Well I fixed it... sort of. I just followed the steps here: ubuntuforums.org/showthread.php?t=1014708 and ended up just fixing the Windows 7 one. I'll eventually have to get back to grub, but for now this works for me.

---

### Post by drs305 on 2012-05-23
Without seeing the information requested, I'm fairly certain you installed Grub into your Windows partition rather than the MBR. This would cause the result you described.

When you get around to reinstalling Grub, make sure you install it to the device (sda, sdb, etc) and not a partition. This will make Grub the default bootloader but it should find and add a menu for your Windows OS.

If you have two hard drives, install Grub to the MBR of the non-Windows drive and have the BIOS boot that one first. If Grub ever fails, you can change the BIOS boot order and get back your original Windows bootloader.

---

