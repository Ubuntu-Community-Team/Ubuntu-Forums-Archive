---
title: "wifi disconnects when I plug webcam in"
date: 2010-10-20
forum: General Help
---

### Post by geoffy0404 on 2010-10-20
Hello this is my very first post for ubuntu, I can usually google search a problem that I have with ubuntu and find a solution but I could not find one, now straight to the point.


I am on a toshiba laptop with a wireless internet connection, I have recently purchased a logitech pro 9000 webcam , I plan on using it for skype. So the wifi is working fine, I plug in the usb webcam and all of the sudden I just lose connection and my keyring doesnt even remember the wep key for my wifi. 

I am amateur with linux based system but I have taken a operation system class so i know some stuff and can follow instructions quite well. thank you.

---

### Post by Jebtrix on 2010-10-20
Try **dmesg | grep -i uvcvideo**

Post the results if any.

---

### Post by geoffy0404 on 2010-10-21
geoffrey@geoffrey-laptop:~$ dmesg | grep -i uvcvideo
[   60.828711] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0809)
[   60.864602] usbcore: registered new interface driver uvcvideo


thats my results it stll doesnt work after I used that I also tried 

[http://www.quickcamteam.net/documentation/how-to/how-to-install-the-webcam-tools](http://www.quickcamteam.net/documentation/how-to/how-to-install-the-webcam-tools)

which doesnt seem to help

---

### Post by Jebtrix on 2010-10-23
Try setting the quirks parameter to 2 before plugging your webcam 
Driver not already loaded do:
```
sudo modprobe uvcvideo quirks=2
```
Driver is already loaded do:
```
sudo echo 2 > /sys/modules/uvcvideo/parameters/quirks
```

---

### Post by geoffy0404 on 2010-10-25
here are the results for the second thing you had me try.

geoffrey@geoffrey-laptop:~$ sudo modprobe uvcvideo quirks=2
[sudo] password for geoffrey:
geoffrey@geoffrey-laptop:~$ sudo echo 2 > /sys/modules/uvcvideo/parameters/quirks
bash: /sys/modules/uvcvideo/parameters/quirks: No such file or directory
geoffrey@geoffrey-laptop:~$ 


that was what i did in the terminal, on the same session i plugged the usb cam in and it disconnected me, I unplugged it and restart the computer and plugged it back in on a fresh session, it still disconnected me from the wifi.     

so basically no solution.

also i forgot to mention the version of Ubuntu i am running is:   10.04 LTS

also the laptop i am has no internal built in webcam, so i was maybe thinking ubuntu didnt see a reason to install the proper configuration since there was no webcam, would that be any problem? and thanks for taking your time and helping me even though there is yet to be a solution.:)

---

### Post by Dooglus on 2011-01-31
> **geoffy0404 said:**
> $ sudo echo 2 > /sys/modules/uvcvideo/parameters/quirks
bash: /sys/modules/uvcvideo/parameters/quirks: No such file or directory


I think he meant
```

sudo echo 2 > /sys/module/uvcvideo/parameters/quirks

```

note 'module' is singular, not plural.

I have the same problem as you.  I'm on a toshiba laptop, with a logitech quickcam pro 9000.  It has a built in cam, which is very low quality, but sometimes works for a while before killing the network connection, but as soon as I plug in the USB logitech cam, the wireless internet connection dies, and I can't find a way to get it up again without rebooting.

Here's what appeared in the syslog as I went through breaking my network connection...

First I removed the uvcvideo device that was automatically loaded, presumably because of the built-in webcam:

```

# rmmod uvcvideo
Jan 30 22:29:07 localhost kernel: [10600.350681] usbcore: deregistering interface driver uvcvideo

```

Then I reloaded the uvcvideo module with quirks=2:

```

# modprobe with quirks=2
Jan 30 22:29:19 localhost kernel: [10612.740728] uvcvideo: Found UVC 1.00 device Chicony USB 2.0 Camera (04f2:b008)
Jan 30 22:29:19 localhost kernel: [10612.740738] uvcvideo: Forcing device quirks to 0x2 by module parameter for testing purpose.
Jan 30 22:29:19 localhost kernel: [10612.740745] uvcvideo: Please report required quirks to the linux-uvc-devel mailing list.
Jan 30 22:29:19 localhost kernel: [10612.744563] input: Chicony USB 2.0 Camera as /devices/pci0000:00/0000:00:13.5/usb1/1-8/1-8:1.0/input/input10
Jan 30 22:29:19 localhost kernel: [10612.744779] usbcore: registered new interface driver uvcvideo
Jan 30 22:29:19 localhost kernel: [10612.744786] USB Video Class driver (v1.0.0)

```

Then I wanted to be sure of using a working USB port, so I unplugged the USB mouse I was using:

```

# unplug mouse
Jan 30 22:30:00 localhost kernel: [10653.849120] usb 2-1: USB disconnect, address 3
Jan 30 22:30:01 localhost CRON[6065]: (CRON) error (grandchild #6069 failed with exit status 1)

```

then I plugged in the logitech quickcam pro 9000:

```

# plug in webcam
Jan 30 22:30:50 localhost kernel: [10703.076131] usb 1-1: new high speed USB device using ehci_hcd and address 6
Jan 30 22:30:50 localhost kernel: [10703.338537] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0990)
Jan 30 22:30:50 localhost kernel: [10703.338548] uvcvideo: Forcing device quirks to 0x2 by module parameter for testing purpose.
Jan 30 22:30:50 localhost kernel: [10703.338555] uvcvideo: Please report required quirks to the linux-uvc-devel mailing list.
Jan 30 22:30:50 localhost kernel: [10703.371273] input: UVC Camera (046d:0990) as /devices/pci0000:00/0000:00:13.5/usb1/1-1/1-1:1.0/input/input11
Jan 30 22:30:50 localhost kernel: [10703.637236] ehci_hcd 0000:00:13.5: force halt; handshake f8412424 00004000 00000000 -> -110
Jan 30 22:30:50 localhost kernel: [10703.644083] 6:3:1: cannot get freq at ep 0x86
Jan 30 22:30:50 localhost kernel: [10703.645698] usbcore: registered new interface driver snd-usb-audio
Jan 30 22:30:51 localhost kernel: [10703.890613] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.890651] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.890688] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.890936] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.891672] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.892264] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.892294] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.892513] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.892770] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.893486] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.894154] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.894210] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.894340] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.894793] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.895614] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.897021] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.897087] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.897231] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.897567] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.898381] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost pulseaudio[5388]: module-alsa-card.c: Failed to find a working profile.
Jan 30 22:30:51 localhost pulseaudio[5388]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="usb-046d_0990_2CA88DD9-02-Q9000" card_name="alsa_card.usb-046d_0990_2CA88DD9-02-Q9000" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Jan 30 22:30:51 localhost kernel: [10703.918907] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.918942] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.918978] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.919218] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.919936] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.920814] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.920848] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.920883] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.921120] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.921851] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.922535] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.922591] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.922721] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.923045] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.923860] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.925358] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.925419] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.925560] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.925909] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.926859] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost pulseaudio[5388]: module-alsa-card.c: Failed to find a working profile.
Jan 30 22:30:51 localhost pulseaudio[5388]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="usb-046d_0990_2CA88DD9-02-Q9000" card_name="alsa_card.usb-046d_0990_2CA88DD9-02-Q9000" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Jan 30 22:30:51 localhost kernel: [10703.949392] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.949428] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.949466] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.949805] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.950606] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.951237] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.951269] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.951306] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.951564] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.952769] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.953452] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.953509] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.953639] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.953953] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.954752] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.955717] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.955775] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.955916] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.956727] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.957568] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost pulseaudio[5388]: module-alsa-card.c: Failed to find a working profile.
Jan 30 22:30:51 localhost pulseaudio[5388]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="usb-046d_0990_2CA88DD9-02-Q9000" card_name="alsa_card.usb-046d_0990_2CA88DD9-02-Q9000" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Jan 30 22:30:51 localhost kernel: [10703.977486] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.977529] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.977568] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.977885] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.978805] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.979315] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.979346] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.979383] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.979617] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.980941] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.981658] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.981716] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.981847] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.982155] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.982960] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.983932] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.983994] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.984942] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.985375] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10703.986739] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost pulseaudio[5388]: module-alsa-card.c: Failed to find a working profile.
Jan 30 22:30:51 localhost pulseaudio[5388]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="usb-046d_0990_2CA88DD9-02-Q9000" card_name="alsa_card.usb-046d_0990_2CA88DD9-02-Q9000" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Jan 30 22:30:51 localhost kernel: [10704.010455] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10704.010496] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10704.010535] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10704.010847] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10704.012755] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10704.013507] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10704.013546] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10704.013583] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10704.013901] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10704.014877] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10704.015619] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10704.015676] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10704.015808] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10704.016789] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10704.017671] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10704.018856] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10704.018927] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10704.019068] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10704.019394] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost pulseaudio[5388]: module-alsa-card.c: Failed to find a working profile.
Jan 30 22:30:51 localhost kernel: [10704.020685] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost pulseaudio[5388]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="usb-046d_0990_2CA88DD9-02-Q9000" card_name="alsa_card.usb-046d_0990_2CA88DD9-02-Q9000" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Jan 30 22:30:51 localhost kernel: [10704.042304] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10704.042345] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10704.042386] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10704.042636] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10704.043762] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10704.044769] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10704.044807] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10704.044846] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10704.045085] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10704.045798] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10704.046459] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10704.046518] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10704.046652] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10704.046964] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10704.047764] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10704.049448] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10704.049515] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10704.049658] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10704.049994] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost kernel: [10704.050821] 6:3:1: usb_set_interface failed
Jan 30 22:30:51 localhost pulseaudio[5388]: module-alsa-card.c: Failed to find a working profile.
Jan 30 22:30:51 localhost pulseaudio[5388]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="usb-046d_0990_2CA88DD9-02-Q9000" card_name="alsa_card.usb-046d_0990_2CA88DD9-02-Q9000" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Jan 30 22:30:51 localhost pulseaudio[5388]: module-udev-detect.c: Tried to configure /devices/pci0000:00/0000:00:13.5/usb1/1-1/1-1:1.2/sound/card1 (alsa_card.usb-046d_0990_2CA88DD9-02-Q9000) more often than 5 times in 10s
Jan 30 22:30:53 localhost kernel: [10705.992194] uvcvideo: Failed to set UVC commit control : -108 (exp. 26).
Jan 30 22:30:53 localhost kernel: [10705.992214] uvcvideo 1-8:1.1: resume error -5
Jan 30 22:30:54 localhost kernel: [10706.992139] rtl8187: wireless radio switch turned off
Jan 30 22:30:54 localhost kernel: [10706.992341] wlan1: deauthenticating from 00:13:46:07:20:4c by local choice (reason=3)
Jan 30 22:30:54 localhost kernel: [10707.056152] cfg80211: All devices are disconnected, going to restore regulatory settings
Jan 30 22:30:54 localhost kernel: [10707.056171] cfg80211: Restoring regulatory settings
Jan 30 22:30:54 localhost kernel: [10707.056185] cfg80211: Calling CRDA to update world regulatory domain
Jan 30 22:30:54 localhost wpa_supplicant[813]: CTRL-EVENT-DISCONNECTED bssid=00:13:46:07:20:4c reason=0
Jan 30 22:30:54 localhost dhclient: receive_packet failed on wlan1: Network is down
Jan 30 22:30:54 localhost NetworkManager[683]: <info> WiFi now disabled by radio killswitch
Jan 30 22:30:54 localhost kernel: [10707.501090] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
Jan 30 22:30:54 localhost NetworkManager[683]: <info> (wlan1): device state change: 8 -> 2 (reason 0)
Jan 30 22:30:54 localhost NetworkManager[683]: <info> (wlan1): deactivating device (reason: 0).
Jan 30 22:30:54 localhost wpa_supplicant[813]: Failed to initiate AP scan.
Jan 30 22:30:54 localhost avahi-daemon[686]: Interface wlan1.IPv6 no longer relevant for mDNS.
Jan 30 22:30:54 localhost avahi-daemon[686]: Leaving mDNS multicast group on interface wlan1.IPv6 with address fe80::216:44ff:fe69:89e7.
Jan 30 22:30:54 localhost avahi-daemon[686]: Interface wlan1.IPv4 no longer relevant for mDNS.
Jan 30 22:30:54 localhost avahi-daemon[686]: Leaving mDNS multicast group on interface wlan1.IPv4 with address 192.168.0.187.
Jan 30 22:30:54 localhost avahi-daemon[686]: Withdrawing address record for fe80::216:44ff:fe69:89e7 on wlan1.
Jan 30 22:30:54 localhost kernel: [10707.778286] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:30:54 localhost kernel: [10707.778300] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:30:54 localhost kernel: [10707.778309] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:30:54 localhost kernel: [10707.778318] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:30:54 localhost kernel: [10707.778325] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:30:54 localhost kernel: [10707.778333] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:30:54 localhost kernel: [10707.778340] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:30:54 localhost kernel: [10707.778349] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:30:54 localhost kernel: [10707.778356] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:30:54 localhost kernel: [10707.778364] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:30:54 localhost kernel: [10707.778371] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:30:54 localhost kernel: [10707.778380] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:30:54 localhost kernel: [10707.778387] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:30:54 localhost kernel: [10707.778395] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:30:54 localhost kernel: [10707.778403] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:30:54 localhost kernel: [10707.778411] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:30:54 localhost kernel: [10707.778418] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:30:54 localhost kernel: [10707.778427] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:30:54 localhost kernel: [10707.778434] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:30:54 localhost kernel: [10707.778442] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:30:54 localhost kernel: [10707.778449] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:30:54 localhost kernel: [10707.778457] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:30:54 localhost kernel: [10707.778465] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:30:54 localhost kernel: [10707.778473] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:30:54 localhost kernel: [10707.778480] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:30:54 localhost kernel: [10707.778489] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:30:54 localhost kernel: [10707.778496] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:30:54 localhost kernel: [10707.778504] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:30:54 localhost kernel: [10707.778514] cfg80211: World regulatory domain updated:
Jan 30 22:30:54 localhost kernel: [10707.778519] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jan 30 22:30:54 localhost kernel: [10707.778528] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan 30 22:30:54 localhost kernel: [10707.778536] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan 30 22:30:54 localhost kernel: [10707.778544] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan 30 22:30:54 localhost kernel: [10707.778552] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan 30 22:30:54 localhost kernel: [10707.778560] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan 30 22:30:54 localhost avahi-daemon[686]: Withdrawing address record for 192.168.0.187 on wlan1.
Jan 30 22:30:54 localhost avahi-daemon[686]: Joining mDNS multicast group on interface wlan1.IPv4 with address 192.168.0.187.
Jan 30 22:30:54 localhost avahi-daemon[686]: New relevant interface wlan1.IPv4 for mDNS.
Jan 30 22:30:54 localhost avahi-daemon[686]: Registering new address record for 192.168.0.187 on wlan1.IPv4.
Jan 30 22:30:55 localhost NetworkManager[683]: <info> (wlan1): canceled DHCP transaction, DHCP client pid 1365
Jan 30 22:30:55 localhost avahi-daemon[686]: Withdrawing address record for 192.168.0.187 on wlan1.
Jan 30 22:30:55 localhost avahi-daemon[686]: Leaving mDNS multicast group on interface wlan1.IPv4 with address 192.168.0.187.
Jan 30 22:30:55 localhost avahi-daemon[686]: Interface wlan1.IPv4 no longer relevant for mDNS.
Jan 30 22:32:43 localhost kernel: [10816.853606] usbcore: deregistering interface driver uvcvideo
Jan 30 22:32:53 localhost kernel: [10826.394903] usbcore: deregistering interface driver rtl8187
Jan 30 22:32:53 localhost avahi-daemon[686]: Withdrawing workstation service for wlan1.
Jan 30 22:32:53 localhost kernel: [10826.460329] hub 1-0:1.0: cannot reset port 6 (err = -108)
Jan 30 22:32:53 localhost kernel: [10826.460344] hub 1-0:1.0: cannot reset port 6 (err = -108)
Jan 30 22:32:53 localhost kernel: [10826.460353] hub 1-0:1.0: cannot reset port 6 (err = -108)
Jan 30 22:32:53 localhost kernel: [10826.460361] hub 1-0:1.0: cannot reset port 6 (err = -108)
Jan 30 22:32:53 localhost kernel: [10826.460369] hub 1-0:1.0: cannot reset port 6 (err = -108)
Jan 30 22:32:53 localhost kernel: [10826.460375] hub 1-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
Jan 30 22:32:53 localhost kernel: [10826.460384] hub 1-0:1.0: cannot disable port 6 (err = -108)
Jan 30 22:32:53 localhost kernel: [10826.460393] hub 1-0:1.0: cannot reset port 6 (err = -108)
Jan 30 22:32:53 localhost kernel: [10826.460401] hub 1-0:1.0: cannot reset port 6 (err = -108)
Jan 30 22:32:53 localhost kernel: [10826.460408] hub 1-0:1.0: cannot reset port 6 (err = -108)
Jan 30 22:32:53 localhost kernel: [10826.460416] hub 1-0:1.0: cannot reset port 6 (err = -108)
Jan 30 22:32:53 localhost kernel: [10826.460423] hub 1-0:1.0: cannot reset port 6 (err = -108)
Jan 30 22:32:53 localhost kernel: [10826.460429] hub 1-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
Jan 30 22:32:53 localhost kernel: [10826.460438] hub 1-0:1.0: cannot disable port 6 (err = -108)
Jan 30 22:32:53 localhost kernel: [10826.460446] hub 1-0:1.0: cannot reset port 6 (err = -108)
Jan 30 22:32:53 localhost kernel: [10826.460454] hub 1-0:1.0: cannot reset port 6 (err = -108)
Jan 30 22:32:53 localhost kernel: [10826.461143] hub 1-0:1.0: cannot reset port 6 (err = -108)
Jan 30 22:32:53 localhost kernel: [10826.461154] hub 1-0:1.0: cannot reset port 6 (err = -108)
Jan 30 22:32:53 localhost kernel: [10826.461162] hub 1-0:1.0: cannot reset port 6 (err = -108)
Jan 30 22:32:53 localhost kernel: [10826.461169] hub 1-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
Jan 30 22:32:53 localhost kernel: [10826.461179] hub 1-0:1.0: cannot disable port 6 (err = -108)
Jan 30 22:32:53 localhost kernel: [10826.461191] hub 1-0:1.0: cannot reset port 6 (err = -108)
Jan 30 22:32:53 localhost kernel: [10826.461199] hub 1-0:1.0: cannot reset port 6 (err = -108)
Jan 30 22:32:53 localhost kernel: [10826.461207] hub 1-0:1.0: cannot reset port 6 (err = -108)
Jan 30 22:32:53 localhost kernel: [10826.461214] hub 1-0:1.0: cannot reset port 6 (err = -108)
Jan 30 22:32:53 localhost kernel: [10826.461222] hub 1-0:1.0: cannot reset port 6 (err = -108)
Jan 30 22:32:53 localhost kernel: [10826.461228] hub 1-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
Jan 30 22:32:53 localhost kernel: [10826.461237] hub 1-0:1.0: cannot disable port 6 (err = -108)
Jan 30 22:32:53 localhost kernel: [10826.461246] hub 1-0:1.0: cannot disable port 6 (err = -108)
Jan 30 22:32:53 localhost kernel: [10826.461289] hub 1-0:1.0: hub_port_status failed (err = -108)
Jan 30 22:32:53 localhost NetworkManager[683]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:13.5/usb1/1-6/1-6:1.0/net/wlan1, iface: wlan1)
Jan 30 22:32:53 localhost NetworkManager[683]: <info> (wlan1): now unmanaged
Jan 30 22:32:53 localhost NetworkManager[683]: <info> (wlan1): device state change: 2 -> 1 (reason 36)
Jan 30 22:32:53 localhost NetworkManager[683]: <info> (wlan1): cleaning up...
Jan 30 22:32:53 localhost NetworkManager[683]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jan 30 22:32:53 localhost NetworkManager[683]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jan 30 22:32:53 localhost NetworkManager[683]: <info> WiFi now enabled by radio killswitch
Jan 30 22:32:53 localhost NetworkManager[683]: <info> radio killswitch /sys/devices/pci0000:00/0000:00:13.5/usb1/1-6/1-6:1.0/ieee80211/phy0/rfkill0 disappeared
Jan 30 22:33:09 localhost kernel: [10842.460831] rtl8187: Invalid hwaddr! Using randomly generated MAC address
Jan 30 22:33:09 localhost kernel: [10842.468621] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:33:09 localhost kernel: [10842.468632] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:33:09 localhost kernel: [10842.468640] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:33:09 localhost kernel: [10842.468649] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:33:09 localhost kernel: [10842.468657] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:33:09 localhost kernel: [10842.468665] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:33:09 localhost kernel: [10842.468673] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:33:09 localhost kernel: [10842.468681] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:33:09 localhost kernel: [10842.468689] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:33:09 localhost kernel: [10842.468698] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:33:09 localhost kernel: [10842.468705] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:33:09 localhost kernel: [10842.468714] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:33:09 localhost kernel: [10842.468721] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:33:09 localhost kernel: [10842.468730] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:33:09 localhost kernel: [10842.468737] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:33:09 localhost kernel: [10842.468746] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:33:09 localhost kernel: [10842.468753] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:33:09 localhost kernel: [10842.468762] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:33:09 localhost kernel: [10842.468769] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:33:09 localhost kernel: [10842.468778] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:33:09 localhost kernel: [10842.468785] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:33:09 localhost kernel: [10842.468794] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:33:09 localhost kernel: [10842.468802] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:33:09 localhost kernel: [10842.468810] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:33:09 localhost kernel: [10842.468818] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:33:09 localhost kernel: [10842.468827] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:33:09 localhost kernel: [10842.468834] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:33:09 localhost kernel: [10842.468843] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:33:09 localhost kernel: [10842.469173] ieee80211 phy1: Selected rate control algorithm 'minstrel_ht'
Jan 30 22:33:09 localhost kernel: [10842.475637] ieee80211 phy1: hwaddr 92:4a:e5:62:10:b0, RTL8187BvB V1 + rtl8225z2, rfkill mask 2
Jan 30 22:33:09 localhost NetworkManager[683]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/pci0000:00/0000:00:13.5/usb1/1-6/1-6:1.0/ieee80211/phy1/rfkill1) (driver <unknown>)
Jan 30 22:33:09 localhost kernel: [10842.476848] rtl8187: Customer ID is 0x00
Jan 30 22:33:09 localhost kernel: [10842.477393] Registered led device: rtl8187-phy1::radio
Jan 30 22:33:09 localhost kernel: [10842.483353] Registered led device: rtl8187-phy1::tx
Jan 30 22:33:09 localhost kernel: [10842.483485] Registered led device: rtl8187-phy1::rx
Jan 30 22:33:09 localhost kernel: [10842.483499] rtl8187: wireless switch is off
Jan 30 22:33:09 localhost NetworkManager[683]: <info> WiFi now disabled by radio killswitch
Jan 30 22:33:09 localhost kernel: [10842.484697] usbcore: registered new interface driver rtl8187
Jan 30 22:33:09 localhost NetworkManager[683]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Jan 30 22:33:09 localhost NetworkManager[683]: <info> (wlan0): new 802.11 WiFi device (driver: 'rtl8187' ifindex: 4)
Jan 30 22:33:09 localhost NetworkManager[683]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/2
Jan 30 22:33:09 localhost NetworkManager[683]: <info> (wlan0): now managed
Jan 30 22:33:09 localhost NetworkManager[683]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Jan 30 22:33:09 localhost NetworkManager[683]: <info> (wlan0): bringing up device.
Jan 30 22:33:09 localhost NetworkManager[683]: <info> (wlan0): deactivating device (reason: 2).
Jan 30 22:33:09 localhost NetworkManager[683]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:13.5/usb1/1-6/1-6:1.0/net/wlan0, iface: wlan0)
Jan 30 22:33:09 localhost NetworkManager[683]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:13.5/usb1/1-6/1-6:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jan 30 22:33:18 localhost ntpd[1689]: Deleting interface #4 wlan1, fe80::216:44ff:fe69:89e7#123, interface stats: received=0, sent=0, dropped=0, active_time=10801 secs
Jan 30 22:33:18 localhost ntpd[1689]: Deleting interface #3 wlan1, 192.168.0.187#123, interface stats: received=65, sent=66, dropped=0, active_time=10801 secs
Jan 30 22:33:18 localhost ntpd[1689]: 132.246.11.229 interface 192.168.0.187 -> (null)
Jan 30 22:33:36 localhost kernel: [10869.517567] usbcore: deregistering interface driver rtl8187
Jan 30 22:33:36 localhost avahi-daemon[686]: Withdrawing workstation service for wlan0.
Jan 30 22:33:36 localhost NetworkManager[683]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:13.5/usb1/1-6/1-6:1.0/net/wlan0, iface: wlan0)
Jan 30 22:33:36 localhost NetworkManager[683]: <info> (wlan0): now unmanaged
Jan 30 22:33:36 localhost NetworkManager[683]: <info> (wlan0): device state change: 2 -> 1 (reason 36)
Jan 30 22:33:36 localhost NetworkManager[683]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jan 30 22:33:36 localhost NetworkManager[683]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jan 30 22:33:36 localhost NetworkManager[683]: <info> radio killswitch /sys/devices/pci0000:00/0000:00:13.5/usb1/1-6/1-6:1.0/ieee80211/phy1/rfkill1 disappeared
Jan 30 22:33:36 localhost NetworkManager[683]: <info> WiFi now enabled by radio killswitch
Jan 30 22:33:37 localhost kernel: [10870.678538] rtl8187: Invalid hwaddr! Using randomly generated MAC address
Jan 30 22:33:37 localhost kernel: [10870.688285] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:33:37 localhost kernel: [10870.688300] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:33:37 localhost kernel: [10870.688308] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:33:37 localhost kernel: [10870.688333] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:33:37 localhost kernel: [10870.688340] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:33:37 localhost kernel: [10870.688349] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:33:37 localhost kernel: [10870.688357] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:33:37 localhost kernel: [10870.688366] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:33:37 localhost kernel: [10870.688373] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:33:37 localhost kernel: [10870.688382] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:33:37 localhost kernel: [10870.688389] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:33:37 localhost kernel: [10870.688398] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:33:37 localhost kernel: [10870.688405] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:33:37 localhost kernel: [10870.688414] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:33:37 localhost kernel: [10870.688421] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:33:37 localhost kernel: [10870.688430] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:33:37 localhost kernel: [10870.688437] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:33:37 localhost kernel: [10870.688446] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:33:37 localhost kernel: [10870.688453] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:33:37 localhost kernel: [10870.688462] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:33:37 localhost kernel: [10870.688469] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:33:37 localhost kernel: [10870.688478] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:33:37 localhost kernel: [10870.688485] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:33:37 localhost kernel: [10870.688494] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:33:37 localhost kernel: [10870.688501] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:33:37 localhost kernel: [10870.688510] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:33:37 localhost kernel: [10870.688518] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
Jan 30 22:33:37 localhost kernel: [10870.688527] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
Jan 30 22:33:37 localhost kernel: [10870.688890] ieee80211 phy2: Selected rate control algorithm 'minstrel_ht'
Jan 30 22:33:37 localhost kernel: [10870.691396] ieee80211 phy2: hwaddr 3e:bd:47:82:b9:10, RTL8187BvB V1 + rtl8225z2, rfkill mask 2
Jan 30 22:33:37 localhost kernel: [10870.692321] rtl8187: Customer ID is 0x00
Jan 30 22:33:37 localhost kernel: [10870.692494] Registered led device: rtl8187-phy2::radio
Jan 30 22:33:37 localhost kernel: [10870.692585] Registered led device: rtl8187-phy2::tx
Jan 30 22:33:37 localhost kernel: [10870.692651] Registered led device: rtl8187-phy2::rx
Jan 30 22:33:37 localhost kernel: [10870.692660] rtl8187: wireless switch is off
Jan 30 22:33:37 localhost kernel: [10870.692748] usbcore: registered new interface driver rtl8187
Jan 30 22:33:37 localhost NetworkManager[683]: <info> found WiFi radio killswitch rfkill2 (at /sys/devices/pci0000:00/0000:00:13.5/usb1/1-6/1-6:1.0/ieee80211/phy2/rfkill2) (driver <unknown>)
Jan 30 22:33:37 localhost NetworkManager[683]: <info> WiFi now disabled by radio killswitch
Jan 30 22:33:37 localhost NetworkManager[683]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:13.5/usb1/1-6/1-6:1.0/net/wlan0, iface: wlan0)
Jan 30 22:33:37 localhost NetworkManager[683]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:13.5/usb1/1-6/1-6:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jan 30 22:33:37 localhost NetworkManager[683]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Jan 30 22:33:37 localhost NetworkManager[683]: <info> (wlan0): new 802.11 WiFi device (driver: 'rtl8187' ifindex: 5)
Jan 30 22:33:37 localhost NetworkManager[683]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/3
Jan 30 22:33:37 localhost NetworkManager[683]: <info> (wlan0): now managed
Jan 30 22:33:37 localhost NetworkManager[683]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Jan 30 22:33:37 localhost NetworkManager[683]: <info> (wlan0): bringing up device.
Jan 30 22:33:37 localhost NetworkManager[683]: <info> (wlan0): deactivating device (reason: 2).

```

Help?

Thanks?

Chris.

---

