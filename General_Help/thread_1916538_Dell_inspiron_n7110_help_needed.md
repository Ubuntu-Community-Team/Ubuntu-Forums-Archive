---
title: "Dell inspiron n7110 help needed"
date: 2012-01-28
forum: General Help
---

### Post by ruza on 2012-01-28
Hello world!

I recently bought this laptop and everything kinda falls apart. 

Firstly let's say i'm not really a noob. I use linux as my primary and only os for quite a while. I feel very disappointed because i have to write this from my sisters (winblows) computer. 

Let's get down to problem. 

Laptop config.
i5/8gb ddr3/500gb hdd/ nvidia 525/multitouch capable touchpad/

when i install xubuntu the first thing i notice is that multitouch is not working AT ALL. System recognizes it as regular mouse and does not even try to load synaptics driver. But that is minor problem compared to next one. 

After installation of nvidia proprietary driver i notice that nothing happened. So i opened nvidia settings and it suggested me to run nvidia-xconf command as root. That command generated xorg.conf which led to complete disaster. Xubuntu started hanging on boot. I could login without x (ctrl-alt-f1). then i had to reverse changes made to xorg.conf 


So I need help to make it work. I want my multitouch and i want my graphics card to work. Tried linux mint(both ubuntu and debian), and pure ubuntu. They all had symptoms like that. And i tried manually downloading and installing driver with same result - failing very hard.

---

### Post by zadehas on 2012-01-28
I think that your laptop features nvidia hybrid graphics (although I'm not sure - you need to consult the specs). 
This means that video acceleration will not work out of the box with ubuntu, or the nvidia drivers, since they don't yet support hybrid graphics on linux.
You need to install some open alternatives, like bumblebee: [https://wiki.ubuntu.com/Bumblebee]("https://wiki.ubuntu.com/Bumblebee")
Works for me.

If your BIOS allows it, you can disable the integrated chip and then use the nvidia drivers as they are.

I have no idea how to fix the touchpad problem though.

---

### Post by ruza on 2012-01-28
well forgot to tell you, bumblebee solution was not working also. Bios does not have any option useful for that, so i thing there must be a "secret" key combination to unlock hidden features in BIOS. It would be great if someone tell me that. 

Thanks anyway. :) will try harder to fix this using bumblebee, guess i did something wrong.

---

### Post by mikrus on 2012-12-30
Ubuntu 12.10
Dell Inspiron N7110
GeForce 525M
BIOS A13
Fan noise problem resolved
Optimus card problem resolved

Install fresh Ubuntu. When booting from a USB press F6 and set acpi = off

During the installation, turn off internet access
After installing the system, turn on the internet and type:

sudo add-apt-repository ppa:bumblebee/stable
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get --purge remove xserver-xorg-video-nouveau
sudo reboot
sudo apt-get install bumblebee bumblebee-nvidia linux-headers-generic
sudo reboot

Allow installations and updates all other system components.
sudo apt-get upgrade

Only this method worked out after three days of hard work and more than a dozen attempts.

It is worth to mention another problem. Ubuntu on the Dell Inspiron N7110 will not start if there is any USB device connected during boot. To avoid this problem:

sudo pico /etc/default/grub

find:

GRUB_CMDLINE_LINUX_DEFAULT = "quiet splash"

and replace:

GRUB_CMDLINE_LINUX_DEFAULT = "quiet splash pci=noacpi"

sudo update-grub

This way you can rebooting Ubuntu with USB devices connected BUT this method is forbidden when you want to use Bumblebee
Read -> [https://github.com/Bumblebee-Project/Bumblebee/wiki/Troubleshooting](https://github.com/Bumblebee-Project/Bumblebee/wiki/Troubleshooting)
"Be sure that your kernel boot parameters do not contain on of the options noacpi, pci=noacpi, acpi=off"

---

