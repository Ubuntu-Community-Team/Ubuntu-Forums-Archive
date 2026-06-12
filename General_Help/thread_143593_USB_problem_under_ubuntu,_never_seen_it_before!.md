---
title: "USB problem under ubuntu, never seen it before!"
date: 2006-03-12
forum: General Help
---

### Post by Simimi on 2006-03-12
So, I have ubuntu on my desktop and anytime I plug  in any usb device or flash drive, itis automatically found and shows up on my desktop.

I recently put ubuntu on a friends notebook, and none of his flash devices show up on his desktop like they do mine. 

Case in point: We have two flash drives plugged in now and they show up  under 'computer' but when we try to acess them we are notified they are not mounted, when we try to moun them we get this error---

Unable to mount selected volume
 Error: given UDI is not a mountable volume

This has never happened to me and I am not sure how to help him out, any ideas huns? 
 Love-mimi

---

### Post by taurus on 2006-03-12
How exactly did you try to mount them?  Did it look something like
```

sudo mkdir /media/usb1 /media/usb2
sudo mount -t vfat /dev/sda /media/usb1
sudo mount -t vfat /dev/sdb /media/usb2

```

---

### Post by Simimi on 2006-03-12
No, we went to 'computer' and clicked on them,
 some people on the irc channel said to try
 sudo mkdir -p a/b

but it has not fixed anything, this is truely wierd I have never seen this before.
 love-mimi

---

### Post by Simimi on 2006-03-12
ALSO I did-
 sudo dmesg | grep -i usb
and it returned...

[4309684.117000] usb 1-2: new full speed USB device using uhci_hcd and address 2[4309685.838000] usbcore: registered new driver snd-usb-audio
[4309685.841000] pwc Logitech QuickCam 4000 Pro USB webcam detected.
[4309685.844000] usbcore: registered new driver Philips webcam
[4309880.506000] usb 2-1: new high speed USB device using ehci_hcd and address 3[4309880.869000] Initializing USB Mass Storage driver...
[4309880.875000] scsi0 : SCSI emulation for USB Mass Storage devices
[4309880.877000] usb-storage: device found at 3
[4309880.877000] usb-storage: waiting for device to settle before scanning
[4309880.877000] usbcore: registered new driver usb-storage
[4309880.877000] USB Mass Storage support registered.
[4309880.986000] usb 2-1: USB disconnect, address 3
[4309881.160000] usb 2-1: new high speed USB device using ehci_hcd and address 4[4309881.242000] scsi1 : SCSI emulation for USB Mass Storage devices
[4309881.244000] usb-storage: device found at 4
[4309881.244000] usb-storage: waiting for device to settle before scanning
[4309886.244000]   Vendor:           Model: USB DISK 28X      Rev: PMAP
[4309886.255000] usb-storage: device scan complete
[4310242.486000] usb 2-1: USB disconnect, address 4
[4310246.451000] usb 1-2: USB disconnect, address 2
[4310257.902000] usb 2-2: new high speed USB device using ehci_hcd and address 5[4310257.984000] scsi2 : SCSI emulation for USB Mass Storage devices
[4310257.986000] usb-storage: device found at 5
[4310257.986000] usb-storage: waiting for device to settle before scanning
[4310262.986000]   Vendor:           Model: USB DISK 28X      Rev: PMAP
[4310263.117000] usb 1-1: new full speed USB device using uhci_hcd and address 3[4310263.269000] usb-storage: device scan complete
[4310263.349000] pwc Logitech QuickCam 4000 Pro USB webcam detected.
[4310493.701000] usb 1-1: USB disconnect, address 3
[4310496.486000] usb 2-2: USB disconnect, address 5
[4310499.652000] usb 2-1: new high speed USB device using ehci_hcd and address 7[4310499.734000] scsi3 : SCSI emulation for USB Mass Storage devices
[4310499.736000] usb-storage: device found at 7
[4310499.736000] usb-storage: waiting for device to settle before scanning
[4310504.736000]   Vendor:           Model: USB DISK 28X      Rev: PMAP
[4310505.438000] usb-storage: device scan complete
[4310584.236000] usb 2-1: USB disconnect, address 7
[4310597.652000] usb 2-1: new high speed USB device using ehci_hcd and address 8[4310597.748000] scsi4 : SCSI emulation for USB Mass Storage devices
[4310597.750000] usb-storage: device found at 8
[4310597.750000] usb-storage: waiting for device to settle before scanning
[4310602.750000]   Vendor:           Model: USB DISK 20X      Rev: PMAP
[4310603.216000] usb-storage: device scan complete
[4310680.902000] usb 2-2: new high speed USB device using ehci_hcd and address 9[4310680.984000] scsi5 : SCSI emulation for USB Mass Storage devices
[4310680.986000] usb-storage: device found at 9
[4310680.986000] usb-storage: waiting for device to settle before scanning
[4310685.986000]   Vendor:           Model: USB DISK 28X      Rev: PMAP
[4310686.267000] usb-storage: device scan complete
simimi@ubuntu:~$

---

### Post by Simimi on 2006-03-12
so ok we tried..

sudo pmount -d /dev/sda1 

and sure enough now it works and we can access one of them

Is there a command to see what the things in 'computer' under nautilus are called, such as the flash drive being sda1?
I'm sure there is but we do not know it.
love-mimi

---

### Post by Simimi on 2006-03-12
OK! So we got them both working and whatnot, and now the original user, nor myself have perms to view the flash drives (sda1 and sdb1 respectivly)

Wer both have all of the perm boxes check on the users and groups config menu, and we we try to log in as root user from the main ubuntu login screen, we are told that we can not log in as root user...

 So how do we get these so-called perms to see our own flash media, and make it so we can log in as root from the main login?
 love-mimi:confused:

---

### Post by OBnascar on 2006-03-12
[QUOTE=Simimi]make it so we can log in as root from the main login?[/QUOTE]

One does not log in as root in Ubuntu, you enter your user name & password to log in.

For your last question, enter in a terminal:
sudo df -h

To learn more about root and sudo, see[[COLOR="DarkOrange"]**THIS**[/COLOR]]("https://wiki.ubuntu.com/RootSudo")

---

### Post by OBnascar on 2006-03-12
OH, and welcome to the ubuntu forums Simimi, I hope you enjoy ubuntu as much as I have. Don't give up on it, it takes time, the learning curve and effort is worth it.........jerry

---

### Post by White_Tiger on 2006-08-06
Hello,

I have the same problem with my new Apacer 4GB USB Flash drive.

it was working fine tell I wanted to format it as NTFS file system.

the windows says I have to change the policy to performance mode instead of removable mode, I saied OK. after that the USB becomes unaccessable and always telling me to insert a disk to drive, it becomes like USB CARD READER and the led always on.

I went to device manager to check it, the name was changed to (USB DISK 28X USB Device)

I searched in the internet for this problem then I saw this Thread

after that I returned to my Ubuntu to try the command
sudo dmesg | grep -i usb

and it returned

[4294669.107000]  USB
[4294671.713000] usbcore: registered new driver usbfs
[4294671.713000] usbcore: registered new driver hub
[4294671.713000] USB Universal Host Controller Interface driver v2.3
[4294671.720000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[4294671.721000] hub 1-0:1.0: USB hub found
[4294953.097000] usb 1-1: new full speed USB device using uhci_hcd and address 2[4294953.420000] Initializing USB Mass Storage driver...
[4294953.425000] scsi1 : SCSI emulation for USB Mass Storage devices
[4294953.427000] usb-storage: device found at 2
[4294953.427000] usb-storage: waiting for device to settle before scanning
[4294953.428000] usbcore: registered new driver usb-storage
[4294953.428000] USB Mass Storage support registered.
[4294958.439000]   Vendor:           Model: USB DISK 28X      Rev: 3.00
[4294958.481000] usb-storage: device scan complete

then I did
sudo pmount -d /dev/sda1 

and it returned

/dev/sda1 cannot be resolved to a proper device node
mount point to be used: /media/sda1
no iocharset given, current locale encoding is UTF-8
locale encoding uses UTF-8, setting iocharset to 'utf8'
Cleaning lock directory /var/lock/pmount/_dev_sda1
Error: device /dev/sda1 does not exist
policy check failed


I'm not an expert in Linux commands

so now what shall I do next to fix this problem ?

Best regards,

---

### Post by francocerisola on 2006-08-15
hi,
same problem too!,
I check all the forum for answers, but nothing.

---

### Post by francocerisola on 2006-08-15
I don't know if you need this, but my /etc/fstab file is:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/sda6 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
/dev/sda7 /home ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
/dev/sda1 /media/sda1 ntfs defaults,uid=1000,gid=1000,auto,rw,nouser 0 0
/dev/sda5 none swap sw 0 0
/dev/hda /media/cdrom auto users,atime,auto,rw,dev,exec,suid 0 0
/dev/hda /media/cdrom0 auto users,atime,auto,rw,nodev,noexec,nosuid 0 0
/dev/sdb1 /media/sdb1 vfat uid=1000,gid=1000,auto,rw,users 0 0
/dev/sr0 /media/cdrom1 auto users,atime,noauto,ro,nodev,noexec,nosuid 0 0
proc /proc proc auto 0 0

---

### Post by alowe on 2007-06-14
I think I have worked this out... 

I was having problems with this in 7.04, and found I had an entry in my /etc/fstab for /dev/sdb1 that the device was being found as, removing this fixed the problem.

These newer? larger? usb disk drives seem to have a partition table (like a hard disk drive), so they can be partitioned like a hdd.  The block device to be mounted is therefor /dev/sdb1 by default, rather then /dev/sdb like the older drives.  

I hope this helps people who had problems

---

