---
title: "lirc 0609:031d SMK Manufacturing, Inc. eHome Infrared Receiver problems"
date: 2011-09-17
forum: General Help
---

### Post by SNIFFER_dog on 2011-09-17
Hi Ubuntu community,

I have been trying to get my remote to work with my MCE usb reciever under lirc.

Remote: Hauppauge PVR-350 [(A415 OH/S 1-4) found under battery cover (new batteries fitted)]
IR Receiver: MCE USB ID: 0609:031d SMK Manufacturing, Inc. eHome Infrared Receiver

(Remote is not the remote that came with the USB reciever)

LIRC: version 0.9.0 (I think)
Ubuntu: 11.04 Natty Narwhal (64 bit)

Symptoms: When running 'IRW' to check the input from the remote, nothing happens when I press any button on the remote.

I see there are many posts on LIRC in these forums. A lot have the similar symptoms as I do, where under program 'IRW' in the terminal, I see no results when the buttons are pressed on the remote, which has brand new batteries in it. I have to 'Ctrl C' to get out of 'IRW'

Here is a list of information from my system from what I have gleaned from other posts on what too look for.

cat /proc/bus/usb/devices

gives:```
cat: /proc/bus/usb/devices: No such file or directory
```I think it fails because I have a 64 Bit system? If this is located somewhere else could you let me know what terminal command will find it?

cat /proc/bus/input/devices

gives:```
I: Bus=0003 Vendor=0609 Product=031d Version=0000
N: Name="Media Center Ed. eHome Infrared Remote Transceiver (0609:031d)"
P: Phys=usb-0000:00:1d.0-2
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/rc/rc0/input7
U: Uniq=
H: Handlers=kbd event7 
B: PROP=0
B: EV=100013
B: KEY=fff 0 200108fc326 237605100000000 0 700158000 419200100001 9e968000000000 10000000
B: MSC=10
```lsusb

gives```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 045e:0745 Microsoft Corp. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0609:031d SMK Manufacturing, Inc. eHome Infrared Receiver
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 044e:300d Alps Electric Co., Ltd Bluetooth Controller (ALPS/UGPZ6)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05ca:1839 Ricoh Co., Ltd Visual Communication Camera VGP-VCC6 [R5U870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```dmesg | grep -i lirc

gives:```
[   13.417056] lirc_dev: IR Remote Control driver registered, major 61 
[   13.431912] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[   13.431916] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[   13.431966] usbcore: registered new interface driver lirc_mceusb
[   13.477687] ir_lirc_codec: Unknown symbol lirc_dev_fop_poll (err 0)
[   13.477985] ir_lirc_codec: Unknown symbol lirc_dev_fop_open (err 0)
[   13.478089] ir_lirc_codec: disagrees about version of symbol lirc_get_pdata
[   13.478092] ir_lirc_codec: Unknown symbol lirc_get_pdata (err -22)
[   13.478225] ir_lirc_codec: Unknown symbol lirc_dev_fop_close (err 0)
[   13.478327] ir_lirc_codec: Unknown symbol lirc_dev_fop_read (err 0)
[   13.478415] ir_lirc_codec: disagrees about version of symbol lirc_register_driver
[   13.478418] ir_lirc_codec: Unknown symbol lirc_register_driver (err -22)
[   13.478635] ir_lirc_codec: Unknown symbol lirc_dev_fop_ioctl (err 0)
[  212.060262] usbcore: deregistering interface driver lirc_mceusb
```There are lots of error messages here that I don't know how to fix or what it means?

dmesg | grep usb

gives:```
[    0.440101] usbcore: registered new interface driver usbfs
[    0.440120] usbcore: registered new interface driver hub
[    0.440171] usbcore: registered new device driver usb
[    1.660036] usb 1-3: new high speed USB device using ehci_hcd and address 3
[    2.110124] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    2.860077] usb 5-2: new full speed USB device using uhci_hcd and address 2
[    3.310042] usb 6-1: new full speed USB device using uhci_hcd and address 2
[   13.376250] usbcore: registered new interface driver btusb
[   13.411269] input: Media Center Ed. eHome Infrared Remote Transceiver (0609:031d) as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/rc/rc0/input7
[   13.411387] rc0: Media Center Ed. eHome Infrared Remote Transceiver (0609:031d) as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/rc/rc0
[   13.415625] mceusb 5-2:1.0: Registered SMK eHome Infrared Transceiver on usb5:2
[   13.415669] usbcore: registered new interface driver mceusb
[   13.431912] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[   13.431916] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[   13.431966] usbcore: registered new interface driver lirc_mceusb
[   13.564489] input: Microsoft Microsoft® Nano Transceiver v2.0 as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input8
[   13.570166] generic-usb 0003:045E:0745.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsoft Microsoft® Nano Transceiver v2.0] on usb-0000:00:1d.1-1/input0
[   13.594351] input: Microsoft Microsoft® Nano Transceiver v2.0 as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.1/input/input9
[   13.599536] generic-usb 0003:045E:0745.0002: input,hidraw1: USB HID v1.11 Mouse [Microsoft Microsoft® Nano Transceiver v2.0] on usb-0000:00:1d.1-1/input1
[   13.641481] input: Microsoft Microsoft® Nano Transceiver v2.0 as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.2/input/input10
[   13.641835] generic-usb 0003:045E:0745.0003: input,hiddev0,hidraw2: USB HID v1.11 Device [Microsoft Microsoft® Nano Transceiver v2.0] on usb-0000:00:1d.1-1/input2
[   13.641885] usbcore: registered new interface driver usbhid
[   13.641887] usbhid: USB HID core driver
[   13.803589] input: UVC Camera (05ca:1839) as /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.0/input/input11
[   13.803768] usbcore: registered new interface driver uvcvideo
[   13.900337] usbcore: deregistering interface driver uvcvideo
[   14.037560] input: UVC Camera (05ca:1839) as /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.0/input/input13
[   14.047885] usbcore: registered new interface driver uvcvideo
[   14.093636] usbcore: deregistering interface driver uvcvideo
[   14.180707] input: UVC Camera (05ca:1839) as /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.0/input/input14
[   14.181745] usbcore: registered new interface driver uvcvideo
[  212.060262] usbcore: deregistering interface driver lirc_mceusb

```Contents of hardware configuration file:```
Contents of File:

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge HVR-1300"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""
```That is all I can do with Linux as I'm pretty new to it but I am trying to learn.

Other posts talk about a lirc_mceusb2 module that under lirc 0.9.0 I don't seem to have and I can't find it on the Internet. This info came from posts dated around 2008 and I'm sure I have read that from the lirc.org website that lirc_mceusb is the updated version that has lirc_mceusb2 stuff included but I'm not fully sure. Either way it's not working on my system.

If there are any community members that might be able to help, I would be extremely grateful as I have no further avenues to explore.

P.s. this usb receiver and HVR-350 remote combination works under winLirc on my Windows 7 machine, so I am assuming the hardware works ok.


Kind regards

SNIFFY.

---

### Post by SNIFFER_dog on 2011-09-17
Bump

---

### Post by dowens81625 on 2011-09-17
Just guess but I assume hardware config should have 


# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge HVR-1300"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER="lirc_mceusb"
REMOTE_DEVICE="/dev/event7"  # or input7 cd dev and ls -l to check.
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

---

### Post by SNIFFER_dog on 2011-09-17
Thanks for the reply,

that generates an error message that it can't find that driver

---

### Post by SNIFFER_dog on 2011-09-18
Thanks too uniden9 from the following post: [http://ubuntuforums.org/showthread.php?t=1594799](http://ubuntuforums.org/showthread.php?t=1594799)

I have solved my issue. Turns out that the preloaded kernel module 'mceusb' was working alongside the 'lirc_mceusb' module which I think came from the lirc-modules-source package. With both modules loaded, neither will work so there is no output seen when running 'irw' in the terminal.

You can check if both are loaded by running the following in the terminal:```
lsmod | grep mceusb
```If that lists both 'mceusb' (Kernel module) and 'lirc_mceusb' (old module) then you may have the same problem I did, with having no response within 'irw'

You can try a quick check to see if your system works without making a permanent change by first, removing both modules, then adding back the 'lirc_mceusb' module, followed by restarting lirc. Quickly check only  the module 'lirc_mceusb' is loaded and then finally run 'irw' and check your remote button response.

The following will do this:
```
sudo modprobe -r mceusb
sudo modprobe -r lirc_mceusb

sudo modprobe lirc_mceusb
sudo /etc/init.d/lirc restart

lsmod | grep mceusb

```If you now only have the 'lirc_mceusb' module showing up, then in the terminal run
```
irw
```Now press some buttons on your remote to see if you get any responses. If nothing happens then exit 'irw' with Ctrl C

If nothing happens, then do make sure that your remote is configured with the correct keys, otherwise it still will not work.

Check out:
```
sudo gedit /etc/lirc/lircd.conf
```and paste in your remote config from the lirc website [http://lirc.sourceforge.net/remotes/](http://lirc.sourceforge.net/remotes/)

Try again to see it that works.


If it does and you want to make it a permanent change after reboot, then you have to blacklist the 'mceusb' module. Update the files for all your kernels, and reboot your machine.

Do this by the following:
```
sudo gedit /etc/modprobe.d/blacklist.conf
```Paste at the bottom of the file, the following:
```

# This blacklists the kernel source module and allows the use of the old dkms
# built module lirc_mceusb. You have to install lirc-modules-source from synaptic too
# If both the kernal module mceusb and the old module lirc_mceusb are loaded
# at the same time, then neither will work.
# lsmod | grep mceusb in terminal will list whats loaded
# The kernal module mceusb has to be blacklisted because it works this way
# on my system
blacklist mceusb

```Update the file to your kernel:```
sudo update-initramfs -u -k all
```Wait a few minutes for this to happen.

Once that is done make sure you have the 'lirc-modules-source' loaded in the Synaptic Package Manager. If not install them.

Now reboot your system and hopefully that is it.

I'm still new to this so I hope this works for you if not try version 1 listed in the post by uniden9 at the top of this reply.

Thanks again to uniden9 for helping me sort my problem out.

Kind regards,


SNIFFY.

---

