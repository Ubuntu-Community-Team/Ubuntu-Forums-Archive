---
title: "Can`t see  usb flash disks"
date: 2011-08-18
forum: General Help
---

### Post by IT Support on 2011-08-18
hi all

i just install lubuntu  and  everything is work but it can`t` see my usb flash disks ,  usb ports is working  because when i plug there my mouse it begin to  work 
is any solution?

I have Fujitsu Siemens amilo pro v8010

---

### Post by AleveSicofante on 2011-08-18
I have exactly the same problem. It arose after I manually updated the system, a few minutes ago. It was working before that.

It's very frustrating and I have a particular urgency here since I've been given this laptop for repair.

Any help will be highly appreciated.

BTW: It's not just disk here. A WiFi dongle that was recognized before, isn't any more. Mouse is and an external keyboard too. Have tried two different pendrives and no luck.

---

### Post by spiky001 on 2011-08-18
Have a look in /media see if they are reckognised  in there.
If not type ```
lsusb
``` without the flash drive inserted then try it with flash drive inserted see if there is a difference in output

---

### Post by AleveSicofante on 2011-08-18
They aren't even recognized via sudo fdisk -l

Here's lsusb output both before and after:

```

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```Now here's the output if a mouse is plugged in:

```

Bus 003 Device 024: ID 046d:c040 Logitech, Inc. Corded Tilt-Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```The only special thing: lsusb is somewhat blocked for a few seconds after plugging one of the flashdrives, as if it was trying. It's instantaneous after plugging the mouse.

---

### Post by IT Support on 2011-08-18
> **spiky001 said:**
> Have a look in /media see if they are reckognised  in there.
If not type ```
lsusb
``` without the flash drive inserted then try it with flash drive inserted see if there is a difference in output

root@Linuxoid:~# lsusb
Bus 005 Device 002: ID 15d9:0a4c Trust International B.V. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0bf8:1003 Fujitsu Siemens Computers 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@Linuxoid:~# lsusb
Bus 005 Device 002: ID 15d9:0a4c Trust International B.V. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0bf8:1003 Fujitsu Siemens Computers 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0951:1625 Kingston Technology DataTraveler 101 II
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


after plug in usb flash  there i can see it "kingston technology datatravel 101 II" what i can do??

---

### Post by IT Support on 2011-08-18
> **AleveSicofante said:**
> I have exactly the same problem. It arose after I manually updated the system, a few minutes ago. It was working before that.

It's very frustrating and I have a particular urgency here since I've been given this laptop for repair.

Any help will be highly appreciated.

BTW: It's not just disk here. A WiFi dongle that was recognized before, isn't any more. Mouse is and an external keyboard too. Have tried two different pendrives and no luck.

if you have broadcom maybe it will help you 
[http://afreedenfield.livejournal.com/13106.html?thread=3122#a](http://afreedenfield.livejournal.com/13106.html?thread=3122#a)

---

### Post by AleveSicofante on 2011-08-18
> **IT Support said:**
> if you have broadcom maybe it will help you 
[http://afreedenfield.livejournal.com/13106.html?thread=3122#a](http://afreedenfield.livejournal.com/13106.html?thread=3122#a)
It's not about making it work. It worked a few minutes ago before the USB disaster that happened just after the update.

I'm not as lucky as spiky001. I don't even see the drives plugged in via lsusb. Only mouse and keyboard appear there.

Of course, both flash drives can be perfectly seen on a Macbook Pro and a Windows desktop I have right here at my office.

---

### Post by IT Support on 2011-08-18
> **AleveSicofante said:**
> It's not about making it work. It worked a few minutes ago before the USB disaster that happened just after the update.

I'm not as lucky as spiky001. I don't even see the drives plugged in via lsusb. Only mouse and keyboard appear there.

Of course, both flash drives can be perfectly seen on a Macbook Pro and a Windows desktop I have right here at my office.

at last i had ubuntu 11.04 and there i hadn`t problems only  slow work ubuntu  , i heared that lubuntu is faster than ubuntu 11.04 and because i install lubuntu , it is realy faster but  why i want this fast work if somethings don`t work in it? :D 

enyone can help me with flash drive? i realy wont  it , i am  IT support and  every day i use flash drive  it is very important thing for me , if today i can`t  did this  i will reinstall lubuntu and still install ubuntu  :)


P.S and i have one question ! can i install gnome desktop on the lubuntu? i hate KDE  :(  and if yes  how i will do it??

---

### Post by spiky001 on 2011-08-18
IT Support you should be able to mount yours with the mount command. The output of ```
sudo fdisk -l
``` will give you the dev label

---

### Post by IT Support on 2011-08-18
> **spiky001 said:**
> IT Support you should be able to mount yours with the mount command. The output of ```
sudo fdisk -l
``` will give you the dev label

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001bc8d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3040    24413184   83  Linux
/dev/sda2            3040        7296    34189313    5  Extended
/dev/sda5            3040        7175    33212416   83  Linux
/dev/sda6            7175        7296      975872   82  Linux swap / Solaris
root@Linuxoid:~#



where is  my flash disk? i can`t see it  and  how to mount  ? i am new in linux and i amn`t prof  linuxoid  :D


in this table something is wrong  :D and there is write proximately  80gb, 
and how i guess  in swap i have my flash disk too 
i remember that before i had 1 gb swap
i have 60GB of hdd

---

### Post by cprofitt on 2011-08-18
If your usb drives are formatted ext3/4 you may not have permissions.  Try alt+f2 gksu nautilus and see if you see the drives then.

---

### Post by IT Support on 2011-08-18
> **cprofitt said:**
> If your usb drives are formatted ext3/4 you may not have permissions.  Try alt+f2 gksu nautilus and see if you see the drives then.

no it isn`t formated  to ext , it is formated in ntfs  and i can`t see it in nautilus :(

---

### Post by AleveSicofante on 2011-08-18
Don't ask me why. I turned my computer completely off, then turn it on again and USB drives are visible again. (Rebooting didn't do the trick, BTW).

Scary.

---

### Post by IT Support on 2011-08-18
> **AleveSicofante said:**
> Don't ask me why. I turned my computer completely off, then turn it on again and USB drives are visible again. (Rebooting didn't do the trick, BTW).

Scary.

haha u doing miracle s my bro :D :D

no no i try it  to reboot and turn off too  :)

---

### Post by spiky001 on 2011-08-18
With usb unplugged ```
gedit /var/log/syslog
``` then plug in usb It should report and give the dev name, Give it a few seconds to register

---

### Post by IT Support on 2011-08-18
> **spiky001 said:**
> With usb unplugged ```
gedit /var/log/syslog
``` then plug in usb It should report and give the dev name, Give it a few seconds to register

i get this log 


> Aug 18 21:46:57 Linuxoid kernel: [ 5228.580049] usb 1-1: new high speed USB device using ehci_hcd and address 9

what is it?

---

### Post by spiky001 on 2011-08-18
Did that appear when you plugged in device. Can you try the device on another machine dose it work ok

---

### Post by IT Support on 2011-08-18
> **spiky001 said:**
> Did that appear when you plugged in device. Can you try the device on another machine dose it work ok

i have 3 flash drives  :) and  today they work in windows  :)

---

### Post by spiky001 on 2011-08-18
Have you tried starting the machine with the usb plugged in. Otherwise I,m at a bit of a loss, maybe some has more info

---

### Post by IT Support on 2011-08-18
> **spiky001 said:**
> Have you tried starting the machine with the usb plugged in. Otherwise I,m at a bit of a loss, maybe some has more info
yes i tryed it before u post and how strange it is sound  lubuntu has saw flash disk but i dislike lubuntu and  still install ubuntu  but not Natty , i install maverick, and  all hardware  and software are  working great , thank you all to replay me  to help  :) :popcorn:

---

### Post by spiky001 on 2011-08-18
I could not find any fixes on google. Glad you got it working tho

---

### Post by IT Support on 2011-08-18
> **spiky001 said:**
> I could not find any fixes on google. Glad you got it working tho
yeah it was strange problem  :D 

Ubuntu forever  :guitar:

---

