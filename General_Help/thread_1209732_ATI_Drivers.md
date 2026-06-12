---
title: "ATI Drivers"
date: 2009-07-10
forum: General Help
---

### Post by magespawn on 2009-07-10
I have by mistake installed ati graphics drivers. Now when I boot all I get is a black screen after the Ubuntu progress bar.

01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)

This is the graphics that is actually in the laptop. 

All I need to know how to do is remove the ati drivers and reinstall the original drivers.

I assume that they are the default drivers that come with Jaunty Jackalope 9.04. since it was working before the ati drivers were installed.

The drivers where install buy using the Applications then Add/Remove. The ati package was selected from the available repositories.

This all has to be done from a command line because of the lack of graphics.

---

### Post by rocket16 on 2009-07-10
While loading Ubuntu, you can select "Ubuntu 9.04 {recovery mode" from the Gurb loader, instead of loading the first choice. Now, open the root shell. Now, type your root password, and uninstall the atu drivers from the terminal. Next, restart the system, and the problem will be cleared.

---

### Post by nnamdi on 2009-07-10
yup ATI drivers still has issues with jaunty jackalope so all u need to do is to uninstall the Xorg drivers, when you reboot your system choose the option from grub boot loader 
1.choose recovery mode
then
root terminal then  type

```

sudo apt-get autoremove xorg-driver-fglrx

```

then reboot

---

### Post by rocket16 on 2009-07-10
Thanks for the information and the code mentioned. I forgot to mention it in detail.

---

### Post by magespawn on 2009-07-11
[SIZE=2]Thanks all for the help, I also got a lot of help from cocooncrash in #ubuntu-za. There are also two entries at [/SIZE][SIZE=2]**paste.ubuntu.com/215002** and **/215073**, for those who would like to know the exact details.

Thank you all.
[/SIZE]

---

