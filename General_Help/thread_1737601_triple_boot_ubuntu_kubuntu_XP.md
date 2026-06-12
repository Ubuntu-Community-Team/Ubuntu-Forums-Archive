---
title: "triple boot ubuntu kubuntu XP"
date: 2011-04-23
forum: General Help
---

### Post by athalsten on 2011-04-23
can i set up triple boot
1 xp
2 ubuntu
3. kubuntu?

what is the process?

---

### Post by stunet on 2011-04-23
I never tripled-booted a machine, but my advice would be to do xp first since ms like to overrule you a lot lol :)

you can do the other two in any order you like as they will detect each other upon installation. you will get a warning that theres another os installed and if you want to just partition a chunk for that os.

linux will also create the grub setup for you (ms has their own, but its a bear to setup)

here is a great article on this, they have other versions of this, so its worth looking at :)

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

---

### Post by SavageWolf on 2011-04-23
If you like, you can install kubuntu-desktop or ubuntu-desktop in (K)Ubuntu, and you can combine them, choosing which one to use on login.

---

### Post by Habeouscorpus on 2011-04-23
To do it, you'll need to create an extended partition. 

What I would do:

1. Install XP. 
2. Resize it so it takes up 1/3 of the disk.
3. Boot to a live disk, and make the free space an extended partition.
4. Install the other two anyway you like on the partition.

---

### Post by beew on 2011-04-23
Yes, but you have to make sure you install grub correctly.

Install XP first as others say.

Then boot to a Ubuntu live usb and  use gparted to shrink Windows and then created an extended partition in the unallocated space, then create 5 logical partitions within it.  You need 2 partitions of about 15Gs for the / partitions of the two Ubuntus, and two partitions of whatever size  /home partitions for the Ubuntus. All these should be ext4 partitions and you don't need to label them.

The home partitions are for storing data and settings so they need to be roomy enough (but in a multiboot you may want to store your data in a separate share partition, if so that needs to be created separately and your home partitions don't have to be so big) Finally a Swap partition about the 1.5 x ram.

Then  install  Ubuntu, it doesn't matter which one but the first one you install would control grub.  Choose install and then on the partition step choose partition manually, then assign one of the partitions you made earlier as / and another as /home and then install. The grub loader will be installed in sda and this version of Ubuntu would control grub. Finish the install.

Next boot into the live usb for the other Ubuntu and do exactly the same EXCEPT you don't want its grub to overwrite the one in the first Ubuntu. For some Linux distros such as Fedora there is an option of not installing bootloader, but in Ubuntu apparently that is absent, so you have to install it in the partition where this second copy of Ubuntu is so it won't interfere with the first grub (so, you would install the bootloader in sda3, say, instead of sda)

After finish installing the second Ubuntu, reboot and log into the first Ubuntu (which controls grub) at this point you probably don't see the second Ubuntu on the boot menu. After logging into the first Ubuntu go to the terminal and run
 ```
sudo update-grub

```Then grub will detect the second Ubuntu and next time when you log in you would see it in the boot menu.

Also you may need to run sudo update-grub in the first Ubuntu everytime the second Ubuntu has a kernel update, or the kernel may not function properly.

You can multiboot as many Linux distros as your hard disk can handle this way,--I have 5 Linuxes multibooting from one external drive, but I think you are limited to one Windows probably (even dual booting two Windows is not that simple from what I heard, but I hardly use Windows anymore)

---

### Post by rummy77 on 2011-04-23
I'm with SavageWolf.  Leave xp on your computer.  Install ubuntu to dual boot.  Then install the Kubuntu package from the software center, and you can choose whether to use the ubuntu or Kubuntu desktop when you get to the login screen.  For that matter you can install Xubuntu and Unity as well, and be totally tricked out.

---

### Post by oldfred on 2011-04-23
I am more with beew on dual booting.

I installed K desktop but did not like it several versions ago. When I went to uninstall it messed up settings. I could not easily uninstall everything K related as I like k3b & Kmymoney which require a lot of the underlying packages.

Much cleaner just to dual boot. I plan on trying Kubuntu again after 11.04 is out. I have several extra / partitions just for trying out things.

---

### Post by athalsten on 2011-04-23
> **SavageWolf said:**
> If you like, you can install kubuntu-desktop or ubuntu-desktop in (K)Ubuntu, and you can combine them, choosing which one to use on login.



but how can u explain?:confused:

---

### Post by oldfred on 2011-04-23
While I do not recommend it these are the meta packages that install other desktops:

The key meta packages of Ubuntu are :
ubuntu-base (the whole base system which everybody should install)
ubuntu-desktop (the whole gnome environment)
kubuntu-desktop (the whole kde environment)
xubuntu-desktop (the whole xfce4 environment)
edubuntu-desktop (the whole kids/schools oriented gnome environment)

Install like this.
sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm restart
sudo service gdm start

On the log in screen they is a choice of which to use.

---

### Post by jannytra on 2012-01-25
First I would like to thank beew for the information he provided, it helped a lot :)

I would like to ask something about grub - I have a dual-boot setup of Windows 7 and Ubuntu 10.04 as follows:

sda1, sda2 - Win7
sda5, sda6 (swap), sda7 - Ubuntu 10.04
sda8, sda9 (swap), sda10 - empty
sda4 - common NTFS storage partition.

Right now, I would like to add another Ubuntu 10.04 which I would use for music production. My question is: where will those entries appear in the grub menu? If I understand right from what I read - that new Ubuntu should be recognized by os_prober and therefore placed after the Windows 7 entry? :) (right now I have my Ubuntu kernels listed, memtest+86 and than Windows 7)

---

### Post by oldfred on 2012-01-25
I think os-prober just posts them in the order found. But you can reorder to whatever you want.

HOWTO: Grub Customizer Updated for grub 1.99
[http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html](http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html) 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
The Grub 2 Guide (formerly Grub 2 Basics) manual way
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by jannytra on 2012-01-26
Thank you, I just wanted to make sure that os_prober will be the one that will find my second Ubuntu, so that I will be able to detect it in the menu (I already have Grub Customizer, nice GUI tool to eliminate unwanted entries in grub menu). I am still learning a lot, so help is appreciated :)

OK, I installed another Ubuntu as I planned and during installation I chose not to install boot loader - and now my grub only shows that Ubuntu as 1 entry, no way to choose kernel to load :( would that be fixed by additionally manually installing grub to the root partition of the newly installed Ubuntu via a LiveCD?

---

### Post by oldfred on 2012-01-26
The os-prober looks for grub.cfg, menu.lst and other grub boot files and copies/edits the entries to boot. I thought if it found a kernel it created its own boot entry, but maybe not. So if you did not install any grub, you do not have any grub.cfg file to copy from. 

You can install grub to the PBR (and in effect never use it) or you can add a partition boot entry to 40_custom. The advantage of the partition boot entry is that it will always boot the most current kernel without having to update grub in both systems to get both menus updated.

I first saw this from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition using links in / (root) that Ubuntu keeps updated.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

gksudo gedit /etc/grub.d/40_custom
sudo update-grub

---

### Post by jannytra on 2012-01-26
Thank you for your help and suggestions. I decided to take the easy way - I reinstalled the second Ubuntu, but this time installing grub to the / partition of that Ubuntu and after updating grub in my main Ubuntu, entries for kernels of the second one appeared in grub menu :)

---

