---
title: "To change screen resolution"
date: 2010-05-14
forum: General Help
---

### Post by satimis on 2010-05-14
Hi folks,

host - Ubuntu 10.01
guest (VM) - ubuntu 10.01
Sun VirtualBox - virtualizer

How can I change screen resolution?

$ locate xorg.conf```

/usr/lib/X11/xorg.conf.d
/usr/lib/X11/xorg.conf.d/05-evdev.conf
/usr/lib/X11/xorg.conf.d/10-synaptics.conf
/usr/lib/X11/xorg.conf.d/10-vmmouse.conf
/usr/lib/X11/xorg.conf.d/10-wacom.conf
/usr/share/man/man5/xorg.conf.5.gz

```

xorg.conf doesn't existing

System -> Preferences -> Monitor
800x600 max.

Thanks

B.R.
satimis

---

### Post by wojox on 2010-05-14
What do you have for graphics?

```
lspci | grep VGA
```

---

### Post by satimis on 2010-05-14
> **wojox said:**
> What do you have for graphics?

```
lspci | grep VGA
```

On guest (VM)

$ lspci | grep VGA```

00:02.0 VGA compatible controller: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter

```


On host

$ lspci | grep VGA```

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3300 Graphics

```

same ubuntu 10.04 version


B.R.
satimis

---

### Post by Muhammad Takdir on 2010-05-14
> **satimis said:**
> 
$ lspci | grep VGA```

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3300 Graphics

```same ubuntu 10.04 version

B.R.
satimis

May be this uri can help ?
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/285517](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/285517)

---

### Post by satimis on 2010-05-14
Hi folks,

Solution found as follow (nothing to do with Ubuntu);

On host
Applications -> System Tools -> Sun VirtualBox

highlight the VM (Ubuntu 10.04)

Settings -> Storage -> Attributes
CD/DVD Device: VBoxGuestAddition.ISO

Boot up the VM.

After login.  On console;

$ cd /cdrom
$ sudo ./VBoxLinuxAdditions_amd64.run

$ sudo nano /etc/X11/xorg.conf
to create an empty file.  Put following lines on it```

Section "Device"
Identifier "VirtualBox Video Card"
Driver "vboxvideo"
EndSection

Section "InputDevice"
Identifier "VBoxMouse"
Driver "vboxmouse"
Option "CorePointer"
EndSection

```


then run;
$ sudo /etc/init.d/vboxadd setup```

Removing old VirtualBox vboxvideo kernel module ...done.
Removing old VirtualBox vboxvfs kernel module ...done.
Removing old VirtualBox vboxguest kernel module ...done.
Building the VirtualBox Guest Additions kernel modules
Building the main Guest Additions module ...done.
Building the shared folder support module ...done.
Building the OpenGL support module ...done.
Doing non-kernel setup of the Guest Additions ...done.
You should restart your guest to make sure the new modules are actually used

```

Reboot the VM

That is ALL.  Screen can be resized.

satimis

---

