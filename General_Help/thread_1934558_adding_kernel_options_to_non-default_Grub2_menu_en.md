---
title: "adding kernel options to non-default Grub2 menu entry"
date: 2012-03-02
forum: General Help
---

### Post by adityavpratap on 2012-03-02
Hi!
I am trying to dual boot Ubuntu and openSuSE. Ubuntu is the default option in Grub2. I have to pass "i8042.nomux" option to the linux line in the openSuSE entry (which happens to be non-default). If I add this option to grub_cmdline_linux in /etc/default/grub, this line is added only to the Ubuntu entry in Grub2 while booting. How can I add it all the OS entries in the Grub menu during booting?
Thanking in advance,

---

### Post by oldfred on 2012-03-02
Do you need the same option for both Ubuntu & OpenSuse? What boot loader is OpenSuse now using grub or grub2?

My brute force solution would be just to copy boot entry to 40_custom and turn off os-prober. But then you have to manually update entry on every kernel update to OpenSuse. 

If OpenSuse is using grub legacy, you can install grub legacy to the OpenSuse partition and add a chainload entry to Ubunutu's 40_custom.

---

### Post by adityavpratap on 2012-03-02
Thanks for the prompt reply!

Yes, I want the same options "i8042.nomux" in both the OSs. 

I have installed Grub via Ubuntu but I haven't installed a bootloader in OpenSuSE.

---

### Post by oldfred on 2012-03-02
Did grub2's os-prober find you OpenSuse. I thought it normally read grub.cfg, menu.lst or other boot files to find the boot entries it uses. If so then it must also search for kernels and create its own entry.

---

### Post by adityavpratap on 2012-03-02
Ubuntu's Grub2 finds OpenSuSE without a problem. I am able to boot into both without any issues.

---

### Post by oldfred on 2012-03-02
I think I would install OpenSuSE's grub to the / (root) or /boot partition if it has one. Then you could chainload or when you add the parameter to the menu in OpenSuSE, I think Ubuntu's os-prober will pick up the entire entry including parameters.

---

### Post by adityavpratap on 2012-03-02
Ok!

I don't have a separate /boot partition. Can you suggest me a way of installing Grub2 in OpenSuSE on its root partition without breaking my system in the process? I don't have much experience with Grub2.

---

### Post by oldfred on 2012-03-03
I do not know how in OpenSuse.

In Ubuntu you can install easiest from your working system. Grub2 does not like to be installed to a partition as it does not have all the space it needs so it converts to blocklists which if actually using to boot may require updating on any grub changes. But it still works and if our real objective is just to create a good grub.cfg file it should be fine.

From Ubuntu this would be the way, you may have to convert for your system. This example is to install to sdb, but you may want sda5 or which ever partition your install is in. Often it will complain and you have to add a --force to make it work for a partition. I think only Debian use dpkg, so you may have to research how to do that if you even need those extra commands.

#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub
#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

Your case may be:

```
sudo grub-install /dev/sda5 --force
```

Ubuntu's grub2 gives this message:
> Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea.
Embedding is not possible, GRUB can only be installed in this setup by using blocklists. However blocklists are UNRELIABLE and its use is discouraged.
error: If you really want blocklists, use --force 


---

