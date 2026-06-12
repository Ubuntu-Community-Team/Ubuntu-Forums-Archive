---
title: "OEM install problems"
date: 2012-02-23
forum: General Help
---

### Post by fdclemmons on 2012-02-23
Trying to install on brand new hard drive using OEM option and get the following errors.

[7.935662] Kernel panic - not  syncing:VFS: Unable to mount root fs on unknown-block(8,1)
[7.9357381] Pid:1, comm: swapper not tainted 3.0.0-12-generic #20-Ubuntu
[7.935801] Call Trace:
[7.935868] [<1518c98>] ? printk +0x2d/0x2f
[7.935930] [c1518b76] panic +0x5c/0x15
[7.935994] [< c17bcb2b >] mount_block_root + 0xb9/0x14c
[7.936098] [< c1135f7c >] ? sys_mknod +0x2c/0x30
[7.936159] [< c17bcd36 >] mount_root +0x59/0x5f
[7.936220] [< c17bce8a >] prepare_namespace _0x14e/0x192
[7.936286] [< c1127235 >] ? sys_access +0x25/0x30
[7.936347] [< c17bc89f>] kernel_init +0x136/0x13b
[7.936407] [< c17bc769 >] ? start_kernel +0x358/0x358
[7.936470] [< c1533b7e >] kernel_thread_helper +0x6/0x10

Am using Ubuntu 11.10-desktop-i386 CD burned from downloaded iso file.

SYSTEM SPECIFICATIONS:
MOTHERBOARD: VIA Technologies KM400-8235
RAM: 2 Gigabytes DDR 400
PROCESSOR: AMD Athlon XP 2000+,MMX, 3DNOW, ~1.7 Ghz
BIOS: Phoenix-AwardBIOS v6.00PG

I tried Linux Redhat Decades ago and it took several CD's to install it but there were no errors. I want to TOTALLY DUMP MICROSOFT and run Ubuntu. I appreciate all who can help me solve this problem and get the computer working. I really do not want to re-install XP or purchase Windows 7. Thanks in advance

---

### Post by dcstar on 2012-02-24
> **fdclemmons said:**
> Trying to install on brand new hard drive **using OEM option** and get the following errors.
........

Why?

Have you just tried a normal install?

---

### Post by fdclemmons on 2012-02-24
Yes

---

### Post by forrestcupp on 2012-02-24
When you tried the normal install, did the Live CD boot to an Ubuntu desktop? That's the best way to do it because that will show you whether it's even going to work on your hardware or not. Just boot to the Live CD and choose the option to Try Ubuntu, and if it works, you can install it graphically from there. If you can't even boot to a Live CD, then you may have a hard time installing Ubuntu. On older hardware, you might be better off trying out Xubuntu or Lubuntu.

Also, what video chipset are you using?

---

### Post by mcduck on 2012-02-24
> **dcstar said:**
> Why?

Have you just tried a normal install?

+1 to this.

The only reason to do an OEM install of Ubuntu is if you actually are planning to sell or give the computer away to somebody else. It's nothing like using OEM disc for windows (as there is no price anyway since Ubuntu is free.), and using the OEM install option for normal use just makes things more complicated for no reason.

Anyway, check your computer's BIOS settings and if there's anything about hard drive (or SATA controller) mode, make sure it's not set to RAID. Based on the error message, Ubuntu is currently trying to access the *eighth* hard drive (which is unlikely to be correct...)

edit: ...and if you end using the OEM install anyway, keep in mind that the user created during the install process is not intended as a permanent user account. You'll need to finish the OEM install properly when you are ready setting up the system, and after that on the next boot the new user will be prompted to select language, timezone etc, and to create the actual user account.

---

### Post by fdclemmons on 2012-02-24
Video Chipset: NVIDIA GFORCE 6200 512 MB RAM

Yes I can run Ubuntu from Live CD and it booted to the Ubuntu desktop. I tried to install
Ubuntu as dualboot with windows and got this message
"WindowsBackend object has no attribute iso_path" A portion of the error log is this:

02-24 08:50 DEBUG  CommonBackend: metalink md5sums:
a65c220b437d6907ba9463b7f479fea5  ubuntu-11.10-alternate-amd64.metalink
bdbf5bf7dfa85cad2cd711f081b071ec  ubuntu-11.10-alternate-i386.metalink
4a4ddfa7d6eea4d9cf7a9f8d854e0418  ubuntu-11.10-desktop-amd64.metalink
a84050d7b00ff42b83a69ad7309b6f36  ubuntu-11.10-desktop-i386.metalink
c2f7e1f7352a8d3cd1c2dede0c709a1a  ubuntu-11.10-server-amd64.metalink
2b296035b3ba3f8536dc0efa49a52fc2  ubuntu-11.10-server-i386.metalink

02-24 08:50 DEBUG  TaskList: #### Finished get_metalink
02-24 08:50 DEBUG  TaskList: New task get_file_md5
02-24 08:50 DEBUG  TaskList: #### Running get_file_md5...
02-24 08:50 DEBUG  TaskList: #### Finished get_file_md5
02-24 08:50 ERROR  CommonBackend: Invalid md5 for ISO C:\ubuntu\install\installation.iso (c396dd0f97bd122691bdb92d7e68fde5 != eafaaa530741742c10e27604a17d132a)
None
02-24 08:50 DEBUG  TaskList: ### Finished check_iso
02-24 08:50 ERROR  TaskList: 'WindowsBackend' object has no attribute 'iso_path'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 579, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 565, in use_iso
AttributeError: 'WindowsBackend' object has no attribute 'iso_path'
02-24 08:50 DEBUG  TaskList: # Cancelling tasklist
02-24 08:50 ERROR  root: 'WindowsBackend' object has no attribute 'iso_path'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 205, in run_cd_menu
  File "\lib\wubi\application.py", line 120, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 579, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 565, in use_iso
AttributeError: 'WindowsBackend' object has no attribute 'iso_path'
02-24 08:50 DEBUG  TaskList: # Finished tasklist

From what I can understand from reading this is the iso I burned is not valid. Any suggestions on the best MD5 checker? 
Also I will try the other things you all suggested in your replies to this post.

The reason I am trying to install as OEM is I have a small business and I build my own systems. We are growing and we will be hiring more people. It is more cost effective for me to use Linux than to constantly pout money into the coffers of Microsoft. And, I am not too happy with their technical support. Many times I have had to Google to find the CORRECT solution to a problem with their software. Just tired of that.

---

### Post by forrestcupp on 2012-02-24
Are you trying to install Ubuntu by using Wubi? If so, that's not a true dual boot. The only reason I'm asking is because of all those lines about Wubi. 

Did you actually boot to the CD, or did you let the autostart pop up from within Windows? I assume you actually booted to the Live CD, since you said you got to the Unity desktop.

Also, did you get those errors while you were trying to install, or after you installed?

> **fdclemmons said:**
> And, I am not too happy with their technical support. Many times I have had to Google to find the CORRECT solution to a problem with their software. Just tired of that.
Lol. Well, you should expect to have to Google about a hundred times more often with Linux. ;)

---

### Post by fdclemmons on 2012-02-24
Actually booted to the Live CD and got the errors while trying to install.

---

### Post by mcduck on 2012-02-24
> **fdclemmons said:**
> 
The reason I am trying to install as OEM is I have a small business and I build my own systems. We are growing and we will be hiring more people. It is more cost effective for me to use Linux than to constantly pout money into the coffers of Microsoft. And, I am not too happy with their technical support. Many times I have had to Google to find the CORRECT solution to a problem with their software. Just tired of that.
You shouldn't need OEM install for that.

The only reason to use OEM install on Ubuntu is that you are selling/giving the computer away, and therefore can't create the actual user account during install.

If the machines are going to be used in your company, then creating the user account during install wouldn't be a problem and therefore the extra steps OEM install adds would be pointless.

Like I said, the normal version of Ubuntu is free to use, and exactly same for all home and professional use, so it's not like in Windows world where an OEM install is often preferred because of it's lower cost compared to normal license.

Anyway, 'm quite sure you can't actually make an OEM install using Wubi, and since your problems seem to be Wubi-related I'd recommend just trying a normal install instead. Espcially since you said you can actually run the install CD just fine. (Besides, I really wouldn't recommend a Wubi install for any long-term use, a normal install is more stable and less likely to cause problems in the long run).

---

### Post by forrestcupp on 2012-02-24
> **fdclemmons said:**
> Actually booted to the Live CD and got the errors while trying to install.

Are you trying to install it from the command line somehow? If you can boot to the Live CD, you should just double click on the Install Ubuntu icon and do it graphically. I agree that if you're not selling these computers, but just using them for your business, you should just do a normal graphical installation, and not an OEM one. Like mcduck said, the only reason to use OEM is if you need to install it without setting up a user because you'll be selling the computer and the customer wants to be able to set up their own user account. That's not what you're doing, so you should use the normal graphical installation.

If you've tried all of that, then maybe go back to ubuntu.com and try to download the standard Ubuntu iso and burn it again, possibly at a slower burn speed. Also, if you're downloading the AMD64 iso, make sure you're installing it on a 64-bit computer. If not, you need the x86 version.

---

### Post by fdclemmons on 2012-02-24
Have downloaded the ubuntu-11.10-desktop-i386 again and burned it at 1x speed using ImgBurn software. Checked MD5 Sum and it was correct for downloaded iso. Same problems. Will keep trying.

---

### Post by mcduck on 2012-02-24
> **fdclemmons said:**
> Have downloaded the ubuntu-11.10-desktop-i386 again and burned it at 1x speed using ImgBurn software. Checked MD5 Sum and it was correct for downloaded iso. Same problems. Will keep trying.

OK, did you check if there is some hard drive controller setting in BIOS like I suggested? That's one reason I've definitely seen causing this kind of errors on machines where the drives can be set to either normal or RAID mode.

---

### Post by dcstar on 2012-02-24
> **fdclemmons said:**
> Actually booted to the Live CD and got the errors while trying to install.

Boot the  Live CD and use **gparted** to write a new partition table to the disk, then install.

---

