---
title: "uvcvideo - inverted camera image"
date: 2011-07-31
forum: General Help
---

### Post by Kojot89 on 2011-07-31
I have noticed a problem with inverted camera image on the Asus k52je notebook with Ubuntu 11.04 x64.

When I try to run application like Skype it is not a problem, because I just need to preaload libv4l:
```
export LIBV4LCONTROL_FLAGS=3 && LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
```

Unfortunately this trick does not work for web browser. For example when I try to run google-chrome:
```
export LIBV4LCONTROL_FLAGS=3 && LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so google-chrome
```
flash plugin will still start with inverted camera image.

Is there any possibility to preload parameters globally, so that the flash plugin also used them?

I was also thinking about giving a parameter to uvcvideo kernel module.
```
udevadm info -q all --name=/dev/video0 --attribute-walk
```

```

  looking at device '/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/video4linux/video0':
    KERNEL=="video0"
    SUBSYSTEM=="video4linux"
    DRIVER==""
    ATTR{name}=="USB 2.0 Camera"
    ATTR{index}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0':
    KERNELS=="1-1.2:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="uvcvideo"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="01"
    ATTRS{bInterfaceClass}=="0e"
    ATTRS{bInterfaceSubClass}=="01"
    ATTRS{bInterfaceProtocol}=="00"
    ATTRS{supports_autosuspend}=="1"
    ATTRS{iad_bFirstInterface}=="00"
    ATTRS{iad_bInterfaceCount}=="02"
    ATTRS{iad_bFunctionClass}=="0e"
    ATTRS{iad_bFunctionSubClass}=="03"
    ATTRS{iad_bFunctionProtocol}=="00"
    ATTRS{interface}=="USB Camera"

  looking at parent device '/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2':
    KERNELS=="1-1.2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 2"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{bMaxPower}=="500mA"
    ATTRS{urbnum}=="2627"
    ATTRS{idVendor}=="13d3"
    ATTRS{idProduct}=="5130"
    ATTRS{bcdDevice}=="1211"
    ATTRS{bDeviceClass}=="ef"
    ATTRS{bDeviceSubClass}=="02"
    ATTRS{bDeviceProtocol}=="01"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="1"
    ATTRS{devnum}=="3"
    ATTRS{devpath}=="1.2"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Sonix Technology Co., Ltd."
    ATTRS{product}=="USB 2.0 Camera"

  looking at parent device '/devices/pci0000:00/0000:00:1a.0/usb1/1-1':
    KERNELS=="1-1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="182"
    ATTRS{idVendor}=="8087"
    ATTRS{idProduct}=="0020"
    ATTRS{bcdDevice}=="0000"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="01"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="1"
    ATTRS{devnum}=="2"
    ATTRS{devpath}=="1"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="6"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1a.0/usb1':
    KERNELS=="usb1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="92"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0002"
    ATTRS{bcdDevice}=="0206"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="1"
    ATTRS{devnum}=="1"
    ATTRS{devpath}=="0"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="2"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 2.6.38-10-generic ehci_hcd"
    ATTRS{product}=="EHCI Host Controller"
    ATTRS{serial}=="0000:00:1a.0"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1a.0':
    KERNELS=="0000:00:1a.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci_hcd"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x3b3c"
    ATTRS{subsystem_vendor}=="0x1043"
    ATTRS{subsystem_device}=="0x1c77"
    ATTRS{class}=="0x0c0320"
    ATTRS{irq}=="16"
    ATTRS{local_cpus}=="00000000,00000000,00000000,00000000,00000000,00000000,00000000,0000000f"
    ATTRS{local_cpulist}=="0-3"
    ATTRS{numa_node}=="-1"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""
    ATTRS{companion}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

```

Unfortunately uvcvideo does not accept flip parameters:
```
sudo modprobe -r uvcvideo
sudo modprobe -v uvcvideo vflip=0
```

```
insmod /lib/modules/2.6.38-10-generic/kernel/drivers/media/video/v4l2-compat-ioctl32.ko 
insmod /lib/modules/2.6.38-10-generic/kernel/drivers/media/video/videodev.ko 
insmod /lib/modules/2.6.38-10-generic/kernel/drivers/media/video/uvc/uvcvideo.ko vflip=0
FATAL: Error inserting uvcvideo (/lib/modules/2.6.38-10-generic/kernel/drivers/media/video/uvc/uvcvideo.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

---

### Post by coldraven on 2011-07-31
Try running guvcview (from the Software Centre) then select "invert" and quit. 
I know this works for brightness issues but you will just have to try it for your problem.

---

### Post by Kojot89 on 2011-07-31
> **coldraven said:**
> Try running guvcview (from the Software Centre) then select "invert" and quit. 
I know this works for brightness issues but you will just have to try it for your problem.

Unfortunately it does not invert camera image in the web browser.

I have noticed that this trick inverts skype image only if I run skype this way:
```
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
```

---

### Post by coldraven on 2011-08-02
Sorry, my knowledge base has been depleted :)

---

