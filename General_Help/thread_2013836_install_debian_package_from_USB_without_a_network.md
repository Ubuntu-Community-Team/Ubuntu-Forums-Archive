---
title: "install debian package from USB without a network"
date: 2012-07-01
forum: General Help
---

### Post by brian_mk on 2012-07-01
Here's the problem...

We have some machines controlled from an 'embedded' PC motherboard running Ubuntu 10.04 server.
The machines normally operate without a system console or keyboard and have a private network connection.
The problem is that if a motherboard needs to be replaced in the field, a new Ethernet driver package needs to be installed.
We would like to find a way to install the debian package without the network in fool proof way.

Without Ethernet, the only real option seems to be USB flash.
Because the system is running ubuntu server, USB devices are not auto mounted (usbmount is not installed).
To complicate things further, some machines have a USB flash license dongle.
That means to do the install manually the field service guy would need do something like:-
* Connect a system console and USB keyboard.
* Unplug any USB dongle(s).
* Plug in the USB stick with the driver.
* 'sudo mkdir -p /media/usb'
* 'sudo mount /dev/sdb1 /media/usb0'
* 'sudo dpkg -i /media/usb0/<package name>'
* 'sudo umount /media/usb0'
* Unplug the USB stick
* Reconnect USB dongle(s).

The field service manager doesn't like this because
1) It means giving root permissions to the service engineer.
2) The service engineer could make mistakes when entering the commands.

The only alternatives I can come up with are:-

1) Replace the system disk at the same time as the motherboard.
The new disk will have the required driver already installed.
This would mean having to restore the machine config and calibration files from a backup.
It also means the service engineer will need to carry a stock of replacement disks + software.

2) Create a bootable USB flash drive containing a script that would automatically run when the system is booted.
The field service manager likes this idea because it could be made fully automatic.
It does mean that the PC BIOS config may need changing to enable booting from USB.
I suspect this effectively requires creating a custom flash bootable Ubuntu live.
How easy is this?
Using 'Remastersys' may be a bit of an overkill.
Another possibility may be to use 'uck'.
Both these options look like a fair amount of work.

Is there a simpler solution?
It is possible to do something from grub?

---

### Post by brian_mk on 2012-07-04
No replies. Ho Hum.

In case someone else has a similar problem, here is my solution using 'uck' (still in progress).

My starting point was the 10.04 64bit live desktop iso.
First I found ubuntu 10.04's 'uck' package to be very buggy. I had all sorts of problems. It was made worse because I was accessing the machine remotely using NX & ssh.

Eventually I gave up and installed the latest uck from sourceforge and used the system console. I was a bit surprised that it installed on 64bit 10.04 without the need to build anything. I'm guessing it must be all script based.

It worked ok apart from attempting to run isohybrid at the end despite me selecting the option to disable it (isohybrid is not available on 10.04).
If you ignore the error message it still creates a usable iso file.

I ditched all the ubuntu language options apart from english to save space.
I used the uck package manager to install 'dialog' and remove the 'ubiquity' package (I don't want the 'install ubuntu' option).
I created a Desktop folder for the default 'ubuntu' user under /etc/skel. Added a launcher to run a bash script that uses dialog menus to install or remove a chosen debian package on a selected partition on the hard drive.

As a C/C++ programmer I struggled a bit with bash srings/arrays - what a bizarre arcane syntax!

It does the job although, as I expected, it's been a lot of work to do something that should be a lot simpler.

I did wonder if I could have used the synaptic package manager with a debian repository on the flash drive? I suspect this would require the user to have root permissions. I'm not even sure if synaptic has provision to install packages  on a different partition to the one currently in use?

---

