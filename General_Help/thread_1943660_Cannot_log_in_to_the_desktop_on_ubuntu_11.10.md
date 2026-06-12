---
title: "Cannot log in to the desktop on ubuntu 11.10?"
date: 2012-03-19
forum: General Help
---

### Post by jcyangzh on 2012-03-19
The problem is, I could log in under the terminal, i could ifup eth0,  i could do anything I want in the terminal, but if I use ctrl+alt+f7  goto the gnome login screen, after I input the correct password, the  system just send me back to same login screen again.


  I have created a new user, but it didn't work. 



  I have change all the files under ~/ to jichao:jichao(which is my username) with chown -hR jichao:jichao /home/jichao, but it didn't work too. 



  I searched the internet, somebody said I should see the logs under /var/log/gdm, but there is not a /var/log/gdm directory in my box.


  Here are the tail of files under /var/log/


    tail X.org.log
    [  3263.348] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
    [  3263.348] (**) Dell Dell USB Keyboard: always reports core events
    [  3263.348] (**) Dell Dell USB Keyboard: Device: "/dev/input/event5"
    [  3263.348] (--) Dell Dell USB Keyboard: Found keys
    [  3263.348] (II) Dell Dell USB Keyboard: Configuring as keyboard
    [  3263.348] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/input/input29/event5"
    [  3263.348] (II) XINPUT: Adding extended input device "Dell Dell USB Keyboard" (type: KEYBOARD)
    [  3263.348] (**) Option "xkb_rules" "evdev"
    [  3263.348] (**) Option "xkb_model" "pc105"
    [  3263.348] (**) Option "xkb_layout" "us"
    
    kern.log
    Mar 20 09:32:58 jichao-MS-730 kernel: [ 3182.701247] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/input/input27
    Mar 20 09:32:58 jichao-MS-730 kernel: [ 3182.701392] generic-usb 0003:413C:2003.0018: input,hidraw1: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.0-1.4/input0
    Mar 20 09:33:02 jichao-MS-730 kernel: [ 3186.642572] usb 2-1.3: new low speed USB device number 17 using ehci_hcd
    Mar 20 09:33:02 jichao-MS-730 kernel: [ 3186.741892] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/input/input28
    Mar 20 09:33:02 jichao-MS-730 kernel: [ 3186.742080] generic-usb 0003:045E:0047.0019: input,hidraw2: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.0-1.3/input0
    Mar 20 09:33:27 jichao-MS-730 kernel: [ 3212.473901] usb 2-1.3: USB disconnect, device number 17
    Mar 20 09:33:28 jichao-MS-730 kernel: [ 3212.702031] usb 2-1.4: USB disconnect, device number 16
    Mar 20 09:34:08 jichao-MS-730 kernel: [ 3253.022655] usb 2-1.4: new low speed USB device number 18 using ehci_hcd
    Mar 20 09:34:08 jichao-MS-730 kernel: [ 3253.124278] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/input/input29
    Mar 20 09:34:08 jichao-MS-730 kernel: [ 3253.124423] generic-usb 0003:413C:2003.001A: input,hidraw1: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.0-1.4/input0
    Mar 20 09:33:02 jichao-MS-730 kernel: [ 3186.741892] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/input/input28
    Mar 20 09:33:02 jichao-MS-730 kernel: [ 3186.742080] generic-usb 0003:045E:0047.0019: input,hidraw2: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.0-1.3/input0
    
    syslog
    Mar 20 09:33:02 jichao-MS-730 mtp-probe: bus: 2, device: 17 was not an MTP device
    Mar 20 09:33:27 jichao-MS-730 kernel: [ 3212.473901] usb 2-1.3: USB disconnect, device number 17
    Mar 20 09:33:28 jichao-MS-730 kernel: [ 3212.702031] usb 2-1.4: USB disconnect, device number 16
    Mar 20 09:34:08 jichao-MS-730 kernel: [ 3253.022655] usb 2-1.4: new low speed USB device number 18 using ehci_hcd
    Mar 20 09:34:08 jichao-MS-730 mtp-probe: checking bus 2, device 18: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4"
    Mar 20 09:34:08 jichao-MS-730 mtp-probe: bus: 2, device: 18 was not an MTP device
    Mar 20 09:34:08 jichao-MS-730 kernel: [ 3253.124278] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/input/input29
    Mar 20 09:34:08 jichao-MS-730 kernel: [ 3253.124423] generic-usb 0003:413C:2003.001A: input,hidraw1: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.0-1.4/input0
    
    auth.log
    Mar 20 09:18:52 jichao-MS-730 lightdm: pam_ck_connector(lightdm-autologin:session): nox11 mode, ignoring PAM_TTY :0
    Mar 20 09:18:53 jichao-MS-730 lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "jichao"
    Mar 20 09:18:53 jichao-MS-730 dbus[835]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.240" (uid=104 pid=6457 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.11" (uid=0 pid=1156 comm="/usr/sbin/console-kit-daemon --no-daemon ")
    Mar 20 09:19:38 jichao-MS-730 sudo:   jichao : TTY=tty6 ; PWD=/home ; USER=root ; COMMAND=/bin/chown -hR jichao:jichao jicha
    Mar 20 09:19:39 jichao-MS-730 sudo:   jichao : TTY=tty6 ; PWD=/home ; USER=root ; COMMAND=/bin/chown -hR jichao:jichao jichao
    Mar 20 09:20:10 jichao-MS-730 lightdm: pam_unix(lightdm-autologin:session): session closed for user lightdm
    Mar 20 09:20:11 jichao-MS-730 lightdm: pam_unix(lightdm-autologin:session): session opened for user lightdm by (uid=0)
    Mar 20 09:20:11 jichao-MS-730 lightdm: pam_ck_connector(lightdm-autologin:session): nox11 mode, ignoring PAM_TTY :0
    Mar 20 09:20:12 jichao-MS-730 lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "jichao"
    Mar 20 09:20:12 jichao-MS-730 dbus[835]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.247" (uid=104 pid=6572 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.11" (uid=0 pid=1156 comm="/usr/sbin/console-kit-daemon --no-daemon ")

Could you help me, Thanks.

---

