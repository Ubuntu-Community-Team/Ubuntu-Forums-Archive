---
title: "iPod Classic not connecting"
date: 2011-10-19
forum: General Help
---

### Post by HiImTye on 2011-10-19
I am unable to connect my iPod to Ubuntu and I am unsure what change caused it. I tried to reinstall Banshee to see if maybe it would locate the other half of my library this time (but it didn't so I uninstalled it again), also there were some updates which may have caused the issue but I believe that I have those covered. my iPod connects when the PC is powering up (displays 'connected'), however, once Ubuntu starts loading it ejects (actually, it completely ejects, normally if I simply 'eject' it will continue to charge, it is as if I have chosen 'safely remove'). once Ubuntu is loaded to the desktop if I try to connect it my iPod doesn't even turn on the backlight to acknowledge that it has connected to a power source.

here is my /var/log/apt/history.log for the last ten days:
```
Start-Date: 2011-10-09  07:57:04
Upgrade: flashplugin-installer:i386 (10.3.183.10ubuntu0.11.04.1, 11.0.1.152ubuntu0.11.04.1), flashplugin-nonfree:i386 (10.3.183.10ubuntu0.11.04.1, 11.0.1.152ubuntu0.11.04.1)
End-Date: 2011-10-09  08:00:04

Start-Date: 2011-10-11  20:49:13
Upgrade: python-desktopcouch-records:i386 (1.0.7-0ubuntu2, 1.0.7-0ubuntu2.1), desktopcouch:i386 (1.0.7-0ubuntu2, 1.0.7-0ubuntu2.1), python-desktopcouch-application:i386 (1.0.7-0ubuntu2, 1.0.7-0ubuntu2.1), desktopcouch-ubuntuone:i386 (1.0.7-0ubuntu2, 1.0.7-0ubuntu2.1)
End-Date: 2011-10-11  20:49:28

Start-Date: 2011-10-13  07:38:55
Upgrade: libpq5:i386 (8.4.8-0ubuntu0.11.04, 8.4.9-0ubuntu0.11.04)
End-Date: 2011-10-13  07:39:01

Start-Date: 2011-10-14  23:15:56
Upgrade: faenza-icon-theme:i386 (1.0-ubuntu1, 1.1)
End-Date: 2011-10-14  23:16:19

Start-Date: 2011-10-17  09:03:24
Upgrade: libimobiledevice2:i386 (1.1.0-3, 1.1.0-3ubuntu1)
End-Date: 2011-10-17  09:03:31

Start-Date: 2011-10-18  23:33:28
Upgrade: ubuntuone-client:i386 (1.6.2-0ubuntu1, 1.6.2-0ubuntu2), libkrb5-3:i386 (1.8.3+dfsg-5ubuntu2.1, 1.8.3+dfsg-5ubuntu2.2), unity:i386 (3.8.16-0ubuntu1~natty2, 3.8.16-0ubuntu1~natty3), libkrb5support0:i386 (1.8.3+dfsg-5ubuntu2.1, 1.8.3+dfsg-5ubuntu2.2), xserver-common:i386 (1.10.1-1ubuntu1.2, 1.10.1-1ubuntu1.3), ubuntuone-client-gnome:i386 (1.6.2-0ubuntu1, 1.6.2-0ubuntu2), xserver-xorg-core:i386 (1.10.1-1ubuntu1.2, 1.10.1-1ubuntu1.3), libk5crypto3:i386 (1.8.3+dfsg-5ubuntu2.1, 1.8.3+dfsg-5ubuntu2.2), libsyncdaemon-1.0-1:i386 (1.6.2-0ubuntu1, 1.6.2-0ubuntu2), unity-common:i386 (3.8.16-0ubuntu1~natty2, 3.8.16-0ubuntu1~natty3), libdvdread4:i386 (4.1.3-10ubuntu3, 4.1.3-10ubuntu3.1), python-ubuntuone-client:i386 (1.6.2-0ubuntu1, 1.6.2-0ubuntu2), libgssapi-krb5-2:i386 (1.8.3+dfsg-5ubuntu2.1, 1.8.3+dfsg-5ubuntu2.2), xserver-xorg-video-intel:i386 (2.14.0-4ubuntu7.1, 2.14.0-4ubuntu7.2)
End-Date: 2011-10-18  23:34:15

Start-Date: 2011-10-19  08:30:13
Upgrade: update-manager:i386 (0.150.3, 0.150.4), update-manager-core:i386 (0.150.3, 0.150.4)
End-Date: 2011-10-19  08:30:34

Start-Date: 2011-10-19  11:16:07
Commandline: apt-get install banshee
Install: banshee:i386 (2.0.0-2ubuntu2), banshee-extension-soundmenu:i386 (2.0.0-2ubuntu2, automatic), banshee-extension-ubuntuonemusicstore:i386 (2.0.0-2ubuntu2, automatic)
End-Date: 2011-10-19  11:16:32

Start-Date: 2011-10-19  14:49:28
Install: soundconverter:i386 (1.4.4-2)
End-Date: 2011-10-19  14:49:53

Start-Date: 2011-10-19  15:03:59
Commandline: apt-get remove banshee
Remove: banshee:i386 (2.0.0-2ubuntu2), banshee-extension-soundmenu:i386 (2.0.0-2ubuntu2), banshee-extension-ubuntuonemusicstore:i386 (2.0.0-2ubuntu2)
End-Date: 2011-10-19  15:04:15

Start-Date: 2011-10-19  15:15:20
Commandline: apt-get remove libgpod-common libgpod4
Remove: libgpod4:i386 (0.8.0-2ubuntu0.1), libgpod-common:i386 (0.8.0-2ubuntu0.1), rhythmbox-plugins:i386 (0.13.3-0ubuntu6)
End-Date: 2011-10-19  15:15:27

Start-Date: 2011-10-19  15:15:47
Commandline: apt-get install libgpod-common libgpod4 rhythmbox-plugins
Install: libgpod4:i386 (0.8.0-2ubuntu0.1), libgpod-common:i386 (0.8.0-2ubuntu0.1), rhythmbox-plugins:i386 (0.13.3-0ubuntu6)
End-Date: 2011-10-19  15:15:51

Start-Date: 2011-10-19  15:15:58
Commandline: apt-get autoremove
Remove: tsocks:i386 (1.8beta5-9.1), socat:i386 (1.7.1.3-1)
End-Date: 2011-10-19  15:16:02

Start-Date: 2011-10-19  15:30:50
Commandline: apt-get install banshee
Install: banshee:i386 (2.0.0-2ubuntu2), banshee-extension-soundmenu:i386 (2.0.0-2ubuntu2, automatic), banshee-extension-ubuntuonemusicstore:i386 (2.0.0-2ubuntu2, automatic)
End-Date: 2011-10-19  15:31:10

Start-Date: 2011-10-19  15:32:19
Commandline: apt-get remove banshee
Remove: banshee:i386 (2.0.0-2ubuntu2), banshee-extension-soundmenu:i386 (2.0.0-2ubuntu2), banshee-extension-ubuntuonemusicstore:i386 (2.0.0-2ubuntu2)
End-Date: 2011-10-19  15:32:27

Start-Date: 2011-10-19  15:33:02
Commandline: apt-get purge libgpod-common libgpod4
Purge: libgpod4:i386 (0.8.0-2ubuntu0.1), libgpod-common:i386 (0.8.0-2ubuntu0.1), rhythmbox-plugins:i386 (0.13.3-0ubuntu6)
End-Date: 2011-10-19  15:33:06

Start-Date: 2011-10-19  15:33:14
Commandline: apt-get install libgpod-common libgpod4
Install: libgpod4:i386 (0.8.0-2ubuntu0.1), libgpod-common:i386 (0.8.0-2ubuntu0.1)
End-Date: 2011-10-19  15:33:17

Start-Date: 2011-10-19  15:33:43
Commandline: apt-get install rhythmbox-plugins
Install: rhythmbox-plugins:i386 (0.13.3-0ubuntu6)
End-Date: 2011-10-19  15:33:45

Start-Date: 2011-10-19  17:07:32
Commandline: /usr/sbin/synaptic
Downgrade: libimobiledevice2:i386 (1.1.0-3ubuntu1, 1.1.0-3)
End-Date: 2011-10-19  17:07:38

Start-Date: 2011-10-19  17:11:26
Upgrade: libimobiledevice2:i386 (1.1.0-3, 1.1.0-3ubuntu1)
End-Date: 2011-10-19  17:11:33

Start-Date: 2011-10-19  17:21:35
Commandline: /usr/sbin/synaptic
End-Date: 2011-10-19  17:21:45

```note: I also tried reinstalling usbmux/libusbmux in synaptic and rebooting to no avail

any help would be appreciated

edit: I attempted to connect my gf's nano that connected with no issue earlier this week also and it also behaves the exact same way

---

### Post by Meelad on 2011-10-19
Try:

```
sudo apt-get install ifuse libimobiledevice-utils
idevicepair unpair && idevicepair pair

```
This works for 11.10.. Not sure about 11.04..

---

### Post by HiImTye on 2011-10-19
```
~$ idevicepair unpair && idevicepair pair                                                                                                                                                                                                     
usbmuxd_get_device_list: error opening socket!                                                                                                                                                                                                      
No device found, is it plugged in?
```

I think that's for touch based devices isnt it?

---

### Post by Meelad on 2011-10-19
> **HiImTye said:**
> ```
~$ idevicepair unpair && idevicepair pair                                                                                                                                                                                                     
usbmuxd_get_device_list: error opening socket!                                                                                                                                                                                                      
No device found, is it plugged in?
```I think that's for touch based devices isnt it?

Yeah, thought yours was touch.. Didn't pay attention to the title, my mistake..

---

### Post by HiImTye on 2011-10-19
no worries, thanks for the help anyway

---

### Post by HiImTye on 2011-10-20
odd, I woke up this morning and it was connected yet it wasn't when I went to bed last night. I'm unsure what caused it to stop working let alone what caused it to start again.

---

