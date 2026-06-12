---
title: "Ubuntu 10.10 don't boot after 2.6.35-23-generic kernel headers update"
date: 2010-11-30
forum: General Help
---

### Post by rsansores on 2010-11-30
This week my ubuntu 10.10 was updated via update center. I obtained the new kernel headers 2.6.35-23-generic but now I can't boot using this kernel version and I have to select manually 2.6.35-22-generic in grub. I can see the ubuntu plymouth splash screen but it never rise gnome. Could someone tell me where are the boot logs and how to activate them, In /var/log/ I have "boot" file but is empty and in "boot.log" I cant see any usefull information (I have BOOTLOGD_ENABLE=yes in /etc/defaul/bootlogd).

Thanks

---

### Post by germanix on 2010-11-30
t would seem that for whatever reason, this new kernel does not work for you. i do not know how to get it to work but  i do know how to get rid of it so you can use the kernel you used before.
Go to the Ubuntu-Tweak download page.
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
Add the repository as per the instructions, or download the file manually and double-click the .deb file to install.
Ubuntu-Tweak will be available under Applications > System Tools.
To clean the kernels:
Select "Package Cleaner" on the left and ""Clean Kernel" from the right panel.
Press the "Unlock" button at the lower right, enter your password.
Select from the displayed list the kernel images and headers you wish to remove. The kernel in use is not listed.
Press the "Cleanup" button at the lower right to remove the selected kernel images and headers.

---

### Post by rsansores on 2010-11-30
Tnx Germanix, this avoids the annoy of selecting every time an old kernel. I would like to post this as an issue in the bug tracking system but I don't have the boot logs to provide a clear landscape of the problem. Could someone provide a walktrough to get the boot logs or any log that could be useful.

TNX

---

### Post by rsansores on 2010-12-21
Well, I'm reviving this thread because this week I obtained the new 2.6.35-24 Kernel Update and I'm having the same behavior. Maybe I will need to wait until 2.6.36.

---

### Post by rsansores on 2010-12-21
Ok, finally I found the problem. I stopped the plymouth and logged in text mode. I tried to start Xs manually and got an error:

Can't find Nvidia module (or something like that)

To be honest I dont remember building the Nvidia kernel module myself and I'm almost sure I used the ubuntu repository privative drivers. I'm almost 99% sure... so basically after updating kernel headers the NVIDIA kernel module should build and work fine automatically (but it doesn't).

The solution was download the official drivers from NVIDIA and install them. After that my system boots perfectly and is working again. :) :D :o

---

