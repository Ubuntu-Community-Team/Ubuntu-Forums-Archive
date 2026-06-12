---
title: "Unable to install Cisco VPN client"
date: 2010-05-19
forum: General Help
---

### Post by sgsawant on 2010-05-19
My linux is Ubuntu 9.10 64-bit. I downloaded the cisco vpn client but I keep receiving the following error message. Please let me know if you can guess what might be the problem:

```

shashank@shashank-laptop:~$ sudo /home/shashank/Desktop/vpnpatch/vpnclient/vpn_install
Cisco Systems VPN Client Version 4.8.02 (0030) Linux Installer
Copyright (C) 1998-2006 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.31-21-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.31-21-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.31-21-generic/build" will be used to build the module.

Is the above correct [y]

Making module
sh: Can't open ./driver_build.sh
Failed to make module "cisco_ipsec.ko".
shashank@shashank-laptop:~$ 


```

And I think I already have the appropriate kernel headers. :?

---

### Post by -Jeremy- on 2010-05-19
I don't think the kernel headers are the problem here... It is the driver_build.sh that's 
generating the error: the script can't open it. Have you checked the permissions on that 
file?

---

### Post by sgsawant on 2010-05-19
Thanks for your suggestion. But how do you check permission on a file? Till now I used to think, starting a command with "sudo" will activate all necessary permissions.

Any ideas?

Regards,
-sgsawant

---

### Post by sgsawant on 2010-05-19
Well, I edited all the fields in the permissions tab of the file driver_build.sh to read like "read & write". Also the box "execute as a program" is ticked.

Still when I try to install the VPN client I still receive the same error. Please help.

---

### Post by -Jeremy- on 2010-05-19
Hmmm well I don't have any experience with the Cisco vpn client myself so I am afraid I can't help you much further. But I did notice this thread which might prove to be useful for you:

[http://swiss.ubuntuforums.org/showthread.php?p=5689277](http://swiss.ubuntuforums.org/showthread.php?p=5689277)

---

