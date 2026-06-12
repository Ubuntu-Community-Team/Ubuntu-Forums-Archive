---
title: "Persistent installation on a pendrive problems"
date: 2009-08-07
forum: General Help
---

### Post by madbyte on 2009-08-07
Hi,

1)
Im new to Ubuntu, and I installed Ubuntu 9.04 first following the toturial in this link  [http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/) on a 8Gb Kingston Datatraveler pendrive and then using* uSbuntu Live Creator* with the same result in both installations, everything is ok but when I have to restart or shutdown I'm getting some errors like this:

end_request: I/O error, dev sdb, sector 3902973
end_request: I/O error, dev sdb, sector 3919321
end_request: I/O error, dev sdb, sector 1461721
end_request: I/O error, dev sdb, sector 1461753
end_request: I/O error, dev sdb, sector 1475079
etc..

then my pc is restared or turned off.

2)
When Ubuntu 9.04 was started for the first time I had access to my hard disk (format: NTFS and Windows XP) but after restarting (and getting the errors) can't mount it again, showing this:

mount:according to mtab,/dev/sda1 is already mounted on media/disk-1

Any help?
Thanks

---

### Post by P4man on 2009-08-07
what is sdb ? Is it your XP drive ?
If you're not sure, in ubuntu, open a terminal and type:

```
sudo fdisk -l
```

and copy/paste the output here. 

As for the second issue, I suspect your NTFS volume is "dirty". That happens when windows is not closed down properly. You can force the mount, but its a better idea to just boot windows, and shut it down again.

---

### Post by madbyte on 2009-08-07
Hi, 

> **P4man said:**
> what is sdb ? Is it your XP drive ?
If you're not sure, in ubuntu, open a terminal and type:

```
sudo fdisk -l
```and copy/paste the output here.

[I]Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x98ce98ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38912   312560608+   7  HPFS/NTFS

Disk /dev/sdb: 8015 MB, 8015282176 bytes
32 heads, 63 sectors/track, 7765 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Disk identifier: 0x51697071

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7765     7827088+   b  W95 FAT32[/I]

> **P4man said:**
> As for the second issue, I suspect your NTFS volume is "dirty". That happens when windows is not closed down properly. You can force the mount, but its a better idea to just boot windows, and shut it down again.

I did as you suggested but still getting the same mount error. When Ubuntu was started for the first time I had access to my hard disk, the next reboot failed to mount it.

---

### Post by P4man on 2009-08-08
So sdb (where you get errors from) is your usb stick. It might be dying, although Ive seen similar errors on sticks that seemed ok to me. Not quite sure...

As for the mounting; It says its already mounted. What happens when you browse to /media/disk-1 ?

---

### Post by madbyte on 2009-08-08
Hi again, thank you for answering

> **P4man said:**
> So sdb (where you get errors from) is your usb stick. It might be dying, although Ive seen similar errors on sticks that seemed ok to me. Not quite sure...

Strange...:confused:  my usb stick is new, I bought it 2 weeks ago, anyway I checked it using Check Flash utility reporting no errors on it.

[IMG]http://img14.imageshack.us/img14/3510/imagen2led.jpg[/IMG]


[IMG]http://img9.imageshack.us/img9/3551/imagen3udq.jpg[/IMG]



> **P4man said:**
> As for the mounting; It says its already mounted. What happens when you browse to /media/disk-1 ?

I'm going to try later since I had to format the pendrive to make the test.

---

### Post by madbyte on 2009-08-10
ok, after reinstalling all the mount error is now:

*mount:according to mtab,/dev/sda1 is already mounted on media/disk*

and the media folder is empty.

Anyway, I'm quiting :( I tried to install the nvidia driver and more problems... after the reset in the menu System/Administration/Hardware Drivers/ it say that the nvidia driver (180) is not activated:[I] 

"A different version of this driver is in use"[/I]

And in the menu *NVIDIA X Server Setting*s:

*"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."*

too many errors for a newbie... :confused:

---

### Post by zkriesse on 2009-08-10
search the forums and google it man! DON"T GIVE UP!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by P4man on 2009-08-10
Some of the problems you're having (like the nvidia driver) seem related to the fact you're making a "persistent live cd", which is a bit of a hack by itself, and not without issues. You can install nvidia drivers on a live cd, but not just using built in "wizard". 

I would advice to try ubuntu out on a spare drive if thats an option, or even do a full, normal install on the usb stick (which requires another stick or cd to install from).  8GB is enough for a normal install, and while it costs drive space, it gets you back normality as well as faster boot times. Then try it out for a while, and if you must have a persistent live stick, you can turn your customized and installed copy of ubuntu in to one. But know that even a normal install will boot on pretty much any computer without too much problems.

---

### Post by madbyte on 2009-08-10
> **P4man said:**
> Some of the problems you're having (like the nvidia driver) seem related to the fact you're making a "persistent live cd", which is a bit of a hack by itself, and not without issues.

ok, you're right.

> **P4man said:**
> I would advice to try ubuntu out on a spare drive if thats an option, or even do a full, normal install on the usb stick (which requires another stick or cd to install from).  8GB is enough for a normal install, and while it costs drive space, it gets you back normality as well as faster boot times. Then try it out for a while, and if you must have a persistent live stick, you can turn your customized and installed copy of ubuntu in to one. But know that even a normal install will boot on pretty much any computer without too much problems.

I'm gonna try a normal installation on my usb stick and see what happen. 

Thank you :P

---

### Post by peterjohndavies on 2009-08-13
I have the same problem on my pendrive with persistant. It seems thatthe drives remain open in mtab when we close down but close in fstab. thus when you try to mount the windows disk it says it is already mounted in mtab, but if you try to unmount it you get a message saying it is not mounted. I tried amending mtab but now get a message on boot "cannot create link /etc/mstab perhaps a stale lock file" how can I rectify this?
Also, how do you install on a pendrive without persistant. Is this a normal Linux install where you get the choice of windows / linux at start up. Any tips appreciated:confused:

---

### Post by pakki on 2009-08-18
> **madbyte said:**
> Hi,

1)
Im new to Ubuntu, and I installed Ubuntu 9.04 first following the toturial in this link  [http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/) on a 8Gb Kingston Datatraveler pendrive and then using* uSbuntu Live Creator* with the same result in both installations, everything is ok but when I have to restart or shutdown I'm getting some errors like this:

end_request: I/O error, dev sdb, sector 3902973
end_request: I/O error, dev sdb, sector 3919321
end_request: I/O error, dev sdb, sector 1461721
end_request: I/O error, dev sdb, sector 1461753
end_request: I/O error, dev sdb, sector 1475079
etc..

then my pc is restared or turned off.

2)
When Ubuntu 9.04 was started for the first time I had access to my hard disk (format: NTFS and Windows XP) but after restarting (and getting the errors) can't mount it again, showing this:

mount:according to mtab,/dev/sda1 is already mounted on media/disk-1

Any help?
Thanks

That is the very problem that I am experiencing. & I tried each & every method but didn't run any perisistent Ubuntu e.g I tried Live USB Unetboot.. but nothing helped I am able to run Ubuntu jaunty but can't make it persistent
I have 4gb kingston & my OS ix XP SP3

---

### Post by shel on 2009-10-05
I am not experienced in linux, but I find that if you delete the mtab and derivative files, the next time the pen drive boots up it will be able to see the hard disk. Closing the ubuntu apparently does not cleanly get rid of the mtab file. Open the terminal and type something like "sudo rm /etc/mtab" and for any other mtab-like files lurking in the etc file. 

Hope this helps. you will only be able to access the hard disk until you shut ubuntu down. then the same phenomenon, of leaving the mtab file in place, will occur.

---

### Post by mathew7 on 2012-03-08
Sorry to open such an old thread, but I got (and still get) this in 12.04 alpha2 and beta1.
I think it may have to do with **unmounting the parent partition and shutting down/resetting before the usb driver or flash controller has any opportunity to write all changes** (since a flash driver is typically way slower than an HDD for 4K writes). I say this because after shutdown, if I enter in Live mode (non-persistent) and run fsck on casper-rw and home-rw, fsck reports correcting errors. It seems that a HDD over USB does not exhibit same behavior, or it's very light. Also, a long time ago while using a company-provided laptop in a business trip, I remember I could not use a Corsair Voyager GT and had to use the slower Sandisk Cruiser Contour. I used it every night over a week.
PS: Actually I'm using xubuntu now (12.04), but I don't think they're different in this stage.

---

