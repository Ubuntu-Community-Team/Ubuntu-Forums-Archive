---
title: "modprobe on boot"
date: 2009-12-01
forum: General Help
---

### Post by de_pol on 2009-12-01
Hi all.

I need to remove the kvm_intel module before i can start VirtualBox

When I run
```
sudo modprobe -r kvm_intel
``` i can run my virtualbox without any problems. I tried to automate this process on startup, so I added kvm_intel in the /etc/modprobe.d/blacklist.conf file:

```
blacklist kvm_intel
``` but it didn't changed anything after a reboot.

Can you guys put me in the right direction?

kr,

de_pol

---

### Post by hal10000 on 2009-12-01
You can disable a module to be loaded on startup if you put a line like
```
blacklist kvm_intel
```
into the file **/etc/modprobe.d/blacklist**. You have to edit the file as root.

---

### Post by de_pol on 2009-12-01
Ok, I'll create the /etc/modprobe.d/blacklist file. I added the line in the /etc/modprobe.d/blacklist.conf file, but this isn't working

kr,

de_pol

edit: I put blacklist kvm_intel in the **/etc/modprobe.d/blacklist** file, I rebooted, but I still need to manually disable this through modprobe -r

these are my files:
```

$ cat /etc/modprobe.d/blacklist
blacklist kvm_intel
```

```

$ cat /etc/modprobe.d/blacklist.conf 
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

#some vbox things
blacklist kvm_intel
```

---

### Post by hal10000 on 2009-12-01
I'm sorry, i made a mistake. The name of the file is /etc/modprobe.d/blacklist.conf
Just put your entry at the end of the file.

[EDIT]
I this doesnt work, then i don't know what to do, because this is the way to prevend modules from being loaded at boot time.

The only thing i can imagine is that the kvm_intel module is not loaded at boottime, but by another process after booting the system.

---

### Post by de_pol on 2009-12-01
as you can see in my previous post, i allready did this. is there a possibility this blacklist.conf file isn't executed at boot?

---

### Post by hal10000 on 2009-12-01
> is there a possibility this blacklist.conf file isn't executed at boot

No, this file is always read during the boot process. I'm sorry, i have no idea what's going wrong.

---

### Post by de_pol on 2009-12-01
really strange. the line is realy there :)
```

remy@remy-laptop:~$ cat /etc/modprobe.d/blacklist.conf | grep kvm
blacklist kvm_intel
remy@remy-laptop:~$
```

---

### Post by hal10000 on 2009-12-02
did you install the kvm package? Maybe you can remove it or at least prevend it from being started.

---

### Post by de_pol on 2009-12-02
no, it is not installed, it was one of the first things I checked.

```

remy@remy-laptop:~$ aptitude search kvm
p   ikvm                            - Java virtual machine for the CLI          
p   kvm                             - dummy transitional pacakge for qemu-kvm   
v   kvm-api-4                       -                                           
p   kvm-pxe                         - PXE ROM's for KVM                         
p   libikvm-native                  - native library for IKVM.NET               
c   qemu-kvm                        - Full virtualization on i386 and amd64 hard
p   qemu-kvm-extras                 - fast processor emulator binaries for non-x
remy@remy-laptop:~$
```

should I enter a bug report? or...

kr,

de_pol

---

