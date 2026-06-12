---
title: "How to remove junk form startup menu"
date: 2010-04-13
forum: General Help
---

### Post by Rebelli0us on 2010-04-13
There's a growing list of "Kernel" versions in the boot menu. I just want Ubuntu and Windows, how do I get rid of the superseded kernel entries?

---

### Post by stoneage on 2010-04-13
Open Synaptic, search for linux-image and linux-headers, remove the ones you don't want, and restart.

You are looking for three files:-
linux-headers, linux-headers-2.6.31-xx-generic, linux-image-2.6.31-xx-generic

Most people keep at least one spare kernel version. If an update breaks the one you are using you can still boot with the spare and login to repair the problem.

---

### Post by indylarry on 2010-04-13
I think you are looking for this:

[http://ubuntuforums.org/showthread.php?t=169234]("http://ubuntuforums.org/showthread.php?t=169234")

---

### Post by warfacegod on 2010-04-13
After you done stoneage's instructions, you'll need to open a Terminal and type:

```
sudo update-grub
```

---

### Post by Rebelli0us on 2010-04-13
With the new Grub there is no menu.lst to edit??  Is there a GUI for editing or some other file to edit?

---

### Post by Rebelli0us on 2010-04-13
> **stoneage said:**
> Open Synaptic, search for linux-image and linux-headers, remove the ones you don't want, and restart.

You are looking for three files:-
linux-headers, linux-headers-2.6.31-xx-generic, linux-image-2.6.31-xx-generic

Most people keep at least one spare kernel version. If an update breaks the one you are using you can still boot with the spare and login to repair the problem.


Thank you, I found a whole bunch of "linux-header" files, do I just delete the unwanted ones and keep only the latest?

---

### Post by philinux on 2010-04-13
> **Rebelli0us said:**
> Thank you, I found a whole bunch of "linux-header" files, do I just delete the unwanted ones and keep only the latest?

I always keep two it's up to you.

---

### Post by philinux on 2010-04-13
> **warfacegod said:**
> After you done stoneage's instructions, you'll need to open a Terminal and type:

```
sudo update-grub
```

When you remove kernels the system auto runs update-grub. In fact if you remove more than one it gets run again and again.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/483660](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/483660)

---

### Post by warfacegod on 2010-04-13
> **Rebelli0us said:**
> Thank you, I found a whole bunch of "linux-header" files, do I just delete the unwanted ones and keep only the latest?

If that is what you wish to do, yes. As stoneage said, its usually a good idea to keep an older one just in case but you don't have to.

When you're done remember the code I put in my last post.

---

### Post by warfacegod on 2010-04-13
> **philinux said:**
> When you remove kernels the system auto runs update-grub. In fact if you remove more than one it gets run again and again.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/483660](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/483660)

Mine has never done that.

---

### Post by Rebelli0us on 2010-04-13
> **philinux said:**
> I always keep two it's up to you.

So I can select all but the latest (linux-headers-2.6.31-20-generic) and "Mark for Complete Removal"? And that will also remove them form the boot menu?

---

### Post by philinux on 2010-04-13
> **warfacegod said:**
> Mine has never done that.

Thats odd. Removing one kernel causes it to run twice. I just happen to be cleaning up Lucid but it happens on karmic too.
```

(Reading database ... 184379 files and directories currently installed.)
Removing linux-headers-2.6.32-16 ...
Removing linux-image-2.6.32-16-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 2.6.32-16-generic /boot/vmlinuz-2.6.32-16-generic
Running postrm hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-20-generic
Found initrd image: /boot/initrd.img-2.6.32-20-generic
Found linux image: /boot/vmlinuz-2.6.32-19-generic
Found initrd image: /boot/initrd.img-2.6.32-19-generic
Found linux image: /boot/vmlinuz-2.6.32-17-generic
Found initrd image: /boot/initrd.img-2.6.32-17-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 9.10 (9.10) on /dev/sda1
done
Purging configuration files for linux-image-2.6.32-16-generic ...
Running postrm hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-20-generic
Found initrd image: /boot/initrd.img-2.6.32-20-generic
Found linux image: /boot/vmlinuz-2.6.32-19-generic
Found initrd image: /boot/initrd.img-2.6.32-19-generic
Found linux image: /boot/vmlinuz-2.6.32-17-generic
Found initrd image: /boot/initrd.img-2.6.32-17-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 9.10 (9.10) on /dev/sda1
done
Log ended: 2010-04-13  13:30:21
```

---

### Post by scouser73 on 2010-04-13
> **Rebelli0us said:**
> So I can select all but the latest (linux-headers-2.6.31-20-generic) and "Mark for Complete Removal"? And that will also remove them form the boot menu?

Every time Ubuntu installs a new Linux kernel, the old one is left behind. This means that if you are regularly updating an Ubuntu system the Grub boot menu becomes longer and longer with kernels you don’t need anymore.

The old kernels are deliberately left installed and on the menu so you can boot a previous kernel if you have trouble with a new one. But if the new one works, you can safely uninstall the old kernel, which will also result in the Grub menu being cleaned up.

Follow these steps to identify and remove any old kernels.

**1** - Go to **Terminal** and paste the following command: **uname -r**
It will print the version of the Linux kernel you are running, this is the one you want to keep. It should look something like this: ***2.6.20-16-generic***

**2** - Go to **Synaptic Package Manager** via the **System > Administration** menus

**3** - Paste this: **linux-image-2** into the search box of **Synaptic Package Manager**

**4** - Once you have located the old kernels, **hightlight** them and **right-click** then select **Mark For Complete Removal** then click **Mark** and then click **Apply**

The results should show every available and installed kernel. A green box on the left indicates that the package is installed. The only linux-image you want installed is the latest one.

[COLOR="Red"]**Be careful of what you remove. Ensure that you don’t remove your current kernel, or anything that is not a linux-image. It is possible to break Ubuntu if you remove the wrong kernel.**[/COLOR]

Your computer and Grub menu should now be free of old kernels.

---

### Post by Rebelli0us on 2010-04-13
Success!  

I selected all but the latest "linux-headers" & "linux-image" files and "marked for complete removal". Boot menu is now clean and I assume the kernel files were also deleted. Sorry Linus but them old kernels have got to go ;)

Thank you.

---

