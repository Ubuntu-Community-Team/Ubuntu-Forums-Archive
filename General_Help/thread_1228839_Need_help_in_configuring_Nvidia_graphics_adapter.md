---
title: "Need help in configuring Nvidia graphics adapter"
date: 2009-08-01
forum: General Help
---

### Post by Avinash.Rao on 2009-08-01
Hi, 

I have recently installed Ubuntu Desktop 9.04 on a 64-bit Ubuntu 9.04 Server kernel. Its a HP XW4600 workstation with a Nvidia Graphics adapter.

After the installation, the os prompts me to select an NVidia Display driver, it gives two options, 

1) NVidia Accelerated Graphics Driver (Version 180) [Recommended]
2) NVidia Accelerated Graphics Driver (Version 173)

and it says driver not activated. I am not able to select any of them. if i click on activate, it downloads the driver but nothing happens after that. After reboot, I get the following message, 

**Ubuntu is running in Low-Graphics mode**
The Following error was encountered.You may need to update your configuration to solve this.
(EE) Nvidia(0): Failed to load the kernel module
(EE) Nvidia(0):***Aborting***
(EE) Screen(s) found; but none have usable configuration.

I have an option to click OK, when i did, i get options, to run ubuntu in low-graphics mode, reconfigure,troubleshoot and exit to console login.

I am able to get the login screen after selecting ubuntu to run in low-graphics mode.

lspci | grep -i nvidia
01:00.0 VGA compatible controller: nVidia Corporation Quadro FX 370 (rev a1)

can anybody help me
Avinash

---

### Post by Avinash.Rao on 2009-08-02
:confused:

---

### Post by ratcheer on 2009-08-02
Use this procedure at your own risk.

1) Hit Ctrl-Alt-F1 to get to a system console
2) cd to the location where your Nvidia driver .run file resides
3) sudo /etc/init.d/gdm stop 
4) Step 3 should respond with OK
5) sudo sh ./Nxxxxxxxxxxx.run (the driver file)
6) When it asks if you want to autoconfigure xorg, respond Yes
7) sudo reboot

The machine should come up with your driver installed and ready to use.

More detail: [http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

Tim

---

### Post by Avinash.Rao on 2009-08-02
Thanks for the reply. I downloaded August 1 2009: Latest nVidia 185.xx (STABLE) drivers: 185.18.31 driver from the link you gave me and heres what happened when i executed the .run file.

-> No precompiled kernel interface was found to match your kernel; would you like the installer to attempt to download a kernel interface for your kernel from the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;this means that the installer will need to compile a kernel interface for your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your kernel and that they are properly configured; on Red Hat Linux systems,for example, be sure you have the 'kernel-source' or 'kernel-devel' RPM installed.  If you know the correct kernel source files are installed, you may specify the kernel source path with the '--kernel-source-path' command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions on fixing installation problems in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

---

### Post by ridetheteapot on 2009-08-02
sudo apt-get install linux-headers-generic
generic/server whatever kernel you are using get that package 'uname -r'

---

### Post by Avinash.Rao on 2009-08-02
Thank you for the information.

I installed the linux-headers-server and i could install the Nvidia driver.
But, after i still got that error after the installation, i logged in selecting low-graphics mode and activated the recommended driver and it worked.



> **ridetheteapot said:**
> sudo apt-get install linux-headers-generic
generic/server whatever kernel you are using get that package 'uname -r'

---

### Post by ratcheer on 2009-08-02
> **Avinash.Rao said:**
> 

-> No precompiled kernel interface was found to match your kernel; would you like the installer to attempt to download a kernel interface for your kernel from the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;this means that the installer will need to compile a kernel interface for your kernel.


Odd. I always get those warnings, too, but I just forge ahead through the installation and, after I reboot, the new driver is working.

Tim

---

### Post by ridetheteapot on 2009-08-02
well its cool its working, wonder what was going wrong?
there ubuntu repo versions are more useful to some folks anyway, cause theyll get setup for kernel updates automagicly.
however you dont get to play withthe newest drivers and nvidia has been releasing updates like they think linux is cool or something ;-P

---

### Post by Avinash.Rao on 2009-08-02
I was able to install the drivers.

But, i see a delay when working with multiple windows say 2 windows. 
For example, When i minimize one of the windows, there is a slight delay not as quick as i would want it to be. Is anybody facing this?

---

