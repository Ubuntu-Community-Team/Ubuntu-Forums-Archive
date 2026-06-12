---
title: "upgraded to 10.10...stuck on tty1"
date: 2010-10-11
forum: General Help
---

### Post by samarchepas on 2010-10-11
so I upgraded to 10.10 and it just goes to tty1 so I used startx to boot and I'm getting a fatal server error: no screen found (which is kinda ironic because its saying that on the SCREEN :lol:)
so I'm kinda lost at this point...please help.

---

### Post by 3Miro on 2010-10-11
Try
```
sudo dpkg-reconfigure xserver-xorg
```

The message refers to a xorg screen capable of showing graphics, the console screen doesn't count.

---

### Post by samarchepas on 2010-10-11
thanks for the reply, I tried that command and it didn't do anything.

---

### Post by 3Miro on 2010-10-11
OK, so the problem is more serious and we need more info. Can you post the log file /var/log/Xorg.0.log? If you don't know how to do it from CLI, here is one way:

Do you have an Ubuntu liveCD (any version will be good)?

1. Boot you computer.
2. Insert he live CD.
3. Run startx.
4. Reboot with
```
sudo shutdown -r now
```
5. Enter the liveCD environment.
6. Open "Places" and click on the drive that contains your system, then you can navigate to /var/log/Xorg.0.log and post it here.

---

### Post by samarchepas on 2010-10-11
Sadly the only LiveCD I have is version 9.04 (32 bit) so I can't access "places" (or I just don't see where it is lol)

---

### Post by 3Miro on 2010-10-11
> **samarchepas said:**
> Sadly the only LiveCD I have is version 9.04 (32 bit) so I can't access "places" (or I just don't see where it is lol)

On the top panel right next to applications. You are using Ubuntu not Xubuntu or Kubuntu, right?

You can also do that by going to Applications -> Accessories -> Terminal and then typing:
```
 gksudo nautilus 
```

When nautilus comes up, on the left hand side, there will be a list of partitions/drives. Select the one with Ubuntu and then go to var -> log and get Xorg.0.log file to post it here.

---

### Post by samarchepas on 2010-10-11
when I boot the liveCD the only options I have:
Install Ubuntu
check disc for defects
test memory
boot from first hard disk
rescue a broken system

and yes its Ubuntu

---

### Post by 3Miro on 2010-10-11
> **samarchepas said:**
> when I boot the liveCD the only options I have:
Install Ubuntu
check disc for defects
test memory
boot from first hard disk
rescue a broken system

and yes its Ubuntu

Is there no "Try Ubuntu w/o changes to your system"? This could be an alternative install or something like that. You should get a liveCD that can boot Ubuntu, it is always nice to have one around it is very useful in many situations.


OK, here is the "hard way":

Start your computer and try to startx again. Then put a flash drive into your USB. Then type:
```
 sudo fdisk -l 
```
This will list all disks and partitions on your system. The flash drive will be "/dev/sd*" where * will be sdb1 or sdc1 or something along those lines (also most flash drives are Win95 FAT or NTFS). From now on, I am assuming that it is adb1. Then try the following:

```
 sudo mkdir /media/usb-drive
 sudo mount /dev/sdb1 /media/usb-drive 
```

Now your drive should be connected to the /media/usb-drive folder.
```
 ls /media/usb-drive 
```
should display all the files that you have on the USB drive.

Then you can put the file there:
```
 cp /var/log/Xorg.0.log /media/usb-drive 
```
if it doesn't work, you can try with sudo as well.

Safely remove the drive:
```
 sudo umount /media/usb-drive 
```

You can then take the file to another computer.

---

### Post by feroxy on 2010-10-11
What graphics card do you have samarchepas? I have the same problem and it seems to be due to this bug [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/626974](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/626974)

---

### Post by khaze on 2010-10-15
I have the same problem I think.

I'm using however an ATI card.

Here's the Xorg.0.log

```
[   699.722] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[   699.729] X Protocol Version 11, Revision 0
[   699.731] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[   699.733] Current Operating System: Linux Nelson-Linux 2.6.35-22-generic-pae #34-Ubuntu SMP Sun Oct 10 11:03:48 UTC 2010 i686
[   699.734] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=efa34c07-5d6a-4bfc-9aba-eeb32e1e4337 ro quiet splash
[   699.736] Build Date: 16 September 2010  05:39:22PM
[   699.737] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[   699.738] Current version of pixman: 0.18.4
[   699.740]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   699.743] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   699.747] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Oct 15 22:21:55 2010
[   699.749] (==) Using config file: "/etc/X11/xorg.conf"
[   699.750] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   699.752] (==) No Layout section.  Using the first Screen section.
[   699.752] (**) |-->Screen "Default Screen" (0)
[   699.752] (**) |   |-->Monitor "<default monitor>"
[   699.752] (==) No device specified for screen "Default Screen".
    Using the first device section listed.
[   699.752] (**) |   |-->Device "Default Device"
[   699.752] (==) No monitor specified for screen "Default Screen".
    Using a default monitor configuration.
[   699.752] (==) Automatically adding devices
[   699.752] (==) Automatically enabling devices
[   699.752] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   699.752]     Entry deleted from font path.
[   699.752] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[   699.752] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   699.752] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   699.752] (II) Loader magic: 0x81f8e00
[   699.752] (II) Module ABI versions:
[   699.752]     X.Org ANSI C Emulation: 0.4
[   699.752]     X.Org Video Driver: 8.0
[   699.753]     X.Org XInput driver : 11.0
[   699.753]     X.Org Server Extension : 4.0
[   699.753] (--) PCI:*(0:0:2:0) 8086:0046:1025:035d rev 24, Mem @ 0xd8000000/4194304, 0xc0000000/268435456, I/O @ 0x00004050/8
[   699.753] (--) PCI: (0:1:0:0) 1002:68c1:1025:035d rev 0, Mem @ 0xd0000000/134217728, 0xdc400000/131072, I/O @ 0x00003000/256, BIOS @ 0x????????/131072
[   699.753] (II) Open ACPI successful (/var/run/acpid.socket)
[   699.753] (II) "extmod" will be loaded by default.
[   699.753] (II) "dbe" will be loaded by default.
[   699.753] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[   699.753] (II) "record" will be loaded by default.
[   699.753] (II) "dri" will be loaded by default.
[   699.753] (II) "dri2" will be loaded by default.
[   699.753] (II) LoadModule: "glx"
[   699.754] (II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
[   699.754] (II) Module glx: vendor="FireGL - ATI Technologies Inc."
[   699.754]     compiled for 7.6.0, module version = 1.0.0
[   699.754] (II) Loading extension GLX
[   699.754] (II) LoadModule: "extmod"
[   699.754] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   699.754] (II) Module extmod: vendor="X.Org Foundation"
[   699.754]     compiled for 1.9.0, module version = 1.0.0
[   699.754]     Module class: X.Org Server Extension
[   699.754]     ABI class: X.Org Server Extension, version 4.0
[   699.754] (II) Loading extension MIT-SCREEN-SAVER
[   699.754] (II) Loading extension XFree86-VidModeExtension
[   699.754] (II) Loading extension XFree86-DGA
[   699.754] (II) Loading extension DPMS
[   699.754] (II) Loading extension XVideo
[   699.754] (II) Loading extension XVideo-MotionCompensation
[   699.754] (II) Loading extension X-Resource
[   699.754] (II) LoadModule: "dbe"
[   699.755] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   699.755] (II) Module dbe: vendor="X.Org Foundation"
[   699.755]     compiled for 1.9.0, module version = 1.0.0
[   699.755]     Module class: X.Org Server Extension
[   699.755]     ABI class: X.Org Server Extension, version 4.0
[   699.755] (II) Loading extension DOUBLE-BUFFER
[   699.755] (II) LoadModule: "record"
[   699.755] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   699.755] (II) Module record: vendor="X.Org Foundation"
[   699.755]     compiled for 1.9.0, module version = 1.13.0
[   699.755]     Module class: X.Org Server Extension
[   699.755]     ABI class: X.Org Server Extension, version 4.0
[   699.755] (II) Loading extension RECORD
[   699.755] (II) LoadModule: "dri"
[   699.756] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   699.756] (II) Module dri: vendor="X.Org Foundation"
[   699.756]     compiled for 1.9.0, module version = 1.0.0
[   699.756]     ABI class: X.Org Server Extension, version 4.0
[   699.756] (II) Loading extension XFree86-DRI
[   699.756] (II) LoadModule: "dri2"
[   699.756] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   699.756] (II) Module dri2: vendor="X.Org Foundation"
[   699.756]     compiled for 1.9.0, module version = 1.2.0
[   699.756]     ABI class: X.Org Server Extension, version 4.0
[   699.756] (II) Loading extension DRI2
[   699.756] (II) LoadModule: "fglrx"
[   699.756] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[   699.771] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[   699.771]     compiled for 1.4.99.906, module version = 8.78.30
[   699.771]     Module class: X.Org Video Driver
[   699.771] (II) Loading sub module "fglrxdrm"
[   699.771] (II) LoadModule: "fglrxdrm"
[   699.771] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[   699.771] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[   699.771]     compiled for 1.8.99.905, module version = 8.78.30
[   699.771] (II) ATI Proprietary Linux Driver Version Identifier:8.78.30
[   699.771] (II) ATI Proprietary Linux Driver Release Identifier: 8.78.3                               
[   699.771] (II) ATI Proprietary Linux Driver Build Date: Sep 20 2010 21:30:49
[   699.771] (--) using VT number 8

[   699.775] (WW) Falling back to old probe method for fglrx
[   699.779] (II) PCS database file /etc/ati/amdpcsdb not found
[   699.779] (II)   Creating PCS database from initial defaults instead
[   699.779] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:0) found
[   699.779] (EE) No devices detected.
[   699.779] 
Fatal server error:
[   699.779] no screens found
[   699.779] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[   699.780] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   699.780] 
```

---

### Post by Kheops_74 on 2010-10-16
Same here. Any new idea?

---

### Post by Kheops_74 on 2010-10-16
I did : sudo apt-get xserver-xorg-video-ati and it seems to work.

It still freeze in Internet Browser but it did it in version 10.4

---

### Post by mightysween on 2010-11-02
I had the exact same problem, but with a Nvidia graphics adapter.  My solution was simply to delete my xorg.conf file completely and reboot. (i suppose renaming it would be "safer" but I like to live on the edge when it comes to Linux :) )

Without an xorg.conf the system falls back to the default graphics configuration, and I was then able to reinstall the latest drivers and get it working properly.

Not an elegant solution, but it worked flawlessly and the system now boots properly.

---

