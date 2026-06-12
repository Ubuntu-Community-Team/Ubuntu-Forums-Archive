---
title: "Udev rule read, but not respected?"
date: 2012-09-14
forum: General Help
---

### Post by jensjk on 2012-09-14
I have two usb-webcams on them machine, but at bot they some switch /dev/video number. The solution to this problem seems to be new udev rule. I have added this rule in
/etc/udev/rules.d/jj-video.rules:

#Fix webcam 1
KERNEL=="video1", SUBSYSTEM=="video4linux", SUBSYSTEMS=="usb", ATTRS{idVendor}=="1d6b", ATTRS{idProduct}=="0001", SYMLINK+="webcam1"

#Fix webcam 2
KERNEL=="video2", SUBSYSTEM=="video4linux", ATTR{name}=="Logitech QuickCam Pro 3000", KERNELS=="0000:00:1d.0", SUBSYSTEMS=="pci", DRIVERS=="uhci_hcd", ATTRS{vendor}=="0x8086", ATTRS##{device}=="0x2658", SYMLINK+="webcam2"

but the symlinks are not created. I have tried many different combinations in this file. The present ones are just my lates attempts.

I found the parameters in:

jjk@eee-old:~$ udevadm info -a -p $(udevadm info -q path -p /class/video4linux/video1)  
Udevadm info starts with the device specified by the devpath and then walks up the chain of parent devices. It prints for every device found, all possible attributes in the udev rules key format. A rule to match, can be composed by the attributes of the device and the attributes from one single parent device.

 looking at device '/devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/video4linux/video1':
    KERNEL=="video1"
    SUBSYSTEM=="video4linux"
    DRIVER==""
    ATTR{name}=="Logitech QuickCam Pro 3000"
    ATTR{index}=="0"
    ATTR{button}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0':
    KERNELS=="2-2:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="Philips webcam"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bAlternateSetting}==" 9"
    ATTRS{bNumEndpoints}=="02"
    ATTRS{bInterfaceClass}=="0a"
    ATTRS{bInterfaceSubClass}=="ff"
    ATTRS{bInterfaceProtocol}=="00"
    ATTRS{supports_autosuspend}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb2/2-2':
    KERNELS=="2-2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 3"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="a0"
    ATTRS{bMaxPower}=="500mA"
    ATTRS{urbnum}=="371076"
    ATTRS{idVendor}=="046d"
    ATTRS{idProduct}=="08b0"
    ATTRS{bcdDevice}=="0002"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="8"
    ATTRS{speed}=="12"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="2"
    ATTRS{devpath}=="2"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{serial}=="01402100A5000000"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb2':
    KERNELS=="usb2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="34"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0001"
    ATTRS{bcdDevice}=="0302"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="12"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="1"
    ATTRS{devpath}=="0"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="2"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 3.2.0-29-generic uhci_hcd"
    ATTRS{product}=="UHCI Host Controller"
    ATTRS{serial}=="0000:00:1d.0"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0':
    KERNELS=="0000:00:1d.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="uhci_hcd"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x2658"
    ATTRS{subsystem_vendor}=="0x1043"
    ATTRS{subsystem_device}=="0x82d8"
    ATTRS{class}=="0x0c0300"
    ATTRS{irq}=="23"
    ATTRS{local_cpus}=="ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

jjk@eee-old:~$ 
And tested the setup:

sudo udevadm --debug test /sys/class/video4linux/video1

main: runtime dir '/run/udev'
run_command: calling: test
adm_test: version 175
This program is for debugging only, it does not run any program,
specified by a RUN key. It may show incorrect results, because
some values may be different, or not available at a simulation run.

parse_file: reading '/lib/udev/rules.d/40-crda.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-fuse.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-gnupg.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-hplip.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-ia64.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-inputattach.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-libgphoto2-2.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-libsane.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-ppc.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-usb_modeswitch.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-xserver-xorg-video-intel.rules' as rules file
parse_file: reading '/lib/udev/rules.d/42-qemu-usb.rules' as rules file
parse_file: reading '/lib/udev/rules.d/50-firmware.rules' as rules file
parse_file: reading '/lib/udev/rules.d/50-udev-default.rules' as rules file
parse_file: reading '/lib/udev/rules.d/55-dm.rules' as rules file
parse_file: reading '/lib/udev/rules.d/56-hpmud_support.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-cdrom_id.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-pcmcia.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-alsa.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-input.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-serial.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-storage-dm.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-storage-tape.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-storage.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-v4l.rules' as rules file
parse_file: reading '/lib/udev/rules.d/61-accelerometer.rules' as rules file


(and correspondingly for video2)

It looks to me like my rules are read, but not respected. What am I doing wrong?

---

### Post by steeldriver on 2012-09-14
I struggled with this recently - I *think* the answer is that you need to **trigger **the new rule - either by unplugging / replugging the device, or issuing an explicit 'udevadm trigger' command

[http://unix.stackexchange.com/questions/39370/how-to-reload-udev-rules-without-reboot](http://unix.stackexchange.com/questions/39370/how-to-reload-udev-rules-without-reboot)

Both methods seem to work for the USB fingerprint reader that I am playing with here, e.g. for that case

```
$ cat /etc/udev/rules.d/21-persistent-local.rules 
ATTR{idVendor}=="0483", ATTR{idProduct}=="2015", GROUP:="usb", MODE:="0660"
$
$ sudo udevadm trigger --attr-match=idVendor=0483 --attr-match=idProduct=2015
$
$ ls -l /dev/bus/usb/005/004
crw-rw---- 1 root usb 189, 515 Sep 14 10:55 /dev/bus/usb/005/004

```

---

### Post by jensjk on 2012-09-15
Thanks - problem solved :)

---

