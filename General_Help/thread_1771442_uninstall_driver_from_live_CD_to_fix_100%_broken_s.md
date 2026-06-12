---
title: "uninstall driver from live CD to fix 100% broken system???"
date: 2011-05-30
forum: General Help
---

### Post by pythonscript on 2011-05-30
I just installed a new driver from the Realtek site for my wireless chip, and it broke my system. Ubuntu won't boot in normal mode or recovery mode, and I'm sincerely hoping beyond all hope that I can avoid reinstalling the system I *just* got working yesterday.

At my connection speed, it will take about two days to download all of the packages I use. Is there any way to get rid of this driver and restore my system back to how it was... about twenty minutes before I posted this, without booting in the system?

Thank you!

---

### Post by coffeecat on 2011-05-30
A few points and questions.

Was there an uninstall script in the package you downloaded from the Realtek site? Perhaps you could post a link to where you downloaded it.

If there is an uninstall script then yes, in theory, you should be able to run it by chrooting into your broken installation from a live CD. If you want to know how to do that, please post back details of your partition layout. We need to know which partition your Ubuntu root partition is in.

If all this fails, you may not need to download all the packages again. If you haven't run 'sudo apt-get clean' they will still be sitting in the cache in /var/cache/apt/archives. It would be a simple matter to copy them to a USB drive with the live CD and then copy them into a new installation's /var/cache/apt/archives before running an update. The new system will detect their presence and not re-download any that are in the cache.

---

### Post by pythonscript on 2011-05-30
The instructions from Realtek said to uninstall the driver, I just needed to run "make uninstall." My Ubuntu installation is located on /dev/sda2, as well. /dev/sda1 is a Windows 7 installation, dev/sda2 is my Ubuntu root, /dev/sda3 is a shared NTFS partition that both OS's use, and /dev/sda4 is the swap partition. 

I've already run sudo apt-get clean several times since the installation of the packages, out of habit; it sounds like chrooting into my ubuntu root partition is probably the best way to go.

---

### Post by coffeecat on 2011-05-30
OK. I can't guarantee this will work - or rather the chroot will work - but I don't know about the Realtek side of the equation. Before you start, did you retain the folder in which you extracted the Realtek stuff? "make uninstall" needs a target which will be where you ran "make install".

Boot up the live CD and go to the live desktop. Open a terminal. Now, do these commands one after the other:

```
sudo mount /dev/sda2 /mnt
sudo mount -o bind /proc /mnt/proc
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /dev/pts /mnt/dev/pts
sudo mount -o bind /sys /mnt/sys
sudo cp -L /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt /bin/bash
```The sixth command - the copy of resolv.conf - is only necessary if you have connected to the internet in the live session and need to access the internet from your chroot. Otherwise, it can be safely omitted - I've merely included it for completeness.

You will then be confronted with a 'root@hostname:/#' prompt. The hostname will be that of the live session, but you are "in" your sda2 installation. The # signifies that you are root so be careful what you type. You will be in the root of the sda2 filesystem. You'll need to cd to wherever you ran 'make install' and then run 'make uninstall' from the chroot prompt. You don't need sudo.

Once you've done that, simply close the terminal and shut the live session down. Everything will be unmounted gracefully by shutting the live session down.

Good luck with that and tell us whether that fixes the problem.

---

### Post by pythonscript on 2011-05-30
Thank you very much for the help! I can boot my system now, but once I log in, wireless appears to be disabled and I don't know which module Ubuntu was using for the wireless chip in the first place. modprobe... <something>? I just don't remember which one.

EDIT: I think I've posted this in another thread, but the exact model of my wireless card (from the output of lspci -nn) is a Realtek RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01).

lspci -k shows no module loaded, either, but it shows the r8169 module is in use for the ethernet controller. Since the wireless shows up as "Device 8195," is it too simple to just load the "r8195" module, if that exists, and go from there? I'm afraid to try in case I mess up the boot again; hopefully I haven't uninstalled the module in any relatively permanent fashion.

---

### Post by coffeecat on 2011-05-30
I'm afraid I have next to no experience of Realtek wireless, and certainly not for a long time.

People who know about Realtek wireless may not necessarily look at this thread, considering its title. I suggest you start a new thread in the Networking and Wireless sub-forum. Good luck with that and I hope someone knowledgeable about Realtek wireless will notice your thread.

**EDIT**: sorry, I should have added: No, I don't think it's too simplistic to try 'modprobe r8195', but you may need to have the module loaded at bootup and make sure it's not blacklisted in /etc/modprobe.d/blacklist.conf.

---

### Post by pythonscript on 2011-05-30
Well I greatly appreciate the help in getting my system working again! I posted a new thread ([http://ubuntuforums.org/showthread.php?p=10882103](http://ubuntuforums.org/showthread.php?p=10882103)) so hopefully someone with more Realtek experience than either of us can help me out. If only the *connection* problem would go away once the wireless module actually gets working again. 

Thanks again!

---

