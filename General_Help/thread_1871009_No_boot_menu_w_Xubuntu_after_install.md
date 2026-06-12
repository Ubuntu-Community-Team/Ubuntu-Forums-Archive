---
title: "No boot menu w/ Xubuntu after install"
date: 2011-10-28
forum: General Help
---

### Post by geovino on 2011-10-28
I wanted to share a hdd with Ubuntu11.10 and Xubuntu 11.10. but after installing Ubuntu on a hdd with Xubuntu already installed on it, no boot menu. It goes straight to Ubuntu. 

Many years ago I used to edit a file to fix this. What is that file and what would the entry be to have Xubuntu as the second choice?

---

### Post by ajgreeny on 2011-10-28
You have not given us enough information about what exactly you did when you installed the ubuntu alongside xubuntu.  Grub from the second installation should have found the first OS and added it automatically to the grub menu, so something has gone wrong.

From the OS that you are able to boot to please use command ```
sudo fdisk -l
``` to let us see the partition layout on your machine;  it sounds as if you may have overwritten the first OS with the second, but let's not make assumptions just yet.

It would also be useful if you use the boot-info-script link in my signature, and download and run the script, then copy the RESULTS.txt file it produces back here between code tags, (use the # icon in the toolbar).

---

### Post by geovino on 2011-10-28
here it is:

davek@dave-sys:~$ sudo fdisk -l
[sudo] password for davek: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000de51b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   253893474   126946706   83  Linux
/dev/sda2       253894654   488392064   117248705+   5  Extended
/dev/sda5       484456203   488392064     1967931   82  Linux swap / Solaris
/dev/sda6       253894656   480526335   113315840   83  Linux
/dev/sda7       480528384   484454399     1963008   82  Linux swap / Solaris

Partition table entries are not in disk order
davek@dave-sys:~$

---

### Post by geovino on 2011-10-28
here's a screen shot of gparted. I see that there are two swaps. Maybe that is the problem?

---

### Post by ajgreeny on 2011-10-28
No, the two swaps would not be causing that problem.  Can you run sudo update-grub in terminal then reboot and see if you get the option for both OSs.

If that is no help, can you please show the output from the command ```
grep menuentry /boot/grub/grub.cfg
``` and also from ```
cat /etc/default/grub
```

Please also use the **boot-info-script** as I asked in my first post.

---

### Post by geovino on 2011-10-28
Thanks but the command didn't do anything.

Here's the output:

davek@dave-sys:~$ grep menuentry /boot/grub/grub.cfg
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
davek@dave-sys:~$ 

davek@dave-sys:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
davek@dave-sys:~$

---

### Post by geovino on 2011-10-28
> **ajgreeny said:**
> You have not given us enough information about what exactly you did when you installed the ubuntu alongside xubuntu.  Grub from the second installation should have found the first OS and added it automatically to the grub menu, so something has gone wrong.

From the OS that you are able to boot to please use command ```
sudo fdisk -l
``` to let us see the partition layout on your machine;  it sounds as if you may have overwritten the first OS with the second, but let's not make assumptions just yet.

It would also be useful if you use the boot-info-script link in my signature, and download and run the script, then copy the RESULTS.txt file it produces back here between code tags, (use the # icon in the toolbar).

I extracted the script but didn't see any RESULTS.txt file. sorry.

Isn't there a grub file that can be edited? Seems like it used to be simpler to fix.

---

### Post by ajgreeny on 2011-10-28
> **geovino said:**
> I extracted the script but didn't see any RESULTS.txt file. sorry.

Isn't there a grub file that can be edited? Seems like it used to be simpler to fix.
Having extracted the script file you need to run it as is explained in the instructions on the web-page that the link takes you to.  It is all shown in some detail there.

The file that might have needed editing is the one you posted from the *cat /etc/default/grub* command, but that is fine, so no worries there.

---

### Post by geovino on 2011-10-28
> **ajgreeny said:**
> Having extracted the script file you need to run it as is explained in the instructions on the web-page that the link takes you to.  It is all shown in some detail there.

The file that might have needed editing is the one you posted from the *cat /etc/default/grub* command, but that is fine, so no worries there.

I've got the Results.txt now, but its very large. How do I paste it in so its not so big?

---

### Post by geovino on 2011-10-28
I uploaded it.

---

### Post by ajgreeny on 2011-10-28
I can not see much wrong with the RESULTS.txt file, but I note that one of the two grub.cfg files shown, from sda1, has just the single OS listed, your ubuntu, but the other on sda6 has both OSs listed, so I think running the *sudo update-grub* command should put everything right for you, and get you the grub menu you want.

You can always show the grub menu by holding shift immediately after pressing the power button, but with xubuntu on sda6 I am surprised that it did not take over the boot sequence itself.  Did you allow the bootloader files to be put onto the MBR of sda when you installed xubuntu, or did you put it on a separate partition, because strangely the system is still looking at sda1 for the configuration files for grub.

PS:  Have you tried rebooting after running the *sudo update-grub* command to see if it has made any difference?   You should have seen some output in terminal when you ran the command something like```
$ sudo update-grub
[sudo] password for *user*: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-30-generic
Found initrd image: /boot/initrd.img-2.6.35-30-generic
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found linux image: /boot/vmlinuz-2.6.32-34-generic
Found initrd image: /boot/initrd.img-2.6.32-34-generic
Found memtest86+ image: /boot/memtest86+.bin
done
```
If you see nothing, the command has not run.

---

### Post by geovino on 2011-10-28
this is what I get:

davek@dave-sys:~$ sudo update-grub
[sudo] password for davek: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 11.10 (11.10) on /dev/sda1
done
davek@dave-sys:~$ 


Back in the old days, you would give me a command that opened the grub file and I would add or delete an entry and that would get the boot menu to show up. maybe with grub2 you can't do that anymore. this is why a rarely partition hard drives anymore, because its easier to plug in another hdd and install a distro on the whole hdd. this was a test to see if Ubuntu could partition the drive and have two distros on one hdd. It failed. 

Otherwise I'll reinstall either Ubuntu or Xubuntu and leave it at that. 
Thanks for your time.

---

### Post by ajgreeny on 2011-10-29
I am still baffled by this.  I have four OSs on one of my drives and grub has moved from the first of those to the fourth as I've installed, with never a hic-cup in the booting.

Sorry we could not get it to work properly so far.  All I can suggest is trying to re-install grub to the mbr with a live CD using [Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275") with a live CD making sure you use sda6 as the root partition;  at the moment grub menu still seems to not show for reasons I can not fathom.  []("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by geovino on 2011-10-29
> **ajgreeny said:**
> I am still baffled by this.  I have four OSs on one of my drives and grub has moved from the first of those to the fourth as I've installed, with never a hic-cup in the booting.

Sorry we could not get it to work properly so far.  All I can suggest is trying to re-install grub to the mbr with a live CD using [Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275") with a live CD making sure you use sda6 as the root partition;  at the moment grub menu still seems to not show for reasons I can not fathom.  []("http://ubuntuforums.org/showthread.php?t=1195275")

Thanks for all your help. I'll just use Ubuntu for now. the Grub2 basics looks too confusing,if I try I'll loose both and have to start all over again so I'll pass on it. The old Grub was much easier. 

Since I never use more than 80gb on any hdd the 111gb on sda6 is OK. One thing I do like about Ubuntu 11.10 is the clarity of the fonts, a little sharper than in Xubuntu.

---

### Post by ajgreeny on 2011-10-30
Did you try holding shift at bootup to get the menu to show?  You should then be able to choose xubuntu from the choices available, though it will still show as ubuntu in the menu.  Once you are in xubuntu run ```
sudo grub-install /dev/sda
``` and you should then be using xubuntu's grub, not that from ubuntu

EDIT:
Sorry, I think I got that bthe wrong way round with the xubuntu/ubuntu choice, but I hope you still can get the idea.

---

### Post by geovino on 2011-10-30
> **ajgreeny said:**
> Did you try holding shift at bootup to get the menu to show?  You should then be able to choose xubuntu from the choices available, though it will still show as ubuntu in the menu.  Once you are in xubuntu run ```
sudo grub-install /dev/sda
``` and you should then be using xubuntu's grub, not that from ubuntu

EDIT:
Sorry, I think I got that bthe wrong way round with the xubuntu/ubuntu choice, but I hope you still can get the idea.

Thanks again, but when booting up and holding down the shift key, it didn't bring up any boot menu. I ended up running a live CD of Parted Magic and resized the Xubuntu to 25gb and enlarged the Ubuntu by 100gb and will use Ubuntu from now on.

---

### Post by ajgreeny on 2011-10-30
> **geovino said:**
> Thanks again, but when booting up and holding down the shift key, it didn't bring up any boot menu. I ended up running a live CD of Parted Magic and resized the Xubuntu to 25gb and enlarged the Ubuntu by 100gb and will use Ubuntu from now on.
OK, and good luck with the ubuntu installation, which you obviously like.

I still do not understand why the grub menu does not appear, particularly when you hold shift at boot;  it always works on my machines when there is only one OS installed, and if there is more than one OS it always appears automatically.

Baffling!!

---

