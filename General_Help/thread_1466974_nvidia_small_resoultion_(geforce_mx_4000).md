---
title: "nvidia small resoultion (geforce mx 4000)"
date: 2010-04-30
forum: General Help
---

### Post by 7Sasha on 2010-04-30
Neither the proprietary driver, nor the default one used by ubuntu after fresh install would provide me with the option to change resolution and refresh rate above 800*600.

Ubuntu 9.10

---

### Post by 7Sasha on 2010-04-30
This guy 
[https://answers.launchpad.net/ubuntu/+question/6014](https://answers.launchpad.net/ubuntu/+question/6014)
really helped me out.

He said:
> Thanks for your question, to resolve it we try to install correctly the new nvidia driver:

1) downloads from this site the NVIDIA-Linux-x86-1.0-9755-pkg1.run file (this is for x86 cpu)

[http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html)

2) open a shell and do:

$: sudo apt-get install build-essential
$: sudo apt-get install linux-headers-$(uname -r)
$: sudo apt-get install xserver-xorg-dev

$: sudo gedit /etc/default/linux-restricted-modules-common

add "nv" in the line DISABLED_MODULES=""
this block the nv module, don't worry.

$: chmod +x /dir_where_you_have_save_the_file/NVIDIA-Linux-x86-1.0-9755-pkg1.run

do a backup of your xorg.conf

$: sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

$: sudo /etc/init.d/gdm stop

this stop your desktop.

After do ctrl+alt+f1.

Now you are in console mode, enetr your usrid and password, than do:

$: sudo sh /dir_where_you_have_save_the_file/NVIDIA-Linux-x86-1.0-9755-pkg1.run

You must answer the questions (the last question is about the possibility of nvidia installe to update you xorg.conf, answer ok). After this do:

$: sudo shutdwon -r now

This restart your pc.

Thanks

After restarting, my screen went black alerting me vsync is out of range.
I had to go ctrl+alt+f1 and then edit the /etc/X11/xorg.conf using vim.

sudo vi /etc/X11/xorg.conf

There would be a section with refresh rates range. Just make sure it's in the supported monitor's range. 

Type :wq to save and quit vim.
Reboot.
Hope that helps.

---

