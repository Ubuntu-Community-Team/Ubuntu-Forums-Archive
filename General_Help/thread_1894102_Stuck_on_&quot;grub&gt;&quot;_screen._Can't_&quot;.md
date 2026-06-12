---
title: "Stuck on &quot;grub&gt;&quot; screen. Can't &quot;update-grub&quot;."
date: 2011-12-11
forum: General Help
---

### Post by lordjj on 2011-12-11
[SIZE=2]Well,  I went ahead an installed a Windows 7 on another partition yesterday,  thought I'd try out some game development programs and whatnot. It  finished installing, I rebooted, and all I get is "Starting Windows"... what the... where's my grub dual boot screen that let's me choose which  OS to boot?
 I boot a Live Linux USB, 
 sudo mount /dev/sda9 /mnt
 sudo grub-install root-directory=/mnt /dev/sda
 
 Reboot
 
 now I get a
 grub>
 screen. 
 
 Boot again from Live USB, 
 sudo update-grub
 /usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
 
 Huh?
 Great, thanks Win 7... now what?
I need to regain access to my Ubuntu install, even if it means wiping the Windows partition. Help appreciated, thanks.

Here's fdisk -l
(sda9 is Ubuntu, sda8 is /home, sda1 is windows, the rest are storage partitions):


```
Disk /dev/sda: 320.1 GB, 320072933376 bytes [/SIZE][SIZE=2]
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x09fb7a2d

[/SIZE][SIZE=2]    Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   286923035   143461486+   7  HPFS/NTFS/exFAT
/dev/sda2       286924798   625137344   169106273+   f  W95 Ext'd (LBA)
/dev/sda5       307837530   506095694    99129082+   7  HPFS/NTFS/exFAT
/dev/sda6       588011193   625137344    18563076    7  HPFS/NTFS/exFAT
/dev/sda7       506095758   515268809     4586526   82  Linux swap / Solaris
/dev/sda8       286924800   293491484     3283342+  83  Linux
/dev/sda9       515270656   588009471    36369408   83  Linux

```I also tried to chroot to my install and run "apt-get install grub-pc", but got a similar error:
```
ubuntu@ubuntu:/mnt$ sudo chroot .
 
ubuntu / # sudo update-grub 
sudo: update-grub: command not found
ubuntu / # sudo apt-get install grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libkadm5clnt-mit7 libgssrpc4 krb5-multidev libgnome-speech7 libkadm5srv-mit7
  libkdb5-4
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  grub-common grub-gfxpayload-lists
Suggested packages:
  multiboot-doc grub-emu xorriso desktop-base
The following NEW packages will be installed:
  grub-common grub-gfxpayload-lists grub-pc
0 upgraded, 3 newly installed, 0 to remove and 134 not upgraded.
Need to get 3091 kB of archives.
After this operation, 8012 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ natty/main grub-gfxpayload-lists i386 0.2 [2956 B]
Get:2 http://packages.linuxmint.com/ katya/upstream grub-common i386 1.99~rc1-13ubuntu3-1mint1 [2117 kB]
Get:3 http://packages.linuxmint.com/ katya/upstream grub-pc i386 1.99~rc1-13ubuntu3-1mint1 [971 kB]
Fetched 3091 kB in 36s (84.0 kB/s)                                             
Preconfiguring packages ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Selecting previously deselected package grub-common.
(Reading database ... 200340 files and directories currently installed.)
Unpacking grub-common (from .../grub-common_1.99~rc1-13ubuntu3-1mint1_i386.deb) ...
Selecting previously deselected package grub-pc.
Unpacking grub-pc (from .../grub-pc_1.99~rc1-13ubuntu3-1mint1_i386.deb) ...
Selecting previously deselected package grub-gfxpayload-lists.
Unpacking grub-gfxpayload-lists (from .../grub-gfxpayload-lists_0.2_i386.deb) ...
Processing triggers for install-info ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up grub-common (1.99~rc1-13ubuntu3-1mint1) ...
Setting up grub-pc (1.99~rc1-13ubuntu3-1mint1) ...

Creating config file /etc/default/grub with new version [/SIZE][SIZE=2]
grub-probe: error: cannot find a device for /boot (is /dev mounted?).
grub-probe: error: cannot find a device for / (is /dev mounted?).
grub-probe: error: cannot find a device for /boot (is /dev mounted?).
grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).

```[/SIZE]

---

### Post by drs305 on 2011-12-11
You can try using the Boot Repair app to fix things, or follow the 'Chroot' guide since it looks like your attempt at chrooting was unsuccessful. Both are linked in my signature line.

If neither works, please run the boot info script ("BIS" in the sig line) and post the contents of the RESULTS.txt. Try the other two methods first. And then you can run the script from within the Boot Repair app if necessary.

---

### Post by lordjj on 2011-12-11
Thanks, the chroot guide helped me chroot successfully and I was able to install-grub and update-grub from there :)
One question though, the boot screen was replaced with a blank purple screen that boots into Ubuntu after 10 seconds. It seems it's the boot screen without the text. Not essential, but do you know how I can fix that?
Thanks anyways :)

---

### Post by drs305 on 2011-12-11
Try holding down the SHIFT key to see if the menu appears. If Grub is not aware of another OS, it won't display the Grub menu. Holding the SHIFT key should force it to appear.

If that is the issue, it means Grub hasn't found your Windows OS (if you have one installed). Normally running update-grub again locates it. I've got to log off, but if you are still not getting the menu to display and you have other OS's on the machine run the boot info script and post the contents of RESULTS.txt. I'll check it tomorrow if nobody else has responded.

---

### Post by lordjj on 2011-12-12
I installed an app called startupmanager from the default repos, checking "show boot splash" seems to have fixed it.
Thanks for the help.

---

### Post by drs305 on 2011-12-12
Glad you fixed the issue (and marked it SOLVED).

One note for future reference - StartupManager was designed around Grub legacy and has limited functionality with Grub 2. A much more robust app for Grub 2 is 'Grub Customizer', which can do everything SUM can do and a lot more. There is a link for it in my signature line if you are interested in learning more about it.

Happy Ubuntu-ing !

---

