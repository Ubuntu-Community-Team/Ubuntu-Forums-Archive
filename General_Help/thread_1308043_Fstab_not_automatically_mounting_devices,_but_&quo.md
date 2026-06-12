---
title: "Fstab not automatically mounting devices, but &quot;mount -a&quot; does!?"
date: 2009-10-31
forum: General Help
---

### Post by olivertreend on 2009-10-31
Hey

I'm the most bizarre of problems. This is something I've never experienced before.

Basically, upon booting my Ubuntu Server box, fstab doesn't mount my 2 USB external hard drives. However, if I run the command "sudo mount -a", they are mounted correctly as defined in fstab.

Here is my fstab file:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/mapper/roadrunner-root :
UUID=4cad72d9-a1dd-4925-8949-d6cc2e84890a / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=4e51cf03-cf10-45a0-b17c-2fd7fd244c68 /boot ext2 relatime 0 2
# Entry for /dev/mapper/roadrunner-swap_1 :
UUID=76af3bb9-2580-4f8d-b9d6-d753d1faf7c8 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

# Mount Seagate 1TB
/dev/sdb1 /media/seagate ntfs-3g defaults,user,locale=en_GB.utf8 0 0

# Mount OneTouch 500GB
/dev/sdc1 /media/onetouch ntfs-3g defaults,user,locale=en_GB.utf8 0 0
```

I use Samba to share these mounts over the network. In the past, I have never needed to specify the "user" option in fstab, as Samba always used to be able to access this device automatically even with "nouser".

Everything used to work as expected when I only attached and mounted the OneTouch 500GB (previously /dev/sdb1). However, since connecting my Seagate 1TB, things haven't been working properly.

In some odd cases, changing settings for the OneTouch mount in fstab means that Seagate gets mounted on the next reboot - but OneTouch remains unmounted. This is something I've never experienced before.

Could this have something to do with the fact that I had to disable Legacy USB in my BIOS? With this enabled, the machine wouldn't even boot up with both USB HDDs plugged in.

I'm so stuck! I have spent the best part of 5 hours trying to get this working to no avail. I've been searching all over the forums and internet and I haven't found anything similar.

I would greatly appreciate any help you can provide to point me in the right direction!!

Thanks a lot :D

Oliver

---

### Post by Bucky Ball on 2009-10-31
Have you tried using the UUID instead of /dev/sd**?

```
sudo blkid
```

... will find them.

---

### Post by olivertreend on 2009-10-31
> **Bucky Ball said:**
> Have you tried using the UUID instead of /dev/sd**?

```
sudo blkid
```... will find them.

Yes, I have tried UUIDs too... I've never really had any luck with these in the past.
Here is the output of blkid:
```
/dev/sda1: UUID="DgIssN-HSTH-sHFa-jcHW-68fZ-R1GT-X7Q8YZ" TYPE="lvm2pv" 
/dev/sda5: UUID="4e51cf03-cf10-45a0-b17c-2fd7fd244c68" TYPE="ext2" 
/dev/mapper/roadrunner-root: UUID="4cad72d9-a1dd-4925-8949-d6cc2e84890a" TYPE="ext3" 
/dev/mapper/roadrunner-swap_1: TYPE="swap" UUID="76af3bb9-2580-4f8d-b9d6-d753d1faf7c8" 
/dev/sdb1: UUID="723163265957F1E3" TYPE="ntfs" 
/dev/sdc1: UUID="55D123D9E79ABF54" LABEL="OneTouch4" TYPE="ntfs" 

```

I don't know why UUID doesn't work for me. It might have something to do with the fact that UUIDs for the partitions are much shorter than the other partitions on other discs.

What do you think?

---

### Post by Bucky Ball on 2009-10-31
What about running ntfs-3g config GUI again. In there is a box to enable external ntfs drives. That might need to be done again after adding the new external drive.

---

### Post by olivertreend on 2009-10-31
> **Bucky Ball said:**
> What about running ntfs-3g config GUI again. In there is a box to enable external ntfs drives. That might need to be done again after adding the new external drive.

I did try installing ntfs-config (I'm not sure if there's also a ntfs-3g-config that I'm just not aware about). I ran it and it gave me 2 check boxes - 1. enable internal drives, 2. enable external drives. I made sure both of them were checked.

However, this shouldn't be the problem. I never even ran this config utility when the first drive was working correctly. The drive just worked. But now it's just as if fstab forgets to mount them!

I guess I could drop a script in /etc/init.d/ which runs "mount -a", however this is far from ideal as it's just redoing what should already have been done.

---

### Post by renkinjutsu on 2009-10-31
check for glimpses of error messages printed in the console (ctrl+alt+F1) ... quick and dirty way to gather information

---

### Post by olivertreend on 2009-10-31
> **renkinjutsu said:**
> check for glimpses of error messages printed in the console (ctrl+alt+F1) ... quick and dirty way to gather information

I'll just check it now...
but on that note, shouldn't fstab log errors somewhere in /var/log/? Does anywhere know where I could find it?

---

### Post by olivertreend on 2009-10-31
> **renkinjutsu said:**
> check for glimpses of error messages printed in the console (ctrl+alt+F1) ... quick and dirty way to gather information

Just checked...
there's no errors showing in console. Everything looks like it's loading as normal.

It checks for a resume image, doesn't find anything, then does a normal boot. The next thing I see is "Ubuntu 9.04 roadrunner tty1"

No errors.

Good thought though. Maybe fstab isn't finding any errors - maybe it just doesn't read those lines for some reason. Again, no idea why.

Cheers

---

### Post by renkinjutsu on 2009-10-31
thing is.. i don't think the bus's are loaded before the system starts mounting things from fstab.. that's probably why your devices aren't being mounted on startup

a quick and dirty fix would be to add `mount -a` to your /etc/rc.local file and give it a good few seconds with `sleep 3` or so.. (rc.local is the last of the init scripts to be executed)



edit: I only offer quick 'n dirty fixes, because i'm no expert :D

---

### Post by olivertreend on 2009-10-31
> **renkinjutsu said:**
> thing is.. i don't think the bus's are loaded before the system starts mounting things from fstab.. that's probably why your devices aren't being mounted on startup

a quick and dirty fix would be to add `mount -a` to your /etc/rc.local file and give it a good few seconds with `sleep 3` or so.. (rc.local is the last of the init scripts to be executed)



edit: I only offer quick 'n dirty fixes, because i'm no expert :D

Okay... so what would the reason be for the buses not loading before the system starts?
I had to disable Legacy USB in my BIOS before the machine would even boot. It didn't like the 1TB drive for some reason. Now this has been disabled, the machine boots. But would this explain the buses not loading?

---

### Post by renkinjutsu on 2009-10-31
try this..
open up a terminal and type in ```
lsusb
```
you should get an output like ```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 005 Device 002: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 046d:0802 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

find your devices.. and use the ID (example Bus 007 Device 001: [COLOR="Red"]ID 1d6b:0001[/COLOR] Linux Foundation 1.1 root hub)

copy the digits before the colon (example: [COLOR="red"]id6b[/COLOR]) and then do this

```
dmesg|grep -e [COLOR="red"]id6b[/COLOR] -e mount
# replace with your own, of course
```

This will list all the mount output text as well as information on your usb devices

the information is printed in chronological order, so you can see if your system is trying to mount things before the usb devices are even loaded

---

### Post by olivertreend on 2009-10-31
> **renkinjutsu said:**
> thing is.. i don't think the bus's are loaded before the system starts mounting things from fstab.. that's probably why your devices aren't being mounted on startup

a quick and dirty fix would be to add `mount -a` to your /etc/rc.local file and give it a good few seconds with `sleep 3` or so.. (rc.local is the last of the init scripts to be executed)



edit: I only offer quick 'n dirty fixes, because i'm no expert :D

Thanks a lot for your suggestion.
I added the following to my rc.local:
```
sleep 3
mount -a
```

This seems to have done the trick! :D Thanks again.

However, I'm now intrigued as to why the bus wasn't loaded at boot time when fstab did its thing. I've never had this problem before - ever. So I don't know why I should be experiencing it now. :-k :confused:

---

### Post by olivertreend on 2009-10-31
> **renkinjutsu said:**
> try this..
open up a terminal and type in ```
lsusb
```
you should get an output like ```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 005 Device 002: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 046d:0802 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

find your devices.. and use the ID (example Bus 007 Device 001: [COLOR="Red"]ID 1d6b:0001[/COLOR] Linux Foundation 1.1 root hub)

copy the digits before the colon (example: [COLOR="red"]id6b[/COLOR]) and then do this

```
dmesg|grep -e [COLOR="red"]id6b[/COLOR] -e mount
# replace with your own, of course
```

This will list all the mount output text as well as information on your usb devices

the information is printed in chronological order, so you can see if your system is trying to mount things before the usb devices are even loaded

I tried that. I am only getting 1 line returned per device. In fact, the **exact same** line is returned for both devices:
```
[    4.172902] EXT3-fs: mounted filesystem with ordered data mode.
```

Does this mean that the system is only trying to mount it once? In which case, I guess this is because of the newly added "mount -a" command in rc.local

---

### Post by renkinjutsu on 2009-10-31
hold on.. the ID idea was bad.. i took a closer look at the dmesg output and you should use this instead ```
dmesg|grep -e "usb-storage" -e mount
```

and if the USB stuff appears AFTER the mount stuff, then that just means the USB devices aren't being discovered at the time the system is mounting the fstab entries

---

### Post by olivertreend on 2009-10-31
> **renkinjutsu said:**
> hold on.. the ID idea was bad.. i took a closer look at the dmesg output and you should use this instead ```
dmesg|grep -e "usb-storage" -e mount
```

and if the USB stuff appears AFTER the mount stuff, then that just means the USB devices aren't being discovered at the time the system is mounting the fstab entries

Okay. I've tried that.
I'm not sure how to interpret the output of this, but hopefully you can help? It looks like it's trying to scan the drives or something. :confused:
```
[    4.172902] EXT3-fs: mounted filesystem with ordered data mode.
[   11.068545] usbcore: registered new interface driver usb-storage
[   11.070550] usb-storage: device found at 2
[   11.070554] usb-storage: waiting for device to settle before scanning
[   16.070163] usb-storage: device scan complete
[   19.764996] usb-storage: device found at 3
[   19.764999] usb-storage: waiting for device to settle before scanning
[   24.784936] usb-storage: device scan complete

```

---

### Post by renkinjutsu on 2009-11-01
that just means that your system is discovering the USB devices, AFTER fstab is being mounted.. so really, the two usb devices being mounted don't actually exist at that point in time.

I don't know any other way around it, but adding the mount command at rc.local seems to have done the trick.. You'll have to live with that, for now ;)

---

### Post by olivertreend on 2009-11-01
> **renkinjutsu said:**
> that just means that your system is discovering the USB devices, AFTER fstab is being mounted.. so really, the two usb devices being mounted don't actually exist at that point in time.

I don't know any other way around it, but adding the mount command at rc.local seems to have done the trick.. You'll have to live with that, for now ;)

Well, that sucks then!!
Thanks for the quick fix. You saved me from hours more of hair loss LOL! :p

---

### Post by Bucky Ball on 2009-11-01
> **olivertreend said:**
> But now it's just as if fstab forgets to mount them!


That's the idea. ntfs-3g rewrites the fstab where required. Thought that might kick it into action but no.

---

