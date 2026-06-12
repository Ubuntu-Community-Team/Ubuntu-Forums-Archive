---
title: "Problems with Media Centre remote"
date: 2010-05-09
forum: General Help
---

### Post by bert682 on 2010-05-09
Hi guys,

Been using Ubuntu on and off for a while and decided to do a proper setup.  I cant remember if I ever had the remote control working but tried this morning and getting nowhere.  I have searched around and think I am getting somewhere but im lost now.  

```
bert@bert-desktop:~$ lsusb
Bus 006 Device 002: ID 147a:e00d Formosa Industrial Computing, Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0609:031d SMK Manufacturing, Inc. eHome Infrared Receiver
Bus 003 Device 002: ID 1532:0101 Razer USA, Ltd Copperhead Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:00dd Microsoft Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 2.0 Stick (4GB) / PNY Attache 4GB Stick
Bus 001 Device 006: ID 0bda:0111 Realtek Semiconductor Corp. Card Reader
Bus 001 Device 005: ID 13fe:3100 Kingston Technology Company Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```So, Bus 003 Device 003: ID 0609:031d SMK Manufacturing, Inc. eHome Infrared  Receiver, is the USB receiver.  

I installed lirc and was presented with a list of manufactures, didnt see mine, the remote is Acer branded.  So I went with, "Windows Media Center Transceivers/Remotes (all)", no luck.

```
bert@bert-desktop:~$ irw
000000037ff07bdf 00 Left mceusb
000000037ff07bde 00 Right mceusb
000000037ff07bde 01 Right mceusb
000000037ff07be1 00 Up mceusb
000000037ff07be0 00 Down mceusb
000000037ff07be0 01 Down mceusb
000000037ff07bf1 00 Mute mceusb
000000037ff07be5 00 Skip mceusb
000000037ff07beb 00 Forward mceusb
^C
```So the system is detected my remote signals, just not acting on them.  I think its almost there I just need a push in the right direction.

Thanks for any suggestions

Regards, Robert

---

### Post by P4man on 2010-05-09
looks like the remote is working just fine. I guess you are just not using an app that uses it. In rythmbox for instance, you will need to enable the lirc plugin, and then i suspect your remote will work fine with it.

---

### Post by bert682 on 2010-05-09
Tried that, enabled the plugin but to no avail.  Im guessing my conf file is all messed up somehow.

/etc/lirc/lircd.conf

```
#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the Windows Media Center Transceivers/Remotes (all) remote:
include "/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb"

#Configuration for the Microsoft Windows Media Center V2 (usb) : Direct TV Receiver transmitter:
include "/usr/share/lirc/extras/transmitters/directtv/general.conf"
```

It looks very plain to me, any ideas?

Thanks

---

### Post by P4man on 2010-05-09
Think all is ok so far, you're just missing the mapping. Look here:
[https://help.ubuntu.com/community/LIRC](https://help.ubuntu.com/community/LIRC)

---

