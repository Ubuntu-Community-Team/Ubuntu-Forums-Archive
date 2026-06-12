---
title: "Nvidia Drivers"
date: 2011-06-28
forum: General Help
---

### Post by the wolfe on 2011-06-28
ok. I am using 10.04.2 64 bit and have a Nvidia GT540m GPU. I have downloaded the driver 275.09.07 (linux 64 bit) from Nvidia. It saved as a .run file.  I have given it the "run as a program" permissions. Now, I have tried installing it, but it does nothing. The run in terminal operation fails, it says that it need to be ran as root. 
Can someone please explain how I turn this into a root command so that I can install my drivers?
[IMG]http://i1096.photobucket.com/albums/g322/wolfeking/Screenshot-5.png[/IMG]

---

### Post by nzjethro on 2011-06-28
To run as root, you need to use
```
sudo
``` for Command line, or
```
gksudo
``` for GUI.

How are you executing the .run file? Is it through a terminal? If yes, put "sudo" (no quotes) before your run command. IF it is through a gui, type "gksudo nautilus" (again, no quotes) into a terminal to open nautilus file manager as root, then navigate to and run your file.

You can also install your nvidia drivers if you go to Applications > System > Restricted Drivers. This will prompt you for your password, to log you in as root.

---

### Post by Bachstelze on 2011-06-28
Prepend the command with sudo to run it with root privileges.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Also please don't post large images for just one line of text. Just copy-pasting the error message would have been enough.

---

### Post by the wolfe on 2011-06-28
Its not listing the Nvidia driver in the restricted driver installer. I already tried that. It installed the driver for the Intel HD from the i3-380m processor, but not the Nvidia card. 
 
As for the picture, Its better to show than to tell. And its not that large. 1024*768 resolution. better than 1920*1080.

---

### Post by pqwoerituytrueiwoq on 2011-06-28
to install that drive you will need to close gdm and install via command line and disable the default nvidia driver with "nomodeset" in the boot command 
you will need to reinstall it after every kernel update

to get nomodeset in place look under grub on this page
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/) only difference is you use *nomodeset* instead of *i915.modeset=1*
then do the following after a reboot
1. Remember where the driver is located and its name
2. Open terminal
3. [FONT=Courier New]sudo service gdm stop[/FONT]
4. Press [alt]+[f1]
5. Type user name and press enter
6. Type password and press enter
7. [FONT=Courier New]chmod +x /home/wolfe/Downloads/NVIDIA-Linux-x86_64-275.09.07.run[/FONT]
8. [FONT=Courier New]sudo [/FONT][FONT=Courier New]/home/wolfe[/FONT][FONT=Courier New]/[/FONT][FONT=Courier New]Downloads/[/FONT][FONT=Courier New]NVIDIA-Linux-x86_64-275.09.07.run[/FONT]
9. Go though the installer
10. [FONT=Courier New]sudo service gdm start[/FONT]

I recommend storing *NVIDIA-Linux-x86_64-275.09.07.run* in your /opt folder so you will have it when you need to reinstall after a kernel upgrade
[FONT=Courier New]sudo mv /home/wolfe/downloads/NVIDIA-Linux-x86_64-275.09.07.run /opt/[/FONT]

If press the tab key when typing long names in to a terminal/tty magical things will happen

---

