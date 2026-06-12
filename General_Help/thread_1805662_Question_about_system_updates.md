---
title: "Question about system updates"
date: 2011-07-16
forum: General Help
---

### Post by tomdkat on 2011-07-16
So, I was running a system update of my Ubuntu 11.04 (64-bit) system this morning when the system crashed (due to a GIMP issue).  I had to use the power button to recycle the machine.  Anyway, Thunderbird 5 was one of the updates, I believe to be installed and the update didn't complete, due to the crash.

Now, Thunderbird 3.1.11 continues to run fine but when I manually run the update manager, it says my system is current.

Should I be concerned about this or will future updates correct any problems that might be lurking, due to the crash that occurred while my last update was running?

Thanks in advance! :)

Peace...

---

### Post by karlson on 2011-07-16
> **tomdkat said:**
> So, I was running a system update of my Ubuntu 11.04 (64-bit) system this morning when the system crashed (due to a GIMP issue).  I had to use the power button to recycle the machine.  Anyway, Thunderbird 5 was one of the updates, I believe to be installed and the update didn't complete, due to the crash.

Now, Thunderbird 3.1.11 continues to run fine but when I manually run the update manager, it says my system is current.

Should I be concerned about this or will future updates correct any problems that might be lurking, due to the crash that occurred while my last update was running?

Thanks in advance! :)

Peace...

Easiest way to check is open a terminal and run:
```

$ sudo dpkg --configure -a
$ sudo apt-get update ; aptitude safe-upgrade

```

---

### Post by tomdkat on 2011-07-16
Thanks for those commands. I ran them and there was no indication of any problems or pending updates.  So, maybe the Thunderbird update wasn't to Thunderbird 5 but some other update.

Thanks!

Peace...

---

### Post by DawieS on 2011-07-16
You should also check whether you are booting from the latest kernel, which was included in the last update.

The Grub boot-loader is the last in the update process, and it is possible that it may not have run to completion, in which case all updates were done, but you are still booting from the old kernel. If so, type **sudo update-grub** in a terminal.

To check the version number (that should be displayed in the Grub menu), open Synaptic Package Manager, then click on File > History.

---

### Post by tomdkat on 2011-08-11
Thanks for the info.  I'm running the '2.6.38-10-generic' kernel:

> 
tom@deathstar:~$ uname -a
Linux deathstar 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
tom@deathstar:~$ 


According to the "sudo update-grub" command I ran, that appears to be the latest kernel I have installed:
> 
tom@deathstar:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.38-10-generic
Found kernel: /boot/vmlinuz-2.6.38-8-generic
Found kernel: /boot/vmlinuz-2.6.31-21-generic
Found kernel: /boot/vmlinuz-2.6.31-19-generic
Found kernel: /boot/vmlinuz-2.6.28-16-generic
Found kernel: /boot/memtest86+.bin
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 55108 package 'virtualbox-3.0':
 error in Version string '3.0.12-54655_Ubuntu_jaunty': invalid character in revision number
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 55109 package 'virtualbox-3.0':
 error in Config-Version string '3.0.12-54655_Ubuntu_jaunty': invalid character in revision number
Updating /boot/grub/menu.lst ... done

tom@deathstar:~$

On a side note, how can I deal with those dpkg-query warning?

Is Thunderbird 3.1.11 the latest version of Thunderbird available for Ubuntu 11.04 64-bit?

Thanks!

Peace...

---

