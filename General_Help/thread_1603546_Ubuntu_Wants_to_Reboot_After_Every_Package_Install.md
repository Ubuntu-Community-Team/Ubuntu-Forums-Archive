---
title: "Ubuntu Wants to Reboot After Every Package Installation"
date: 2010-10-22
forum: General Help
---

### Post by freeware.preacher on 2010-10-22
I'm running Ubuntu 10.10 and every time I install a program (either from the center or from the terminal), my power button turns red telling me I have to restart to complete the update and I get an error message saying: 

Package operation failed. The installation or removal of a software package failed.

Details>
> installArchives() failed: Selecting previously deselected package python-bluez. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 213516 files and directories currently installed.) 
Unpacking python-bluez (from .../python-bluez_0.18-1_i386.deb) ... 
Selecting previously deselected package gtkwhiteboard. 
Unpacking gtkwhiteboard (from .../gtkwhiteboard_1.3+dfsg-5.2ubuntu1_all.deb) ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_CA.UTF8.cache... 
Processing triggers for desktop-file-utils ... 
Processing triggers for menu ... 
Processing triggers for man-db ... 
Processing triggers for python-support ... 
Setting up linux-image-2.6.35-22-generic (2.6.35-22.35) ... 
Running depmod. 
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic 
Not updating initrd symbolic links since we are being updated/reinstalled  
(2.6.35-22.34 was configured last, according to dpkg) 
Not updating image symbolic links since we are being updated/reinstalled  
(2.6.35-22.34 was configured last, according to dpkg) 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic 
 * dkms: running auto installation service for kernel 2.6.35-22-generic 
 
 *       bcmwl (5.60.48.36+bdcom)... 
   ...done. 
 *       virtualbox-ose (3.2.8)... 
   ...done. 
 *       nvidia-current (260.19.06)... 
   ...done. 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic 
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic 
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic 
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic 
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic 
/etc/default/grub: 23: Syntax error: newline unexpected 
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-22-generic.postinst line 1010. 
dpkg: error processing linux-image-2.6.35-22-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up python-bluez (0.18-1) ... 
No apport report written because MaxReports is reached already
Processing triggers for python-central ... 
Setting up gtkwhiteboard (1.3+dfsg-5.2ubuntu1) ... 
Processing triggers for menu ... 
Processing triggers for python-central ... 
Errors were encountered while processing: 
 linux-image-2.6.35-22-generic 
localepurge: checking for existence of /var/cache/localepurge... 
localepurge: checking for existence of /var/cache/localepurge/localelist... 
localepurge: checking system for new locale ... 
localepurge: processing locale files ... 
localepurge: Disk space freed in /usr/share/locale: 0 KiB 
localepurge: processing man pages ... 
localepurge: Disk space freed in /usr/share/man: 0 KiB 
localepurge: processing Gnome files ... 
localepurge: Disk space freed in /usr/share/gnome/help: 8 KiB 
localepurge: processing Omf files ... 
localepurge: Disk space freed in /usr/share/omf: 0 KiB 
localepurge: processing KDE files ... 
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB 
 
Total disk space freed by localepurge: 8 KiB 
 
localepurge: checking for existence of /var/cache/localepurge... 
localepurge: checking for existence of /var/cache/localepurge/localelist... 
localepurge: checking system for new locale ... 
localepurge: processing locale files ... 
localepurge: Disk space freed in /usr/share/locale: 0 KiB 
localepurge: processing man pages ... 
localepurge: Disk space freed in /usr/share/man: 0 KiB 
localepurge: processing Gnome files ... 
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB 
localepurge: processing Omf files ... 
localepurge: Disk space freed in /usr/share/omf: 0 KiB 
localepurge: processing KDE files ... 
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB 
 
Total disk space freed by localepurge: 0 KiB 
 
Setting up linux-image-2.6.35-22-generic (2.6.35-22.35) ... 
Running depmod. 
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic 
Not updating initrd symbolic links since we are being updated/reinstalled  
(2.6.35-22.34 was configured last, according to dpkg) 
Not updating image symbolic links since we are being updated/reinstalled  
(2.6.35-22.34 was configured last, according to dpkg) 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic 
 * dkms: running auto installation service for kernel 2.6.35-22-generic 
 
 *       bcmwl (5.60.48.36+bdcom)... 
   ...done. 
 *       virtualbox-ose (3.2.8)... 
   ...done. 
 *       nvidia-current (260.19.06)... 
   ...done. 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic 
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic 
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic 
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic 
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic 
/etc/default/grub: 23: Syntax error: newline unexpected 
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-22-generic.postinst line 1010. 
dpkg: error processing linux-image-2.6.35-22-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2 
The program was clearly installed, and when I reboot, the red power button goes away.

What's wrong?

---

### Post by sikander3786 on 2010-10-22
The problems lies here.

> Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-22-generic.postinst line 1010. 

Try this from terminal and post the output.

```
sudo dpkg --configure -a
```

And here

> /etc/default/grub: 23: Syntax error: newline unexpected 

Post the contents of your /etc/default/grub file by,

```
gedit /etc/default/grub
```

---

### Post by yetiman64 on 2010-10-22
> **sikander3786 said:**
> ....
```
sudo gedit /etc/default/grub
```
 
@ sikander3786, rather than the OP opening that file in a root editor just for accessing the contents for posting (the potential for accidental changes is very high), maybe the command,
```
cat /etc/default/grub
```would be better. btw gedit is a graphical application and as such the use of "gksudo" is also recommended. Link #4 in my sig, "Graphical Sudo" section explains why. Hope this is of some help.

Edit: or even just consider removing the sudo as there is no need to actually edit the file, just to open it "read only"

---

### Post by sikander3786 on 2010-10-22
> **yetiman64 said:**
> @ sikander3786, rather than the OP opening that file in a root editor just for accessing the contents for posting (the potential for accidental changes is very high), maybe the command,
```
cat /etc/default/grub
```would be better. btw gedit is a graphical application and as such the use of "gksudo" is also recommended. Link #4 in my sig, "Graphical Sudo" section explains why. Hope this is of some help.

Edit: or even just consider removing the sudo as there is no need to actually edit the file, just to open it "read only"
Ahhh. I keep on making that mistake. Feeling a bit heavy headed due to work load overnight. Thanks for pointing out. Just updated the code in above post.

---

### Post by yetiman64 on 2010-10-22
You're welcome, :)

---

### Post by freeware.preacher on 2010-10-23
sudo dpkg --configure -a

> Setting up linux-image-2.6.35-22-generic (2.6.35-22.35) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.35-22.34 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.35-22.34 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
 * dkms: running auto installation service for kernel 2.6.35-22-generic         
 *       bcmwl (5.60.48.36+bdcom)...                                     [ OK ] 
 *       virtualbox-ose (3.2.8)...                                       [ OK ] 
 *       nvidia-current (260.19.06)...                                   [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
/etc/default/grub: 23: Syntax error: newline unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-22-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.35-22-generic

My power button also prompted me to reboot.

cat /etc/default/grub
> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=>>1204x768-24<<,mtrr=3,scroll=ywrap"
GRUB_CMDLINE_LINUX=" vga=769"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=>>1204x768-24<<

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


Thanks for the help guys, this i why I love the Linux community.

---

### Post by sikander3786 on 2010-10-23
Edit /etc/default/grub by,

```
gksudo gedit /etc/default/grub
```

Comment this line with # at start

> GRUB_GFXMODE=>>1204x768-24<<

So it looks like

```
#GRUB_GFXMODE=>>1204x768-24<<
```

Save and close. Now update your grub.cfg by,

```
sudo update-grub
```

Now try to reconfigure the packages.

```
sudo dpkg --configure -a
```

I hope it reports no errors this time.

Note: You can always have custom resolutions for your Grub menu. Commenting that line means that it will revert to its defaults. I have never tweaked Grub resolution. If you want to, you can change the line to

```
GRUB_GFXMODE=1024x768
```

instead of commenting it and later run update-grub.

More info here.

[https://wiki.ubuntu.com/Grub2#grub%20%28/etc/default/grub%29](https://wiki.ubuntu.com/Grub2#grub%20%28/etc/default/grub%29)

---

### Post by freeware.preacher on 2010-10-23
Yeah... Well, at first I did that, and I couldn't boot, as my Ubuntu Desktop entry was removed from grub. I had to boot from my install CD to recover it. 

One line had to be changed too:

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

When I rebooted and ran > grub-update everything worked fine.

All in all, I'm happy, but a lesser geek might have spazzed.

Thanks guys!

---

