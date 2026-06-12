---
title: "Cleaning Grub"
date: 2011-10-03
forum: General Help
---

### Post by DaimyoKirby on 2011-10-03
I recently installed Xubuntu alongside Ubuntu, then after moving a few personal files, I removed Ubuntu. Now, though, it still shows grub when I boot up - is there a way to stop grub from showing up, and have it boot straight to Xubuntu?

---

### Post by wolfen69 on 2011-10-03
```
sudo update-grub
```

---

### Post by garvinrick4 on 2011-10-03
Go into Xubuntu and 
```
sudo update-grub
```If you no longer have Ubuntu install it will make a new config file without Ubuntu and will
default to boot xubuntu without showing menu entry screen at all. Must hold shift key down
at boot to see menuentrys with only one install.

---

### Post by DaimyoKirby on 2011-10-03
Well, I ran that code, and this is what it outputted:
```
alden@Laptop:~$ sudo update-grub
[sudo] password for alden: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-11-generic
Found initrd image: /boot/initrd.img-2.6.38-11-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
done
```

So I'm assuming it's still finding other (old?) kernels, or something like that. So my new question I assume would be - How do I remove these other boot options?

---

### Post by drs305 on 2011-10-03
You can try rebooting and you probably won't see the Grub menu (unless you hold down the SHIFT key).

But if you do, you can remove the memtest86+ menu item with:
```
sudo chmod -x /etc/grub.d/20_memtest86+
sudo update-grub
```
This makes the script that adds memtest to the menu unexecutable. If you want to restore it, change the - to a + and rerun "sudo update-grub".

The other entries are kernels, and having two listed isn't a bad idea. If the first one fails, the second may still boot.

---

### Post by DaimyoKirby on 2011-10-03
Ok, that worked, mostly - now it only lists Xubuntu and Ubuntu (recovery mode). Is there a way to hide it from showing, to have it automatically choose Xubuntu?

---

### Post by drs305 on 2011-10-03
I'd recommend installing and using Grub Customizer. It's a great app that can tweak almost every aspect of Grub 2.

You can read more about it by clicking the "Customizer" in my signature line.

If the menu is still showing, you can hide it by setting the GRUB TIMEOUT to 0. You can do this via Grub Customizer.

If you do set the timeout to 0, reboot to make sure the menu isn't displayed. 

Then, on the next reboot try holding down the SHIFT key to make sure you can access the menu if you have problems. If SHIFT doesn't work, I'd recommend keeping the menu displayed for at least 1 second (default is 10) so you can access the menu if necessary.

---

### Post by DaimyoKirby on 2011-10-03
That worked! Thanks so much!

---

