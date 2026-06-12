---
title: "Kernel upgrade problem"
date: 2011-07-02
forum: General Help
---

### Post by srisharan on 2011-07-02
Yesterday my update manager showed some updates related to the Linux kernel.I didn't exactly bother to see what they are and updated them.I then restarted the system when it asked to restart.But now every time in install or remove or upgrade any small thing it also does something,i dont exactly know what it is related to the kernel and shows an error message.It also asks me restart the system again.I removed totem from via the terminal and this is what i get after totem is removed> Processing triggers for python-support ...
Setting up linux-image-2.6.35-30-generic-pae (2.6.35-30.54) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-30-generic-pae
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-30-generic-pae /boot/vmlinuz-2.6.35-30-generic-pae
 * dkms: running auto installation service for kernel 2.6.35-30-generic-pae                                                                                     
 *       virtualbox-ose (3.2.8)...                                       [ OK ] 
 *       nvidia-current (260.19.06)...                                   [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-30-generic-pae /boot/vmlinuz-2.6.35-30-generic-pae
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-30-generic-pae /boot/vmlinuz-2.6.35-30-generic-pae
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-30-generic-pae /boot/vmlinuz-2.6.35-30-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-30-generic-pae /boot/vmlinuz-2.6.35-30-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-30-generic-pae /boot/vmlinuz-2.6.35-30-generic-pae
Searching for GRUB installation directory ... found: /boot/grub
/etc/default/grub: line 24: unexpected EOF while looking for matching ``'
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-30-generic-pae.postinst line 1010.
dpkg: error processing linux-image-2.6.35-30-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-2.6.35-30-generic-pae; however:
  Package linux-image-2.6.35-30-generic-pae is not configured yet.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 2.6.35.30.38); however:
  Package linux-image-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 linux-image-2.6.35-30-generic-pae
 linux-image-generic-pae
 linux-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)

This is not just irritating but also I am afraid it might break my system if i don't fix it.If anyone knows what the problem is or what to do please help me.I use Ubuntu 10.10.

---

### Post by sanderd17 on 2011-07-02
try
```

sudo dpkg --configure linux-generic-pae

```

And report the errors you got, or report that it worked.

---

### Post by srisharan on 2011-07-02
When I run that command i get:

> dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 2.6.35.30.38 ); however:
  Package linux-image-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-generic-pae

My current Linux kernel version is 2.6.35-28

---

### Post by dino99 on 2011-07-02
as you can see into your post, you need to solve that error first:

/etc/default/grub: line 24: unexpected EOF while looking for matching ``'

so watch that line 24 and correct it

sudo gedit /etc/default/grub

when corrected: sudo update-grub

---

### Post by srisharan on 2011-07-02
Already tried doing that as that was the only part of the error report I could understand.:o However the 24th line of /etc/default/grub says 

**# you can see them in real GRUB with the command `vbeinfo'**

Didn't understand what to do with it,as it is a comment.So left it as it is.Perhaps if you can see and tell me what that line is on the same file on your computer and I can correct it

---

### Post by sanderd17 on 2011-07-02
Thank you dino99, I didn't notice that part.

@srisharan, can you post your entire /etc/default/grub? (please use CODE tags and not QUOTE, click on the # in the editor mode).

---

### Post by srisharan on 2011-07-02
Sure here it is;

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=800x600 -16@50,mtrr=3,scroll=ywrap
GRUB_CMDLINE_LINUX=" splash"
GRUB_GFXPAYLOAD_LINUX="800x600"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
GRUB_GFXMODE="1280x800"


```

---

### Post by sanderd17 on 2011-07-02
> **srisharan said:**
> Sure here it is;

```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=800x600 -16@50,mtrr=3,scroll=ywrap

```

This line doesn't have a close ".

---

### Post by srisharan on 2011-07-02
> **sanderd17 said:**
> This line doesn't have a close ".

Closed the line.Didn't solve the problem.Still getting the same message on running sudo dpkg --configure linux-generic-pae

---

### Post by sanderd17 on 2011-07-02
can you do 
```

sudo update-grub

```
and retry?

---

### Post by srisharan on 2011-07-02
Still get the same message after updating grub :(

---

### Post by rad_sci_guy on 2011-07-02
My acer aspire 5040 laptop doesn't even boot up with this kernel.  I get a black screen with a blinking cursor at the top and nothing else happens.  Can't even ctr-alt-del to restart.  Have to use the power button to turn off system then reboot into the previous kernel.

I hate kernel updates.

---

### Post by srisharan on 2011-07-02
> **rad_sci_guy said:**
> My acer aspire 5040 laptop doesn't even boot up with this kernel. 

Which kernel verion do you have?Mine was supposed to update to 2.35-30 but didn't.I still am with 35-28.So maybe i should count myself lucky that it didn't update :D

---

### Post by sanderd17 on 2011-07-02
Otherwise I would do a purge remove and then reinstall, but honestly, since it's the kernel, I don't dare.

---

### Post by srisharan on 2011-07-02
ya i get what you mean.but really kernel upgrades can be such a pain sometimes

---

### Post by srisharan on 2011-07-02
Solved it myself.Kind of an accident.Removed the file /var/lib/dpkg/lock.Then configured dpkg; sudo dpkg --configure -a.Then it prompted me to restart again but this time the terminal showed that the update was complete and didn't show any errors.So I restarted and its gone now.

Thanks to sandnerd17 and dino99 for helping me.Marking this as closed now

---

### Post by rad_sci_guy on 2011-07-02
> **srisharan said:**
> Which kernel verion do you have?Mine was supposed to update to 2.35-30 but didn't.I still am with 35-28.So maybe i should count myself lucky that it didn't update :D

I also upgraded to 2.6.35-30.  I noticed that the hard drive light would flash when I pressed on enter.  So I continued to press enter until the ubuntu splash screen came on and then the system login showed up.

I have repeated this on a reboot from a shutdown.  So I have to continually press enter until the splash screen appears.

---

### Post by mordalo on 2011-08-02
> **srisharan said:**
> Solved it myself.Kind of an accident.Removed the file /var/lib/dpkg/lock.Then configured dpkg; sudo dpkg --configure -a.Then it prompted me to restart again but this time the terminal showed that the update was complete and didn't show any errors.So I restarted and its gone now.

Thanks to sandnerd17 and dino99 for helping me.Marking this as closed now

I've had this same problem for awhile and this didn't resolve it for me.
I removed the lock file and then configured dpkg, and this is what I got.  Any suggestions?

```
$ sudo dpkg --configure -a
Setting up linux-image-2.6.35-30-generic (2.6.35-30.56) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-30-generic
/usr/share/initramfs-tools/hooks/compcache: 1: application/relaxng: not found
/usr/share/initramfs-tools/hooks/compcache: 2: inode/vnd.kde.device.printer: not found
/usr/share/initramfs-tools/hooks/compcache: 3: application/vnd.oasis.opendocument.image: not found
/usr/share/initramfs-tools/hooks/compcache: 4: interface/x-winamp-skin: not found
/usr/share/initramfs-tools/hooks/compcache: 5: application/x-designer: not found
/usr/share/initramfs-tools/hooks/compcache: 6: inode/vnd.kde.service.afpovertcp: not found
/usr/share/initramfs-tools/hooks/compcache: 7: image/x-portable-bitmap: not found
/usr/share/initramfs-tools/hooks/compcache: 8: application/x-smb-workgroup: not found
/usr/share/initramfs-tools/hooks/compcache: 9: application/rtf: not found
/usr/share/initramfs-tools/hooks/compcache: 10: text/x-rpm-spec: not found
/usr/share/initramfs-tools/hooks/compcache: 11: application/x-theme: not found
/usr/share/initramfs-tools/hooks/compcache: 12: application/x-shared-library-la: not found
/usr/share/initramfs-tools/hooks/compcache: 13: text/x-dsl: not found
/usr/share/initramfs-tools/hooks/compcache: 14: application/x-reject: not found
/usr/share/initramfs-tools/hooks/compcache: 15: text/x-haskell: not found
/usr/share/initramfs-tools/hooks/compcache: 16: application/x-webarchive: not found
/usr/share/initramfs-tools/hooks/compcache: 17: application/x-webarchive: not found
/usr/share/initramfs-tools/hooks/compcache: 18: image/x-sigma-x3f: not found
/usr/share/initramfs-tools/hooks/compcache: 19: application/x-kns: not found
/usr/share/initramfs-tools/hooks/compcache: 20: inode/vnd.kde.service.telnet: not found
/usr/share/initramfs-tools/hooks/compcache: 21: text/html: not found
/usr/share/initramfs-tools/hooks/compcache: 22: text/x-eiffel: not found
/usr/share/initramfs-tools/hooks/compcache: 23: inode/vnd.kde.service.ftp: not found
/usr/share/initramfs-tools/hooks/compcache: 24: text/x-dcl: not found
/usr/share/initramfs-tools/hooks/compcache: 25: video/x-matroska: not found
/usr/share/initramfs-tools/hooks/compcache: 26: text/x-uri: not found
/usr/share/initramfs-tools/hooks/compcache: 27: image/x-canon-crw: not found
/usr/share/initramfs-tools/hooks/compcache: 28: image/x-kde-raw: not found
/usr/share/initramfs-tools/hooks/compcache: 29: application/x-glade: not found
/usr/share/initramfs-tools/hooks/compcache: 30: application/x-magicpoint: not found
/usr/share/initramfs-tools/hooks/compcache: 31: application/x-gnome-saved-search: not found
/usr/share/initramfs-tools/hooks/compcache: 32: inode/mount-point: not found
/usr/share/initramfs-tools/hooks/compcache: 33: application/x-gzpostscript: not found
/usr/share/initramfs-tools/hooks/compcache: 34: inode/vnd.kde.service.sftp-ssh: not found
/usr/share/initramfs-tools/hooks/compcache: 35: application/mathematica: not found
/usr/share/initramfs-tools/hooks/compcache: 36: application/x-cdrdao-toc: not found
/usr/share/initramfs-tools/hooks/compcache: 37: application/vnd.oasis.opendocument.database: not found
/usr/share/initramfs-tools/hooks/compcache: 38: video/x-ms-wmv: not found
/usr/share/initramfs-tools/hooks/compcache: 39: inode/vnd.kde.device.unknown: not found
/usr/share/initramfs-tools/hooks/compcache: 40: application/vnd.oasis.opendocument.formula-template: not found
/usr/share/initramfs-tools/hooks/compcache: 41: x-content/unix-software: not found
/usr/share/initramfs-tools/hooks/compcache: 42: application/x-cb7: not found
/usr/share/initramfs-tools/hooks/compcache: 43: text/x-c++hdr: not found
/usr/share/initramfs-tools/hooks/compcache: 44: text/x-changelog: not found
/usr/share/initramfs-tools/hooks/compcache: 45: text/x-copying: not found
/usr/share/initramfs-tools/hooks/compcache: 46: message/partial: not found
/usr/share/initramfs-tools/hooks/compcache: 47: application/docbook+xml: not found
/usr/share/initramfs-tools/hooks/compcache: 48: application/x-vnd.akonadi.calendar.todo: not found
/usr/share/initramfs-tools/hooks/compcache: 49: application/x-msi: not found
/usr/share/initramfs-tools/hooks/compcache: 50: application/x-ruby: not found
/usr/share/initramfs-tools/hooks/compcache: 51: application/x-ruby: not found
/usr/share/initramfs-tools/hooks/compcache: 52: text/x-txt2tags: not found
/usr/share/initramfs-tools/hooks/compcache: 53: application/x-php: not found
/usr/share/initramfs-tools/hooks/compcache: 54: text/x-troff-me: not found
/usr/share/initramfs-tools/hooks/compcache: 55: application/vnd.openxmlformats-officedocument.presentationml.presentation: not found
/usr/share/initramfs-tools/hooks/compcache: 56: text/x-nfo: not found
/usr/share/initramfs-tools/hooks/compcache: 57: text/x-troff-mm: not found
/usr/share/initramfs-tools/hooks/compcache: 58: video/x-ms-wmp: not found
/usr/share/initramfs-tools/hooks/compcache: 59: application/x-quicktime-media-link: not found
/usr/share/initramfs-tools/hooks/compcache: 60: text/x-troff-ms: not found
/usr/share/initramfs-tools/hooks/compcache: 1: application/relaxng: not found
/usr/share/initramfs-tools/hooks/compcache: 2: inode/vnd.kde.device.printer: not found
/usr/share/initramfs-tools/hooks/compcache: 3: application/vnd.oasis.opendocument.image: not found
/usr/share/initramfs-tools/hooks/compcache: 4: interface/x-winamp-skin: not found
/usr/share/initramfs-tools/hooks/compcache: 5: application/x-designer: not found
/usr/share/initramfs-tools/hooks/compcache: 6: inode/vnd.kde.service.afpovertcp: not found
/usr/share/initramfs-tools/hooks/compcache: 7: image/x-portable-bitmap: not found
/usr/share/initramfs-tools/hooks/compcache: 8: application/x-smb-workgroup: not found
/usr/share/initramfs-tools/hooks/compcache: 9: application/rtf: not found
/usr/share/initramfs-tools/hooks/compcache: 10: text/x-rpm-spec: not found
/usr/share/initramfs-tools/hooks/compcache: 11: application/x-theme: not found
/usr/share/initramfs-tools/hooks/compcache: 12: application/x-shared-library-la: not found
/usr/share/initramfs-tools/hooks/compcache: 13: text/x-dsl: not found
/usr/share/initramfs-tools/hooks/compcache: 14: application/x-reject: not found
/usr/share/initramfs-tools/hooks/compcache: 15: text/x-haskell: not found
/usr/share/initramfs-tools/hooks/compcache: 16: application/x-webarchive: not found
/usr/share/initramfs-tools/hooks/compcache: 17: application/x-webarchive: not found
/usr/share/initramfs-tools/hooks/compcache: 18: image/x-sigma-x3f: not found
/usr/share/initramfs-tools/hooks/compcache: 19: application/x-kns: not found
/usr/share/initramfs-tools/hooks/compcache: 20: inode/vnd.kde.service.telnet: not found
/usr/share/initramfs-tools/hooks/compcache: 21: text/html: not found
/usr/share/initramfs-tools/hooks/compcache: 22: text/x-eiffel: not found
/usr/share/initramfs-tools/hooks/compcache: 23: inode/vnd.kde.service.ftp: not found
/usr/share/initramfs-tools/hooks/compcache: 24: text/x-dcl: not found
/usr/share/initramfs-tools/hooks/compcache: 25: video/x-matroska: not found
/usr/share/initramfs-tools/hooks/compcache: 26: text/x-uri: not found
/usr/share/initramfs-tools/hooks/compcache: 27: image/x-canon-crw: not found
/usr/share/initramfs-tools/hooks/compcache: 28: image/x-kde-raw: not found
/usr/share/initramfs-tools/hooks/compcache: 29: application/x-glade: not found
/usr/share/initramfs-tools/hooks/compcache: 30: application/x-magicpoint: not found
/usr/share/initramfs-tools/hooks/compcache: 31: application/x-gnome-saved-search: not found
/usr/share/initramfs-tools/hooks/compcache: 32: inode/mount-point: not found
/usr/share/initramfs-tools/hooks/compcache: 33: application/x-gzpostscript: not found
/usr/share/initramfs-tools/hooks/compcache: 34: inode/vnd.kde.service.sftp-ssh: not found
/usr/share/initramfs-tools/hooks/compcache: 35: application/mathematica: not found
/usr/share/initramfs-tools/hooks/compcache: 36: application/x-cdrdao-toc: not found
/usr/share/initramfs-tools/hooks/compcache: 37: application/vnd.oasis.opendocument.database: not found
/usr/share/initramfs-tools/hooks/compcache: 38: video/x-ms-wmv: not found
/usr/share/initramfs-tools/hooks/compcache: 39: inode/vnd.kde.device.unknown: not found
/usr/share/initramfs-tools/hooks/compcache: 40: application/vnd.oasis.opendocument.formula-template: not found
/usr/share/initramfs-tools/hooks/compcache: 41: x-content/unix-software: not found
/usr/share/initramfs-tools/hooks/compcache: 42: application/x-cb7: not found
/usr/share/initramfs-tools/hooks/compcache: 43: text/x-c++hdr: not found
/usr/share/initramfs-tools/hooks/compcache: 44: text/x-changelog: not found
/usr/share/initramfs-tools/hooks/compcache: 45: text/x-copying: not found
/usr/share/initramfs-tools/hooks/compcache: 46: message/partial: not found
/usr/share/initramfs-tools/hooks/compcache: 47: application/docbook+xml: not found
/usr/share/initramfs-tools/hooks/compcache: 48: application/x-vnd.akonadi.calendar.todo: not found
/usr/share/initramfs-tools/hooks/compcache: 49: application/x-msi: not found
/usr/share/initramfs-tools/hooks/compcache: 50: application/x-ruby: not found
/usr/share/initramfs-tools/hooks/compcache: 51: application/x-ruby: not found
/usr/share/initramfs-tools/hooks/compcache: 52: text/x-txt2tags: not found
/usr/share/initramfs-tools/hooks/compcache: 53: application/x-php: not found
/usr/share/initramfs-tools/hooks/compcache: 54: text/x-troff-me: not found
/usr/share/initramfs-tools/hooks/compcache: 55: application/vnd.openxmlformats-officedocument.presentationml.presentation: not found
/usr/share/initramfs-tools/hooks/compcache: 56: text/x-nfo: not found
/usr/share/initramfs-tools/hooks/compcache: 57: text/x-troff-mm: not found
/usr/share/initramfs-tools/hooks/compcache: 58: video/x-ms-wmp: not found
/usr/share/initramfs-tools/hooks/compcache: 59: application/x-quicktime-media-link: not found
/usr/share/initramfs-tools/hooks/compcache: 60: text/x-troff-ms: not found
E: /usr/share/initramfs-tools/hooks/compcache failed with return 127.
update-initramfs: failed for /boot/initrd.img-2.6.35-30-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.35-30-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.35-30-generic

```

---

