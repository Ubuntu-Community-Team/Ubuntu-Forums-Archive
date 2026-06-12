---
title: "Help setting up sound card with lastest Ubuntu - Warning first time user!!"
date: 2009-12-27
forum: General Help
---

### Post by mattyj1085 on 2009-12-27
Can any one walk me through installing my drivers for my sound card?

Its the first time i've really tried installing Ubuntu as my main OS and I am trying to get it working with XBMC so I can use it as my media centre pc.

Its a trust 514DX 5.1 sound expert optical sound card which uses a C-Media 8738 chipset

Ubuntu auto picked it up and all seemed to be well untill I tried playing anything with any sound! I have it connected via Optical cable to a receiver but no signal is getting sent from the pc. I have tried all of output settings in sound preferences its like its not even trying to output using optical. I know on XP I had to change the output to digital and choose the optical connection from within the software it installed off the disk.

The disk does have Linux drivers on it but I have no idea on how to install them and the readme isn't making much sense to me either as I get stuck at the first step locating the folder /usr/src/linux/driver/sound

I can only find 
/usr/src/fglrx-8.660
/usr/src/linux-headers-2.6.31-14
/usr/src/linux-headers-2.6.31-14-generic
/usr/src/linux-headers-2.6.31-16
/usr/src/linux-headers-2.6.31-16-generic

Here is the readme included with the linux drivers from my soundcard disk at the end, If someone could walk me through each instruction and try and relate it to the latest Ubuntu Build 9.10 that I am using it would be much appreciated.

Or if you have any other ideas on how I can get my sound working without having to go back to windows!!

Thanks


STEPS TO BUILD DRIVER
================================================================================

  1. Backup the Config.in and Makefile in the sound driver directory
     (/usr/src/linux/driver/sound).
     The Configure.help provide help when you config driver in step
     4, please backup the original one (/usr/src/linux/Document) and
     copy this file.
     The cmpci is document for the driver in detail, please copy it
     to /usr/src/linux/Document/sound so you can refer it. Backup if
     there is already one.

  2. Extract the tar file by 'tar xvzf cmpci-xx.tar.gz' in the above
     directory.

  3. Change directory to /usr/src/linux

  4. Config cm8338 driver by 'make menuconfig', 'make config' or
     'make xconfig' command.

  5. Please select Sound Card (CONFIG_SOUND=m) support and CMPCI
     driver (CONFIG_SOUND_CMPCI=m) as modules. Resident mode not tested.
     For driver option, please refer 'DRIVER PARAMETER'

  6. Compile the kernel if necessary.

  7. Compile the modules by 'make modules'.

  8. Install the modules by 'make modules_install'


INSTALL DRIVER
================================================================================

  1. Before first time to run the driver, create module dependency by
     'depmod -a'

  2. To install the driver manually, enter 'modprobe cmpci'.

  3. Driver installation for various distributions:

    a. Slackware 4.0
       Add the 'modprobe cmpci' command in your /etc/rc.d/rc.modules
       file.so you can start the driver automatically each time booting.

    b. Caldera OpenLinux 2.2
       Use LISA to load the cmpci module.

    c. RedHat 6.0 and S.u.S.E. 6.1
       Add following command in /etc/conf.modules:

       alias sound cmpci

    also visit [http://www.cmedia.com.tw](http://www.cmedia.com.tw) for installation instruction.

---

### Post by mattyj1085 on 2009-12-27
It seems I have fixed it!!!!!

I found another post and tried what they suggested and it worked!

ran this sudo apt-get install gnome-alsamixer

then there was a IEC958 Output that wasn't ticked so I ticked this and now all seems to be working!!!

Thanks anyway!

---

### Post by maizuddin35 on 2009-12-27
yes it is working. thanks for the post. 
it really make me ubuntu feels good...haha
:P

---

### Post by drdanielfc on 2009-12-27
Not sure if this is an old problem or not (i no longer have a separate audio card) but i had some trouble with on-board audio and an external card as ubuntu would only recognize one, and the selection was random. I suggest restarting several times and seeing if the sound still works. If it does, well the problems been fixed :P. Otherwise, try disabling the on board audio through your bios menu

---

