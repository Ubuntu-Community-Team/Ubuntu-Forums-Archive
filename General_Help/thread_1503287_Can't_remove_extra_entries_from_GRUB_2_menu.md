---
title: "Can't remove extra entries from GRUB 2 menu"
date: 2010-06-06
forum: General Help
---

### Post by Yoodle on 2010-06-06
I'm running Ubuntu 9.10 dual booted with Windows XP.  Ever since I installed 9.10, I get a long list of OS's (actually, multiple repeats of what appears to be the same Ubuntu install), and I can't get rid of them.

I've looked through various tutorials and the GRUB 2 Community documentation ([https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)) but I still can't get rid of the menu items.

I edited the 40_custom file and was able to add the entries I wanted to see, and then chmoded 644 all the other files in the /etc/grub.d directory and run update-grub.

The custom entries do appear at the end of the menu now, but the old entries are still there as well.  This is what I get when I run the update-grub:

```

yoodle@HANSOLO:/etc/grub.d$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-21-generic
Found kernel: /boot/vmlinuz-2.6.31-20-generic
Found kernel: /boot/vmlinuz-2.6.31-19-generic
Found kernel: /boot/vmlinuz-2.6.31-17-generic
Found kernel: /boot/vmlinuz-2.6.31-16-generic
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

Where is it pulling these kernels from?  Is it because of all of these files I have in /boot?

```

yoodle@HANSOLO:/boot$ ls
abi-2.6.31-14-generic         memtest86+.bin
abi-2.6.31-16-generic         System.map-2.6.31-14-generic
abi-2.6.31-17-generic         System.map-2.6.31-16-generic
abi-2.6.31-19-generic         System.map-2.6.31-17-generic
abi-2.6.31-20-generic         System.map-2.6.31-19-generic
abi-2.6.31-21-generic         System.map-2.6.31-20-generic
config-2.6.31-14-generic      System.map-2.6.31-21-generic
config-2.6.31-16-generic      vmcoreinfo-2.6.31-14-generic
config-2.6.31-17-generic      vmcoreinfo-2.6.31-16-generic
config-2.6.31-19-generic      vmcoreinfo-2.6.31-17-generic
config-2.6.31-20-generic      vmcoreinfo-2.6.31-19-generic
config-2.6.31-21-generic      vmcoreinfo-2.6.31-20-generic
grub                          vmcoreinfo-2.6.31-21-generic
initrd.img-2.6.31-14-generic  vmlinuz-2.6.31-14-generic
initrd.img-2.6.31-16-generic  vmlinuz-2.6.31-16-generic
initrd.img-2.6.31-17-generic  vmlinuz-2.6.31-17-generic
initrd.img-2.6.31-19-generic  vmlinuz-2.6.31-19-generic
initrd.img-2.6.31-20-generic  vmlinuz-2.6.31-20-generic
initrd.img-2.6.31-21-generic  vmlinuz-2.6.31-21-generic

```


These are the menu entry items from grub.cfg:
```

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-21-generic" {
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode)" {
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
### END /etc/grub.d/10_linux ###

```

I miss menu.lst...

---

### Post by spiky001 on 2010-06-06
you can remove them with syaptic manager use the search part put in linux headers it will allow you to remove them, it is best to leave latest 1 + previous 1

---

### Post by scouser73 on 2010-06-06
> **Yoodle said:**
> I'm running Ubuntu 9.10 dual booted with Windows XP.  Ever since I installed 9.10, I get a long list of OS's (actually, multiple repeats of what appears to be the same Ubuntu install), and I can't get rid of them.

I've looked through various tutorials and the GRUB 2 Community documentation ([https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)) but I still can't get rid of the menu items.

I edited the 40_custom file and was able to add the entries I wanted to see, and then chmoded 644 all the other files in the /etc/grub.d directory and run update-grub.

The custom entries do appear at the end of the menu now, but the old entries are still there as well.  This is what I get when I run the update-grub:

```

yoodle@HANSOLO:/etc/grub.d$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-21-generic
Found kernel: /boot/vmlinuz-2.6.31-20-generic
Found kernel: /boot/vmlinuz-2.6.31-19-generic
Found kernel: /boot/vmlinuz-2.6.31-17-generic
Found kernel: /boot/vmlinuz-2.6.31-16-generic
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

Where is it pulling these kernels from?  Is it because of all of these files I have in /boot?

```

yoodle@HANSOLO:/boot$ ls
abi-2.6.31-14-generic         memtest86+.bin
abi-2.6.31-16-generic         System.map-2.6.31-14-generic
abi-2.6.31-17-generic         System.map-2.6.31-16-generic
abi-2.6.31-19-generic         System.map-2.6.31-17-generic
abi-2.6.31-20-generic         System.map-2.6.31-19-generic
abi-2.6.31-21-generic         System.map-2.6.31-20-generic
config-2.6.31-14-generic      System.map-2.6.31-21-generic
config-2.6.31-16-generic      vmcoreinfo-2.6.31-14-generic
config-2.6.31-17-generic      vmcoreinfo-2.6.31-16-generic
config-2.6.31-19-generic      vmcoreinfo-2.6.31-17-generic
config-2.6.31-20-generic      vmcoreinfo-2.6.31-19-generic
config-2.6.31-21-generic      vmcoreinfo-2.6.31-20-generic
grub                          vmcoreinfo-2.6.31-21-generic
initrd.img-2.6.31-14-generic  vmlinuz-2.6.31-14-generic
initrd.img-2.6.31-16-generic  vmlinuz-2.6.31-16-generic
initrd.img-2.6.31-17-generic  vmlinuz-2.6.31-17-generic
initrd.img-2.6.31-19-generic  vmlinuz-2.6.31-19-generic
initrd.img-2.6.31-20-generic  vmlinuz-2.6.31-20-generic
initrd.img-2.6.31-21-generic  vmlinuz-2.6.31-21-generic

```


These are the menu entry items from grub.cfg:
```

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-21-generic" {
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode)" {
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
### END /etc/grub.d/10_linux ###

```

I miss menu.lst...

Hi Yoodle, you can either remove the old grub entries via Synaptic Package Manager, or a much easier way is to do it via Ubuntu Tweak.

Firstly, go to [[COLOR="Red"]**Ubuntu Tweak**[/COLOR]]("http://ubuntu-tweak.com/"), download and install the software.

Once you have Ubuntu Tweak installed, you will find it under the **System Tools** menu.

Click on it, and once it's loaded select **Package Cleaner**, click on **Unlock** in the bottom right-hand corner & enter your password when prompted.

Then click on **Clean Kernels**, now you will see a list of old kernels that you no longer need. Click **Cleanup** and the old grub entries will be removed and it will keep only the newest version installed.

---

